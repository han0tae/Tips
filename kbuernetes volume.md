ephemeral
persistent 

.spec.volumes에서 파드에 제공할 볼륨을 지정
.spec.container[*].volumeMounts 볼륨 마운트 위치를 선언
퍼시스턴트볼륨 (PV)은 관리자가 프로비저닝하거나 스토리지 클래스를 사용하여 동적으로 프로비저닝한 클러스터의 스토리지
퍼시스턴트볼륨클레임 (PVC)은 사용자의 스토리지에 대한 요청으로 ReadWriteOnce, ReadOnlyMany 또는 ReadWriteMany로 마운트 할 수 있음
