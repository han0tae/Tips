<pre>
<code>
type DnsOpsSpec struct {
	PowerDNSConfig 		string 	'json:"powerdnsConfig"'
	RecursorConfig 		string 	'json:"recursorConfig"'
	PowerDNSIP			string 	'json:"powerdnsIP"'
	RecursorIP			string 	'json:"recursorIP"'
	MariaDBHost			string 	'json:"mariaDBHost"'
	MariaDBPort			int 	'json:"mariaDBPort"'
	MariaDBUser			string 	'json:"mariaDBUser"'
	MariaDBPassword		string 	'json:"mariaDBPassword"'
}

type DnsOpsStatus struct {
	Ready bool 'json:"ready"'
}

import (
	"context"
	"database/sql"
	"fmt"
	corev1 "k8s.io/api/core/v1"
	metav1 "k8s.io/apimachinery/pkg/apis/meta/v1"
	ctrl "sigs.k8s.io/controller-runtime"
	_ "github.com/go-sql-driver/mysql"
)


func (r *DnsOpsReconciler) Reconcile(stx context.Context, req ctrl.Request) (ctrl.Result, log := r.Log.WithValues("dnsops", req.NamespaceName){
	
	var dnsOps dnsv1.DnsOpsReconciler
	
	dbHost := dnsOps.Spec.Mariadb.Host
	dbPort := dnsOps.Spec.Mariadb.Port
	dbUser := dnsOps.Spec.Mariadb.Password
	dbName := dnsOps.Spec.Mariadb.Database
	sqlScriptPath := "/etc/powerdns/schema.sql"
	
	log.Info("Initializing MariaDB database and tables")
	if err := initializeDatabase(ctx, dbHost, dbPort, dbUser, dbPassword, dbName, sqlScriptPath); err != nil {
		log.Error(err, "Failed to initialize MariaDB")
		return ctrl.Result{}, err
	}
	
	if err := r.Get(ctx, req.NamespacedName, &dnsOps); err != nil {
		if errors.IsNotFound(err){
			log.info("DnsOps resource not found. Ignoring since object must be deleted.")
			
			if err := r.cleanupResources(ctx, req.Namespace, req,Name); err != nil {
				log.Error(err, "Failed to clean up resource")
				return ctrl.Result{}, err
			}
			return ctrl.Result{}, nil
		}
		log.error(err, "Failed to get DnsOps")
		return ctrl.Result{}. err
	}
	
	configMap := &corev1.ConfigMap{
		ObjectMeta: metav1. ObjectMeta{
			Name: fmt.Sprintf("dnsops-config-%d", dnsOps.Spec.InstancceNumber), Namespace: req.Namespace, }.
			Data: map[string]string{
				"powerdns.conf": dnsOps.Spec.PowerDNSConfig,
				"recursor.conf": dnsOps.Spec.RecursorConfig,
			},
	}
	
	if err := ctrl.SetControllerReference(&dnsOps, configMap, r.Scheme); err != nil {
		return ctrl.Result{}, err
	}
	
	if err := r.CreateOrUpdate(ctr, configMap); err != nil {
		return ctrl.Result{}, err
	}
	rollback := func(){
		_ = r.rollbackDeployment(ctx, dnsOps.Namespace, fmt.Sprint("powerdns-%d-", dnsOps.Spec.InstanceNumber))
		_ = r.rollbackDeployment(ctx, dnsOps.Namespace, fmt.Sprint("recursor-%d-", dnsOps.Spec.InstanceNumber))
		_ = r.rollbackService(ctx, dnsOps.Namespace, fmt.Sprint("powerdns-%d-", dnsOps.Spec.InstanceNumber))
		_ = r.rollbackService(ctx, dnsOps.Namespace, fmt.Sprint("recursor-%d-", dnsOps.Spec.InstanceNumber))		
	}
	if err := r.createPowerDNSDeployment(ctx, &dnsOps); err != nil {
		log.Error(err, "Failed to deployment PowerDNS, rolling back")
		rollback()
		return ctrl.Result{}, err
	}
	if err := r.createRecursorDeployment(ctx, &dnsOps); err != nil {
		log.Error(err, "Failed to deployment PowerDNS, rolling back")
		rollback()
		return ctrl.Result{}, err
	}
	if err := r.createPowerDNSService(ctx, &dnsOps); err != nil {
		log.Error(err, "Failed to deployment PowerDNS, rolling back")
		rollback()
		return ctrl.Result{}, err
	}
	if err := r.createRecursorService(ctx, &dnsOps); err != nil {
		log.Error(err, "Failed to deployment PowerDNS, rolling back")
		rollback()
		return ctrl.Result{}, err
	}
	log.Info("Reconciled DnsOps Successfully")
	return ctrl.Result{}, nil
}
	
	
func (r *DnsOpsReconciler) createPowerDNSDeployment(ctx context.Context, *dnsv1.DnsOps) error{
	for i := 0; i < dnsOps.Spec.PowerDNSReplica; i++ {
		deployment := &appsv1.Deployment{
			ObjectMeta: metav1.ObjectMeta{
				Name: fmt.Sprintf("powerdns-%d-%d", dnsOps.Spec.InstanceNumber, i),
				Namespace: dnsOps.Namespace,.
			},
			Spec: appsv1.DeploumentSpec{
				Replicas: pointer.Int32(1),
				Selector: &metav1.LabelSelector{
					MatchLabels: map[string]string{"app":"powerdns","instance":fmt.Sprintf("%d", dnsOps.Spec.InstanceNumber)};
					},
				Spec: corev1.PodSpec{
					Containers: []corev1.Container{
						{
							Name: "powerdns",
							Image: "powerdns/pdns:latest",
							VolumeMounts: []corev1.VolumeMount{
							{
								Name: "config"
								MountPath: "/etc/powerdns",
							},
						},
						Env: []corev1.EnvVar{
							{Name: "MARIADB_HOST", Value: dnsOps.Spec.MariaDBHost},
							{Name: "MARIADB_PORT", Value: dnsOps.Spec.MariaDBPort},
							{Name: "MARIADB_USER", Value: dnsOps.Spec.MariaDBUser},
							{Name: "MARIADB_PASSWPRD", Value: dnsOps.Spec.MariaDBPassword},
						},
					},
				},
				Volumes: []corev1.Volume{
				{
					Name: "config",
					VolumeSource: corev1.VolumeSource{
						ConfigMap: &corev1.ConfigMapVolumeSource{
							LocalObjectReference: corev1.LocalObjectReference{
								Name: fmt.Sprintf("dnsops-config-%d", dnsOps.Spec.InstanceNumber),
									},
								},
							},
						},
					},
				},
			},
		},
	}
	if err := r.CreateOrUpdate(ctx, deployment); err != nil {
            return err
        }
    }
    return nil
}

func (r *DnsOpsReconciler) createRecursorDeployment(ctx context.Context, dnsOps *dnsv1.DnsOps) error {
    for i := 0; i < dnsOps.Spec.RecursorReplica; i++ {
        deployment := &appsv1.Deployment{
            ObjectMeta: metav1.ObjectMeta{
                Name:      fmt.Sprintf("recursor-%d-%d", dnsOps.Spec.InstanceNumber, i),
                Namespace: dnsOps.Namespace,
            },
            Spec: appsv1.DeploymentSpec{
                Replicas: pointer.Int32(1),
                Selector: &metav1.LabelSelector{
                    MatchLabels: map[string]string{"app": "recursor", "instance": fmt.Sprintf("%d", dnsOps.Spec.InstanceNumber)},
                },
                Template: corev1.PodTemplateSpec{
                    ObjectMeta: metav1.ObjectMeta{
                        Labels: map[string]string{"app": "recursor", "instance": fmt.Sprintf("%d", dnsOps.Spec.InstanceNumber)},
                    },
                    Spec: corev1.PodSpec{
                        Containers: []corev1.Container{
                            {
                                Name:  "recursor",
                                Image: "powerdns/recursor:latest",
                                VolumeMounts: []corev1.VolumeMount{
                                    {
                                        Name:      "config",
                                        MountPath: "/etc/powerdns",
                                    },
                                },
                            },
                        },
                        Volumes: []corev1.Volume{
                            {
                                Name: "config",
                                VolumeSource: corev1.VolumeSource{
                                    ConfigMap: &corev1.ConfigMapVolumeSource{
                                        LocalObjectReference: corev1.LocalObjectReference{
                                            Name: fmt.Sprintf("dnsops-config-%d", dnsOps.Spec.InstanceNumber),
                                        },
                                    },
                                },
                            },
                        },
                    },
                },
            },
        }

        if err := r.CreateOrUpdate(ctx, deployment); err != nil {
            return err
        }
    }
    return nil
}

func (r *DnsOpsReconciler) createPowerDNSService(ctx context.Context, dnsOps *dnsv1.DnsOps)error {
	service := &corev1.Service{
		ObjectMeta: metav1.ObjectMeta{
			Name: fmt.Sprintf("powerdns-%d", dnsOps.Spec.InstanceNumber),
			Namespace: dnsOps.Namespace,
	},
	spec: corev1.ServiceSpec{
		Selector: map[string]string{
			"app": "powerdns",
			"instance": fmt.Sprintf("%d", dnsOps,Spec.InstanceNumber),
		},
		ports: []corev1.ServicePort{
			{
				Name: "dns",
				Port: 53,
				Protocol: corev1.ProtocolUDP,
				TargetPort: instr.FromInt(53),
			},
			{
				Name: "dns",
				Port: 53,
				Protocol: corev1.ProtocolUDP,
				TargetPort: instr.FromInt(53),
			},
			{
				Name: "api",
				Port: 8081,
				Protocol: corev1.ProtocolTCP,
				TargetPort: instr.FromInt(8081),
			},
		},
		Type: corev1.ServicewTypeClusterIP,
		ExternalIPOs: []string{
			dnsOps.Spec.RecursorExternalIP,
			},
		},
	}
	if err := ctrl.SetControllerReference(dnsOps, service, r.Scheme); err != nil {
		return err
	}
	if err := r.CreateOrUpdate(ctx, service); err != nil {
		return err
	}
	return nil
}

	
func (r *DnsOpsReconciler) createRecursorService(ctx context.Context, dnsOps *dnsv1.DnsOps)error {
	service := &corev1.Service{
		ObjectMeta: metav1.ObjectMeta{
			Name: fmt.Sprintf("recursor-%d", dnsOps.Spec.InstanceNumber),
			Namespace: dnsOps.Namespace,
	},
	spec: corev1.ServiceSpec{
		Selector: map[string]string{
			"app": "recursor",
			"instance": fmt.Sprintf("%d", dnsOps,Spec.InstanceNumber),
		},
		ports: []corev1.ServicePort{
			{
				Name: "dns",
				Port: 53,
				Protocol: corev1.ProtocolUDP,
				TargetPort: instr.FromInt(53),
			},
			{
				Name: "dns",
				Port: 53,
				Protocol: corev1.ProtocolUDP,
				TargetPort: instr.FromInt(53),
			},
		},
		Type: corev1.ServicewTypeLoadBalancer,
		ExternalIPOs: []string{
			dnsOps.Spec.RecursorExternalIP,
			},
		},
	}
	if err := ctrl.SetControllerReference(dnsOps, service, r.Scheme); err != nil {
		return err
	}
	if err := r.CreateOrUpdate(ctx, service); err != nil {
		return err
	}
	return nil
}

func (r *DnsOpsReconciler) rollbackDeplyoment(ctx context.Context, namespace, prefix string) error {
	log := r.Log.WithValues("rollback", prefix)
	deploymentList := &corev1.DeploymentList{}
	err := r.List(ctx, cdeploymentList, client.InNamespace(namespace)); err != nil {
		log.Info("Service not found, no need to rollback")
		return err
	}
	
	for _, deployment := range deploymentList.Items { 
		if strings.HasPrefix(deployment.Name, prefix) {
			log.Info("Deleting deployment", "name", deployment.Name)
			if err := r.Delete(ctx, &deployment); err != nil {
				log.Error(err, "Failed to delete deployment during rollback")
			}
		}
	}
	return nil
}

func (r *DnsOpsReconciler) rollbackService(ctx context.Context, namespace, serviceName string) error {
	log := r.Log.WithValues("rollback", serivceNmae)
	service := &corev1.Service{}
	err := r.Get(ctx, client.ObjectKey{Namespace: namespcae, Name: serviceName}, service)
	if err != nil {
		if errors.IsNotFound(err) {
			log.Info("Service not found, no need to rollback")
			return nil
		}
		log.Error(err, "Failed to get service for rollback")
		return err
	}
	
	log.Info("Deleting service", "name", serviceName)
	if err := r.Delete(ctx, service); err != nil {
		log.Error(err, "Failed to delete service during rollback")
	}
	return nil
}

func initializeDatabase(ctx context.Context, dbhost, dbport, dbUser, dbPassword, dbName, sqlScriptPath string) error {
	dsn := fmt.Sprintf("%a:%a@tcp(%s:%s)/", dbUser, dbPassword, dbHost, dbPort)
	db, err := sql.Open("mysql", dsn)
	if err != nil {
		return fmt.Errorf("failed to connect to MariaDB: %w", err)
	}
	defer db.Close()
	
	createDBQuery := fmt.Sprintf("CREATE DATABASE IF NOT EXISTS %s;", dbName)
	if _, err := db.ExceContext(ctx, createDBQuery); err != nil {
		return fmt.Errorf("failed to create database: %w", err)
	}
	useDBQuery := fmt.Sprintf("ISE %s;", dbName)
	
	if _, err := db.ExecContext(ctx, useDBQuery); err != nil {
		return fmt.Errorf("failed to use database: %w", err)
	}
	
	sqlScript, err := os.ReadFile(sqlScriptPath)
	
	if err != nil {
		return fmt.Errorf("failed to read SQL script: %w", err)
	}
	
	if _, err := db.ExecContext(ctx, string(sqlScript)); err != nil {
		return fmt.Errorf("failed to execute SQL script: %w", err)
	}
	return nil
}
</code>
</pre>
