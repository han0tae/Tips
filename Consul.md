# 설치
<pre>
<code>
helm install -f /tmp/consul.yaml consul hashicorp/consul --set global.name=consul --create-namespace --namespace consul --debug
NAME: consul
LAST DEPLOYED: Thu Oct 26 00:41:55 2023
NAMESPACE: consul
STATUS: deployed
REVISION: 1
NOTES:
Thank you for installing HashiCorp Consul!

Your release is named consul.

To learn more about the release, run:

  $ helm status consul --namespace consul
  $ helm get all consul --namespace consul

Consul on Kubernetes Documentation:
https://www.consul.io/docs/platform/k8s

Consul on Kubernetes CLI Reference:
https://www.consul.io/docs/k8s/k8s-cli
</code>
</pre>
/tmp/consul.yaml
<pre>
<code>
  connectInject:
  enabled: true
  default: true
  namespaceSelector: |
    matchLabels:
      connect-inject: enabled
  cni:
    enabled: true
    logLevel: info
    cniBinDir: "/opt/cni/bin"
    cniNetDir: "/etc/cni/net.d"
</code>
</pre>
