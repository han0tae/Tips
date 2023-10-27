
NO.1 회사가 AWS에 비즈니스 크리티컬 애플리케이션을 배포했습니다. Good 애플리케이션이 us-east-1 리전에서 실행되는 Amazon EC2 인스턴스를 사용합니다. 애플리케이션이 모든 중요 데이터를 저장하는 데 Amazon S3를 사용합니다. 규정 준수 요구 사항을 충족하려면 회사가 반드시 수행해야 하는 다른 AWS 리전에 대한 전체 장애 조치 기능을 제공하는 재해 복구(DR) 계획 생성 이 DR 계획에 대해 솔루션 설계자는 무엇을 권장해야 합니까?
 A. us-east-1의 여러 가용 영역에 애플리케이션 배포 AWS 리소스 그룹에서 리소스 그룹 생성 애플리케이션이 사전 정의된 복구 리전을 사용하도록 자동 장애 조치를 켭니다.
 B. 기존 EC2 인스턴스에서 AWS Import/Export를 사용하여 가상 머신(VM) 내보내기 수행 재해 발생 시 내보낸 인스턴스를 대상 리전으로 복사 내보낸 EC2 인스턴스에서 새 EC2 인스턴스 프로비저닝
 C. us-east-t의 EC2 인스턴스에 연결된 모든 Amazon Elastic Block Store(Amazon EBS) 볼륨의 스냅샷 생성 대상 리전에 스냅샷 복사 재해 발생 시 EBS 스냅샷에서 새 EC2 인스턴스 프로비저닝
 D. Amazon S3에 저장된 데이터에 대해 S3 교차 리전 복제 사용 S3 버킷 파라미터가 있는 애플리케이션용 AWS CloudFormation 템플릿 생성 재해 발생 시 템플릿을 대상 리전에 배포하고 로컬 S3 버킷을 다음과 같이 지정합니다. 매개변수
 답: D

NO.2 애플리케이션은 프라이빗 서브넷의 Amazon EC2 인스턴스에서 실행됩니다. 애플리케이션은 Amazon DynamoDB 테이블에 액세스해야 합니다. 트래픽이 AWS 네트워크를 벗어나지 않도록 하면서 테이블에 액세스하는 가장 안전한 방법은 무엇입니까?
 A. DynamoDB용 VPC 엔드포인트 사용
 B. 퍼블릭 서브넷에서 NAT 게이트웨이 사용
 C. 프라이빗 서브넷에서 NAT 인스턴스 사용
 D. VPC에 연결된 인터넷 게이트웨이 사용
 답: A

NO.3 회사에서 PostgreSQL 데이터베이스를 사용하는 내부 응용 프로그램을 개발하고 있습니다. 회사는 Amazon Aurora에서 데이터베이스를 호스팅하기로 결정했습니다. 애플리케이션이 고가용성일 필요는 없지만 데이터는 내구성을 극대화하기 위해 여러 가용 영역에 저장되어야 합니다. 어떤 데이터베이스 구성이 이러한 요구 사항을 가장 비용 효율적으로 충족합니까?
 A. 단일 D8 인스턴스가 있는 Aurora PostgreSQL DB 클러스터
 B. 기본 DB 인스턴스와 읽기 전용 복제본이 있는 Aurora PostgreSQL DB 클러스터
 C. 다중 AZ 배포가 활성화된 Aurora PostgreSQL DB 클러스터
 D. Aurora PostgreSQL 글로벌 데이터베이스 클러스터
 답: B

NO.4 솔루션 설계자는 Windows IIS(인터넷 정보 서비스) 웹 애플리케이션을 AWS로 마이그레이션해야 합니다. 애플리케이션은 현재 사용자의 온프레미스 NAS(Network Attached Storage)에서 호스팅되는 파일 공유에 의존합니다. 솔루션 설계자는 MS 마이그레이션을 제안했습니다. 스토리지 솔루션에 연결된 여러 가용 영역의 Amazon EC2 인스턴스에 웹 서버를 연결하고 인스턴스에 연결된 Elastic Load Balancer 구성
 A. 파일 공유를 Amazon RDS로 마이그레이션
 B. 파일 공유를 AWS Storage Gateway로 마이그레이션
 C. 파일 공유를 Windows 파일 서버용 Amazon FSx로 마이그레이션
 D. 파일 공유를 Amazon Elastic File System(Amazon EFS)으로 마이그레이션
 답: C

NO.5 애플리케이션 개발자는 비즈니스 보고 사용자가 애플리케이션을 지원하는 Amazon RDS 인스턴스에 대해 대규모 프로덕션 보고서를 실행할 때 프로덕션 애플리케이션이 매우 느리다는 것을 알아차렸습니다. 보고 쿼리가 실행되는 동안 RDS 인스턴스에 대한 CPU 및 메모리 사용률 지표는 60%를 초과하지 않습니다. 실행 중인 비즈니스 보고 사용자는 애플리케이션의 성능에 영향을 주지 않고 보고서를 생성할 수 있어야 합니다. 어떤 조치가 이를 달성할 것입니까?
 A. RDS 인스턴스 크기 늘리기
 B. 읽기 전용 복제본 생성 및 애플리케이션 연결
 C. RDS 인스턴스에서 여러 가용 영역 활성화
 D. 읽기 전용 복제본 생성 및 비즈니스 보고서 연결
 답: D

NO.6 회사에 2개의 가용 영역에 걸쳐 Amazon EC2 인스턴스에서 실행되는 웹 사이트가 있습니다. 회사는 특정 휴일에 트래픽이 급증할 것으로 예상하고 일관된 사용자 경험을 제공하기를 원합니다. 솔루션 설계자는 이 요구 사항을 어떻게 충족할 수 있습니까?
 A. 단계적 스케일링 사용
 B. 간단한 스케일링 사용
 C. 수명 주기 후크 사용
 D. 예약된 확장 사용
 답: D

NO.7 회사는 온프레미스에서 다중 계층 웹 애플리케이션을 실행하고 있습니다. 웹 애플리케이션은 컨테이너화되고 사용자 기록이 포함된 PostgreSQL 데이터베이스에 연결된 여러 Linux 호스트에서 실행됩니다. 인프라 및 용량 계획을 유지 관리하는 운영 오버헤드가 회사의 성장을 제한하고 있습니다. 솔루션 설계자는 애플리케이션의 인프라를 개선해야 합니다. 솔루션 설계자는 이를 달성하기 위해 어떤 조합의 조치를 취해야 합니까? (2개를 선택하십시오.)
 A. PostgreSQL 데이터베이스를 Amazon Aurora로 마이그레이션
 B. Amazon EC2 인스턴스에서 호스팅할 웹 애플리케이션을 마이그레이션합니다.
 C. 웹 애플리케이션 콘텐츠에 대한 Amazon CloudFront 배포를 설정합니다.
 D. 웹 애플리케이션과 PostgreSQL 데이터베이스 간에 Amazon ElastiCache를 설정합니다.
 E. Amazon Elastic Container Service(Amazon ECS)를 사용하여 AWS Fargate에서 호스팅할 웹 애플리케이션을 마이그레이션합니다.
 답: C,D

NO.8 한 회사가 새로운 온라인 게임 애플리케이션을 개발하고 있습니다. 애플리케이션은 여러 AWS 리전의 Amazon EC2 인스턴스에서 실행되며 전 세계적으로 많은 사용자가 분산됩니다. 솔루션 설계자는 사용자의 네트워크 지연 시간을 최적화하도록 애플리케이션을 설계해야 합니다. 솔루션 설계자는 이러한 요구 사항을 충족하기 위해 어떤 조치를 취해야 합니까? (2개를 선택하십시오.)
 A. AWS Global Accelerator 구성 EC2 집합이 호스팅되는 각 리전에서 리전 엔드포인트 그룹 생성
 B. Amazon CloudFront를 사용하여 콘텐츠 전송 네트워크(CDN) 생성 정적 및 동적 콘텐츠에 대한 캐싱 활성화 및 높은 만료 기간 지정
 C. AWS Client VPN을 애플리케이션에 통합합니다. 사용자에게 애플리케이션을 시작한 후 가장 가까운 리전을 선택하도록 지시합니다. 해당 지역에 대한 VPN 연결 설정
 D. Amazon Route 53 가중치 기반 라우팅 정책 생성 리전에서 사용자 수가 가장 많은 EC2 인스턴스에 가장 높은 가중치를 부여하도록 라우팅 정책을 구성합니다.
 E. EC2 집합이 호스팅되는 각 리전에서 Amazon API Gateway 엔드포인트 구성 애플리케이션을 시작한 후 사용자에게 가장 가까운 리전을 선택하도록 지시합니다. 가장 가까운 API Gateway 엔드포인트를 사용하십시오.
 답변: A, B

NO.9 한 회사가 주문 관리 애플리케이션을 자동화하고 있습니다. 회사의 개발 팀은 SFTP를 사용하여 업무상 중요한 정보 파일을 전송하고 저장하기로 결정했습니다. 파일은 암호화되어야 하고 가용성이 높아야 합니다. 또한 파일은 생성된 후 한 달 후에 자동으로 삭제되어야 합니다. 최소한의 운영 오버헤드로 이러한 요구 사항을 충족하는 솔루션은 무엇입니까?
 A. 암호화가 활성화된 Amazon S3 버킷을 구성합니다. SFTP용 AWS 전송을 사용하여 파일을 S3 버킷으로 안전하게 전송 SFTP용 AWS 전송 파일 보존 정책을 적용하여 한 달 후 파일 삭제
 B. Amazon EC2 인스턴스에 SFTP 서비스 설치 EC2 인스턴스에 Amazon Elastic File System(Amazon EFS) 파일 공유를 탑재합니다. cron이 한 달 후에 파일을 삭제하도록 활성화
 C. 암호화가 활성화된 Amazon Elastic File System(Amazon EFS) 파일 시스템을 구성합니다. AWS Transfer for SFTP를 사용하여 파일을 EFS 파일 시스템으로 안전하게 전송하십시오. EFS 수명 주기 정책을 적용하여 한 달 후에 파일을 자동으로 삭제합니다.
 D. 암호화가 활성화된 Amazon S3 버킷을 구성합니다. AWS Transfer for SFTP를 사용하여 파일을 S3 버킷으로 안전하게 전송하십시오. S3 수명 주기 규칙을 적용하여 한 달 후에 파일을 자동으로 삭제합니다.
 답: D

NO.10 회사는 소프트웨어 애플리케이션을 위한 불변의 인프라를 구축하기를 원합니다 회사는 트래픽을 보내기 전에 소프트웨어 애플리케이션을 테스트하기를 원합니다 회사는 애플리케이션 버그의 영향을 제한하는 효율적인 솔루션을 찾고 있습니다 솔루션 설계자가 권장해야 하는 단계 조합 ? {2개 선택)
 A. AWS Cloud Formation을 사용하여 프로덕션 인프라를 업데이트하고 업데이트가 실패할 경우 스택을 롤백합니다.
 B. Amazon Route 53 가중 라우팅을 적용하여 스테이징 환경을 테스트하고 테스트 통과에 따라 트래픽을 점진적으로 늘립니다.
 C. Amazon Route 53 장애 조치 라우팅을 적용하여 스테이징 환경을 테스트하고 테스트를 통과하면 프로덕션 환경으로 장애 조치합니다.
 D. 프로덕션 환경이 아닌 별도의 환경에서 스테이징 값으로 설정된 파라미터와 함께 AWS Cloud Formation 사용
 E. AWS Cloud Formation을 사용하여 스냅샷 삭제 정책이 있는 스테이징 환경을 배포하고 테스트를 통과하면 프로덕션 환경에서 리소스를 재사용합니다.
 답변: A, B

NO.11 회사의 애플리케이션이 Elastic Load Balancer 뒤의 Auto Scaling 그룹 내의 Amazon EC2 인스턴스에서 실행되고 있습니다. 애플리케이션의 이력을 기반으로 회사는 매년 휴일 동안 트래픽이 급증할 것으로 예상합니다. 솔루션 설계자는 다음을 보장하는 전략을 설계해야 합니다. Auto Scaling 그룹은 사전에 용량을 늘려 애플리케이션 사용자에 대한 성능 영향을 최소화합니다. 어떤 솔루션이 이러한 요구 사항을 충족합니까?'
 A. CPU 사용률이 90%를 초과할 때 EC2 인스턴스를 확장하는 Amazon CloudWatch 경보 생성
 B. 예상되는 피크 수요 기간 전에 Auto Scaling 그룹을 확장하기 위해 반복되는 예약된 작업을 생성합니다.
 C. 피크 수요 기간 동안 Auto Scaling 그룹의 최소 및 최대 EC2 인스턴스 수를 늘립니다.
 D. Autoscaling EC2_INSTANCE_LAUNCH 이벤트가 있을 때 알림을 보내도록 Amazon Simple Notification Service(Amazon SNS) 알림을 구성합니다.
 답: B

NO.12 Amazon EC2 Linux 인스턴스에서 웹사이트를 운영하는 회사가 있습니다. 인스턴스 중 일부가 실패하고 있습니다. 문제 해결은 실패한 인스턴스의 스왑 공간이 충분하지 않음을 나타냅니다. 운영 팀장은 이를 모니터링할 솔루션이 필요합니다. 솔루션 설계자는 무엇을 권장해야 합니까?
 A. Amazon CloudWatch SwapUsage 지표 차원 구성 CloudWatch의 EC2 지표에서 SwapUsage 차원을 모니터링합니다.
 B. EC2 메타데이터를 사용하여 정보를 수집한 다음 Amazon CloudWatch 사용자 지정 지표에 게시 CloudWatch에서 SwapUsage 지표 모니터링
 C. 인스턴스에 Amazon CloudWatch 에이전트를 설치합니다. 정해진 일정에 따라 적절한 스크립트를 실행합니다. CloudWatch에서 SwapUtilization 지표 모니터링
 D. EC2 콘솔에서 세부 모니터링 활성화 Amazon CloudWatch SwapUtilization 사용자 지정 지표 생성 CloudWatch에서 SwapUtilization 지표 모니터링
 답: A

NO.13 한 회사에 다양한 부서에 대해 여러 AWS 계정이 있습니다. 부서 중 하나가 다른 모든 부서와 Amazon S3 버킷을 공유하려고 합니다. 가장 적은 노력이 필요한 솔루션은 무엇입니까?
 A. 버킷에 대해 교차 계정 S3 복제 활성화
 B. 버킷에 대한 사전 서명된 URL을 생성하고 다른 부서와 공유
 C. 다른 부서에 대한 교차 계정 액세스를 허용하도록 S3 버킷 정책 설정
 D. 부서별 1AM 사용자 생성 및 읽기 전용 1AM 정책 구성
 답: C

NO.14 회사에서 AWS를 사용하여 보험 견적을 처리할 웹 애플리케이션을 설계하고 있습니다. 사용자가 애플리케이션에서 견적을 요청합니다. 견적은 견적 유형별로 구분되어야 하고, 24시간 이내에 응답해야 하며, 길을 잃지 않아야 합니다. 솔루션은 최대화해야 합니다. 운영 효율성을 높이고 유지 관리를 최소화해야 합니다. 어떤 솔루션이 이러한 요구 사항을 충족합니까?
 A. 견적 유형을 기반으로 여러 Amazon Kinesis 데이터 스트림 생성 적절한 데이터 스트림으로 메시지를 전송하도록 웹 애플리케이션 구성 Kinesis 클라이언트 라이브러리(KCL)를 사용하여 자체 데이터 스트림의 메시지를 풀링하도록 애플리케이션 서버의 각 백엔드 그룹 구성
 B. 각 견적 유형에 대해 AWS Lambda 함수 및 Amazon Simple Notification Service(Amazon SNS) 주제 생성 관련 SNS 주제에 Lambda 함수 구독 적절한 SNS 주제에 요청을 게시하도록 애플리케이션 구성
 C. 단일 Amazon Simple Notification Service(Amazon SNS) 주제 생성 Amazon Simple Queue Service(Amazon SQS) 대기열을 SNS 주제에 구독 견적 유형에 따라 적절한 SQS 대기열에 메시지를 게시하도록 SNS 메시지 필터링 구성 각 백엔드 애플리케이션 서버 구성 자체 SQS 대기열 사용
 D. Amazon Elasucsearch Service(Amazon ES) 클러스터에 데이터 스트림을 전송하기 위해 견적 유형을 기반으로 여러 Amazon Kinesis Data Firehose 전송 스트림 생성 적절한 전송 스트림으로 메시지를 전송하도록 애플리케이션 구성 검색할 애플리케이션 서버의 각 백엔드 그룹 구성 Amazon ES의 메시지 및 그에 따라 처리
 답: C

NO.15 한 회사는 지난 15년 동안 온프레미스 데이터 센터에서 Oracle 관계형 데이터베이스로 웹 애플리케이션을 실행해 왔습니다. 회사는 데이터베이스를 AWS로 마이그레이션해야 합니다. 회사는 애플리케이션의 코드를 수정하지 않고도 운영 오버헤드를 줄여야 합니다. 어떤 솔루션이 이러한 요구 사항을 충족합니까?
 A. AWS Database Migration Service(AWS DMS)를 사용하여 데이터베이스 서버를 Amazon RDS로 마이그레이션합니다.
 B. 서버.
 C. AWS Database Migration Service(AWS DMS)를 사용하여 데이터베이스 서버를 Amazon DynamoDB로 마이그레이션합니다.
 D. AWS Snowball Edge Storage Optimized 디바이스를 사용하여 Oracle에서 Amazon Aurora로 데이터를 마이그레이션합니다.
 답: A

NO.16 솔루션 설계자는 표준 보안 제어를 유지하면서 AWS Organizations를 통해 개별 AWS 계정을 개발자에게 제공하려는 회사를 위한 보안 솔루션을 설계하고 있습니다. 개별 개발자는 자신의 계정에 대한 AWS 계정 루트 사용자 수준 액세스 권한을 갖기 때문입니다. , 솔루션 설계자는 새 개발자 계정에 적용되는 필수 AWS CloudTrail 구성이 수정되지 않았는지 확인하려고 합니다. 이러한 요구 사항을 충족하는 작업은 무엇입니까?
 A. CloudTrail에 대한 변경을 금지하는 IAM 정책을 생성하고 이를 루트 사용자에게 연결합니다.
 B. 조직 추적 옵션이 활성화된 개발자 계정 내에서 CloudTrail에 새 추적을 생성합니다.
 C. CloudTrail 변경을 금지하는 SCP(서비스 제어 정책)를 만들고 개발자 계정에 연결합니다.
 D. 마스터 계정의 Amazon 리소스 이름(ARN) 변경만 허용하는 정책 조건으로 CloudTrail에 대한 서비스 연결 역할 생성
 답: C

NO.17 솔루션 설계자는 고가용성 배스천 호스트 아키텍처를 만들어야 합니다. 솔루션은 단일 AWS 리전 내에서 복원력이 있어야 하며 유지 관리에 최소한의 노력만 필요합니다. 솔루션 설계자는 이러한 요구 사항을 충족하기 위해 무엇을 해야 합니까?
 A. UDP 리스너를 사용하여 Auto Scaling 그룹에서 지원하는 Network Load Balancer를 생성합니다.
 B. 파티션 배치 그룹의 인스턴스가 있는 스팟 집합에서 지원하는 Network Load Balancer를 생성합니다.
 C. 다른 가용 영역의 기존 서버가 지원하는 Network Load Balancer를 대상으로 생성합니다.
 D. 여러 가용 영역의 인스턴스를 대상으로 하는 Auto Scaling 그룹에서 지원하는 Network Load Balancer 생성
 답: D

NO.18 대기업의 관리자가 회사의 AWS 계정에 대한 암호화폐 관련 공격을 모니터링하고 방지하려고 합니다. 관리자가 공격으로부터 회사를 보호하기 위해 사용할 수 있는 AWS 서비스는 무엇입니까?
 A. 아마존 코그니토
 B. 아마존 GuardDuty
 C. 아마존 인스펙터
 D. 아마존 메이시
 답: B

NO.19 회사는 Amazon S3에 데이터를 보호하기 전에 데이터 암호화를 의무화하는 Amazon S3 내부 보안 규정 준수 요구 사항에 민감한 사용자 데이터를 저장할 계획입니다. 이러한 요구 사항을 안전하게 유지하기 위해 솔루션 설계자는 무엇을 권장해야 합니까?
 A. 고객이 제공한 암호화 키를 사용한 서버 측 암호화.
 B. Amazon S3 관리형 암호화 키를 사용한 클라이언트 측 암호화.
 C. AWS Management Service(AWS KMS)에 저장된 키를 사용한 서비스 측 암호화
 D. AWS Management Service(AWS KMS)에 저장된 마스터를 사용한 서버 측 암호화
 답: D

NO.20 솔루션 설계자가 애플리케이션을 위한 새로운 Amazon CloudFront 배포를 생성하고 있습니다. 사용자가 제출한 일부 Ine 정보는 민감합니다. 애플리케이션은 HTTPS를 사용하지만 다른 보안 계층이 필요합니다. 민감한 정보는 전체 애플리케이션 스택에서 보호되어야 합니다. 정보에 대한 최종 액세스는 특정 애플리케이션으로 제한되어야 합니다. 솔루션 설계자는 어떤 조치를 취해야 합니까?
 A. CloudFront 서명된 URL 구성
 B. CloudFront 서명 쿠키를 구성합니다.
 C. CloudFront 필드 수준 암호화 프로필 구성
 D. CloudFront를 구성하고 뷰어 프로토콜 정책에 대해 오리진 프로토콜 정책 설정을 HTTPS 전용으로 설정합니다.
 답: C

NO.21 회사에서 MySQL 데이터베이스를 온프레미스에서 AWS로 마이그레이션하려고 합니다. 회사는 최근 비즈니스에 심각한 영향을 미치는 데이터베이스 중단을 경험했습니다. 이러한 일이 다시는 발생하지 않도록 회사는 데이터 손실을 최소화하고 모든 트랜잭션을 최소 2개의 노드에 저장하는 안정적인 AWS 데이터베이스 솔루션을 원합니다. 다음 중 이러한 요구 사항을 충족하는 솔루션은 무엇입니까?
 A. 3개의 가용 영역에 있는 3개의 노드에 동기식 복제를 사용하여 Amazon RDS DB 인스턴스를 생성합니다.
 B. 데이터를 동기식으로 복제할 수 있도록 다중 AZ 기능이 활성화된 Amazon RDS MySQL DB 인스턴스를 생성합니다.
 C. Amazon RDS MySQL DB 인스턴스를 생성한 다음 데이터를 동기식으로 복제하는 별도의 AWS 리전에 읽기 전용 복제본을 생성합니다.
 D. Amazon RDS MySQL DB 인스턴스에 데이터를 동기식으로 복제하기 위해 AWS Lambda 함수를 트리거하는 MySQL 엔진이 설치된 Amazon EC2 인스턴스 생성
 답: B

NO.22 회사가 자연 재해의 영향을 받는 지역에 본사를 두고 있기 때문에 데이터 센터 공급자로부터 일관되지 않은 서비스를 받는 회사는 AWS 클라우드로 완전히 마이그레이션할 준비가 되지 않았지만, 구내 데이터 센터 실패 회사는 외부 공급업체에 연결하는 웹 서버를 실행합니다. AWS와 온프레미스에서 사용 가능한 데이터는 동일해야 합니다. 다운타임이 가장 적은 솔루션 설계자는 어떤 솔루션을 권장해야 합니까?''
 A. Amazon Route 53 장애 조치 레코드 구성 Auto Scaling 그룹의 Application Load Balancer 뒤에서 Amazon EC2 인스턴스에서 애플리케이션 서버 실행 Amazon S3에 데이터를 백업하기 위해 저장된 볼륨으로 AWS Storage Gateway를 설정합니다.
 B. Amazon Route 53 장애 조치 레코드 구성 스크립트에서 AWS CloudFormation 템플릿을 실행하여 Application Load Balancer 뒤에 Amazon EC2 인스턴스 생성 Amazon S3에 데이터를 백업하기 위해 저장된 볼륨으로 AWS Storage Gateway 설정
 C. Amazon Route 53 장애 조치 레코드 구성 VPC와 데이터 센터 간의 AWS Direct Connect 연결 설정 Auto Scaling 그룹의 Amazon EC2에서 애플리케이션 서버 실행 AWS Lambda 함수를 실행하여 AWS CloudFormation 템플릿을 실행하여 애플리케이션 로드 생성 밸런서
 D. Amazon Route 53 장애 조치 레코드를 구성합니다. AWS Lambda 함수를 실행하여 AWS CloudFormation 템플릿을 실행하여 두 개의 Amazon EC2 인스턴스를 시작합니다. Amazon S3에 데이터를 백업하기 위해 저장된 볼륨으로 AWS Storage Gateway를 설정합니다. VPC와 데이터 센터
 답: A

NO.23 한 회사가 글로벌 사용자 기반에 콘텐츠를 제공하기 위해 최근 웹사이트를 개설했습니다. 이 회사는 Amazon CloudFront를 오리진으로 연결된 Amazon EC2 인스턴스와 함께 활용하여 정적 콘텐츠를 저장하고 사용자에게 빠르게 전달하고자 합니다. 솔루션 설계자는 애플리케이션의 고가용성을 어떻게 최적화해야 합니까?
 A. CloudFront에 lambda@Edge 사용
 B. CloudFront에 Amazon S3 Transfer Acceleration 사용
 C. 다른 가용 영역에 다른 EC2 인스턴스를 오리진 그룹의 일부로 구성
 D. 동일한 가용 영역에서 원본 서버 클러스터의 일부로 다른 EC2 인스턴스 구성
 답: A

NO.24 회사에 데이터를 사내 SQL 데이터베이스에 저장하는 전자상거래 애플리케이션이 있습니다. 회사는 이 데이터베이스를 AWS로 마이그레이션하기로 결정했습니다. 그러나 마이그레이션의 일환으로 회사는 일반적인 읽기 요청에 대해 밀리초 미만의 응답을 얻을 수 있는 방법을 찾고자 합니다. 솔루션 설계자는 속도 향상이 가장 중요하며 데이터베이스 읽기에서 반환되는 오래된 데이터의 작은 비율이 허용. 솔루션 아키텍트는 무엇을 추천해야 할까요?'
 A. Amazon RDS 읽기 전용 복제본을 구축합니다.
 B. 데이터베이스를 더 큰 인스턴스 유형으로 구축합니다.
 C. Amazon ElastiCache를 사용하여 데이터베이스 캐시 구축
 D. Amazon Elasticsearch Service(Amazon ES)를 사용하여 데이터베이스 캐시를 구축합니다.
 답: C

NO.25 회사 시설은 건물 전체의 모든 입구에 배지 판독기가 있습니다. 배지가 스캔되면 리더는 HTTPS를 통해 메시지를 보내 특정 입구에 액세스를 시도한 사람을 나타냅니다. 솔루션 설계자는 센서에서 이러한 메시지를 처리하는 시스템을 설계해야 합니다. 솔루션은 고가용성이어야 하며 회사의 보안 팀이 분석할 수 있도록 결과를 제공해야 합니다. 솔루션 설계자는 어떤 시스템 아키텍처를 권장해야 합니까?
 A. Amazon EC2 인스턴스를 시작하여 HTTPS 엔드포인트 역할을 하고 메시지를 처리합니다. 결과를 Amazon S3 버킷에 저장하도록 EC2 인스턴스를 구성합니다.
 B. Amazon API Gateway에서 HTTPS 엔드포인트를 생성합니다. AWS Lambda 함수를 호출하여 메시지를 처리하고 결과를 Amazon DynamoDB 테이블에 저장하도록 API Gateway 엔드포인트를 구성합니다.
 C. Amazon Route 53을 사용하여 수신 센서 메시지를 AWS Lambda 함수로 보냅니다. 메시지를 처리하고 결과를 Amazon DynamoDB 테이블에 저장하도록 Lambda 함수를 구성합니다.
 D. Amazon S3용 게이트웨이 VPC 엔드포인트를 생성합니다. 센서 데이터가 VPC 엔드포인트를 통해 S3 버킷에 직접 기록될 수 있도록 시설 네트워크에서 VPC로 Site-to-Site VPN 연결을 구성합니다.
 답: B

NO.26 솔루션 설계자는 Amazon S3 버킷에 업로드된 모든 객체를 암호화하려면 어떻게 해야 합니까?
 A. PutObject에 s3 x-amz-acl 헤더 세트가 없는 경우 거부하도록 버킷 정책 업데이트
 B. PutObject에 private로 설정된 s3:x-amz-aci 헤더가 없는 경우 거부하도록 버킷 정책을 업데이트합니다.
 C. PutObject에 aws SecureTransport 헤더가 true로 설정되지 않은 경우 거부하도록 버킷 정책 업데이트
 D. PutObject에 x-amz-server-side-encryption 헤더 세트가 없는 경우 거부하도록 버킷 정책을 업데이트합니다.
 답: D

NO.27 솔루션 설계자는 Amazon S3 오리진과 함께 Amazon CloudFront를 사용하여 정적 웹 사이트를 저장하는 솔루션을 설계해야 합니다. 회사의 보안 정책에 따라 AWS WAF에서 모든 웹 사이트 트래픽을 검사해야 합니다. 솔루션 설계자는 이러한 요구 사항을 어떻게 준수해야 합니까?
 A. AWS WAF Amazon 리소스 이름(ARN)에서 오는 요청만 수락하도록 S3 버킷 정책을 구성합니다.
 B. S3 오리진에서 콘텐츠를 요청하기 전에 수신되는 모든 요청을 AWS WAF로 전달하도록 Amazon CloudFront를 구성합니다.
 C. Amazon CloudFront IP 주소가 Amazon S3에만 액세스하도록 허용하는 보안 그룹을 구성합니다. AWS WAF를 CloudFront에 연결합니다.
 D. 오리진 액세스 ID(OAI)를 사용하여 S3 버킷에 대한 액세스를 제한하도록 Amazon CloudFront 및 Amazon S3 구성 배포에서 AWS WAF 활성화
 답: D

NO.28 회사에 Amazon API Gateway에서 호출하는 AWS Lambda 함수에서 실행되는 상태 비저장 웹 애플리케이션이 있습니다. 이 회사는 여러 AWS 리전에 애플리케이션을 배포하여 리전 장애 조치 기능을 제공하려고 합니다. 솔루션 설계자는 트래픽을 여러 지역으로 라우팅하기 위해 무엇을 해야 합니까?
 A. 각 리전에 대해 Amazon Route 53 상태 확인을 구성합니다. 활성-활성 장애 조치 구성을 사용합니다.
 B. 각 리전에 대한 오리진이 있는 Amazon CloudFront 배포를 생성합니다. CloudFront 상태 확인을 사용하여 트래픽을 라우팅합니다.
 C. AWS Transit Gateway 생성 각 리전의 API Gateway 엔드포인트에 전송 게이트웨이 연결 요청을 라우팅하도록 전송 게이트웨이를 구성합니다.
 D. AWS Global Accelerator를 사용하여 각 리전에 엔드포인트가 있는 액셀러레이터를 생성합니다. Global Accelerator가 엔드포인트의 상태를 자동으로 모니터링하고 요청을 라우팅하도록 허용합니다.
 답: A

NO.29 회사는 대량의 데이터를 처리합니다. a. 출력 데이터는 Amazon S3 Standard 스토리지의 S3 버킷에 저장되며, 여기서 1개월 동안 분석됩니다. 1개월의 분석 기간 후에도 데이터에 즉시 액세스할 수 있어야 합니다. 어떤 스토리지 솔루션이 이러한 요구 사항을 가장 비용 효율적으로 충족합니까?
 A. 30일 후에 객체를 S3 Glacier로 전환하도록 S3 수명 주기 정책을 구성합니다.
 B. 30일 후에 객체를 S3 Glacier로 전환하도록 S3 Intelligent-Tiering을 구성합니다.
 C. 30일 후에 객체를 S3 One Zone-Infrequent Access(S3 One Zone-IA)로 전환하도록 S3 수명 주기 정책을 구성합니다.
 D. 30일 후에 객체를 삭제하도록 S3 수명 주기 정책을 구성합니다. 삭제된 객체를 필요에 따라 즉시 복원할 수 있도록 S3 버킷에서 버전 관리를 활성화합니다.
 답: B

NO.30 웹 사이트는 매일 정오에 트래픽 버스트를 수신하는 웹 애플리케이션을 실행합니다. 사용자는 매일 새로운 사진과 컨텍스트를 업로드하지만 시간 초과에 대해 불평합니다. 설계자는 Amazon EC2 Auto Scaling 그룹을 사용하며 사용자 요청에 응답하기 전에 부팅 시 사용자 지정 애플리케이션을 시작하는 데 일관되게 1분이 걸립니다. 솔루션 설계자는 변화하는 트래픽에 더 잘 대응하기 위해 설계자를 어떻게 재설계해야 합니까?
 A. 느린 시작 구성으로 Network Load Balancer를 구성합니다.
 B. 직접 요청을 서버로 오프로드하도록 Redis용 AWS ElastiCache를 구성합니다.
 C. 인스턴스 준비 조건으로 Auto Scaling 단계 조정 정책을 구성합니다.
 D. Application Load Balancer를 오리진으로 사용하도록 Amazon CloudFront를 구성합니다.
 답: C
  https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html#as-stepscaling-warmup "단계 정책을 생성하는 경우 시간(초)을 지정할 수 있습니다. 새로 시작된 인스턴스가 워밍업되는 데 시간이 걸립니다. 지정된 워밍업 시간이 만료될 때까지 인스턴스는 Auto Scaling 그룹의 집계된 지표에 포함되지 않습니다. 단계 조정 섹션의 예를 사용하여 지표가 다음을 얻는다고 가정합니다. 60에서 62로, 새 인스턴스가 아직 워밍업 중일 때 62가 됩니다. 현재 용량은 여전히 ​​10개 인스턴스이므로 1개의 인스턴스가 추가됩니다(10개 인스턴스의 10%). 그러나 그룹의 원하는 용량은 이미 11개입니다. 따라서 조정 정책은 원하는 용량을 더 이상 늘리지 않습니다.새 인스턴스가 아직 워밍업되는 동안 지표가 70에 도달하면 3개의 인스턴스(인스턴스 10개 중 30%)를 추가해야 합니다. 그러나 그룹의 원하는 용량 는 이미 11이므로 2개의 인스턴스만 추가하여 원하는 새 용량인 13 in 입장"

NO.31 한 회사에서 이미지 처리를 위한 2계층 애플리케이션을 운영하고 있습니다. 애플리케이션은 각각 하나의 퍼블릭 서브넷과 하나의 프라이빗 서브넷이 있는 두 개의 가용 영역을 사용합니다. 웹 계층용 ALB(Application Load Balancer)는 퍼블릭 서브넷을 사용합니다. 애플리케이션 계층의 Amazon EC2 인스턴스는 프라이빗 서브넷을 사용합니다. 사용자는 응용 프로그램이 예상보다 느리게 실행되고 있다고 보고합니다. 웹 서버 로그 파일의 보안 감사에 따르면 애플리케이션이 소수의 IP 주소로부터 수백만 건의 불법적인 요청을 수신하고 있습니다. 솔루션 설계자는 회사가 보다 영구적인 솔루션을 조사하는 동안 즉각적인 성능 문제를 해결해야 합니다. 솔루션 설계자는 이 요구 사항을 충족하기 위해 무엇을 권장해야 합니까?
 A. 웹 계층에 대한 인바운드 보안 그룹을 수정합니다. 리소스를 소비하는 IP 주소에 대한 거부 규칙을 추가합니다.
 B. 웹 계층 서브넷에 대한 네트워크 ACL을 수정합니다. 리소스를 소비하는 IP 주소에 대한 인바운드 거부 규칙을 추가합니다.
 C. 애플리케이션 계층에 대한 인바운드 보안 그룹을 수정합니다. 리소스를 소비하는 IP 주소에 대한 거부 규칙을 추가합니다.
 D. 애플리케이션 계층 서브넷에 대한 네트워크 ACL을 수정합니다. 리소스를 소비하는 IP 주소에 대한 인바운드 거부 규칙을 추가합니다.
 답: B

NO.32 회사에 산발적인 사용 패턴이 있는 웹 응용 프로그램이 있습니다. 매월 초에 사용량이 많습니다. 매주 초에는 사용량이 보통이고 주중에는 사용량이 예측할 수 없습니다. 응용 프로그램은 웹 서버와 실행 중인 MySQL 데이터베이스 서버로 구성됩니다. 데이터 센터 내부 회사는 애플리케이션을 AWS 클라우드로 이동하고 데이터베이스 수정이 필요하지 않은 비용 효율적인 데이터베이스 플랫폼을 선택해야 합니다. 어떤 솔루션이 이러한 요구 사항을 충족할 것입니까?''
 A. Amazon DynamoDB
 B. MySQL용 Amazon RDS
 C. MySQL 호환 Amazon Aurora Serverless
 D. Auto Scaling 그룹의 Amazon EC2에 배포된 MySQL
 답: B

NO.33 회사에서 Amazon Elastic Container Service(Amazon ECS) 클러스터에 배포된 새 애플리케이션을 시작하고 Fargate 시작 유형 또는 ECS 작업을 사용하고 있습니다. 출시 그러나 회사는 활용도가 감소할 때 비용을 절감하고자 합니다. 솔루션 설계자는 무엇을 권장해야 합니까?
 A. Amazon EC2 Auto Scaling을 사용하여 이전 트래픽 패턴을 기반으로 특정 기간에 확장
 B. AWS Lambda 함수를 사용하여 Amazon CloudWatch 경보를 트리거하는 지표 위반을 기반으로 Amazon ECS 확장
 C. ECS 지표 위반이 Amazon CloudWatch 경보를 트리거할 때 확장하는 간단한 조정 정책과 함께 Amazon EC2 Auto Scaling을 사용합니다.
 D. 대상 추적 정책과 함께 AWS Application Auto Scaling을 사용하여 ECS 지표 위반이 Amazon CloudWatch 경보를 트리거할 때 확장
 답: C

NO.34 다음 IAM 정책은 IAM 그룹에 연결됩니다. 이것은 그룹에 적용된 유일한 정책입니다. 그룹 구성원에 대한 이 정책의 유효 IAM 권한은 무엇입니까?
 A. 그룹 구성원은 us-east-1 리전 내에서 모든 Amazon EC2 작업이 허용됩니다. Allow 권한 이후의 문장은 적용되지 않습니다.
 B. 그룹 구성원은 MFA(다단계 인증)로 로그인하지 않는 한 us-east-1 리전에서 Amazon EC2 권한이 거부됩니다.
 C. 그룹 구성원은 ec2 Stoplnstances 및 ec2가 허용됩니다. 다단계 인증(MFA) 그룹 구성원으로 로그인할 때 모든 리전에 대한 TerminateInstances 권한은 다른 모든 Amazon EC2 작업이 허용됩니다.
 D. 그룹 구성원은 ec2 Stoplnstances 및 ec2가 허용됩니다. 다단계 인증(MFA) 그룹 구성원으로 로그인한 경우에만 us-east-1 리전에 대한 인스턴스 권한을 종료하면 us-east-1 리전 내에서 다른 모든 Amazon EC2 작업이 허용됩니다.
 답: D

NO.35 한 회사는 최근 애플리케이션 마이그레이션 이니셔티브에 대한 지원을 위해 AWS Managed Service Provider(MSP) 파트너와 계약을 체결했습니다. 솔루션 설계자는 기존 AWS 계정의 Amazon 머신 이미지(AMI)를 MSP 파트너의 AWS 계정과 공유해야 합니다. AMI는 Amazon Elastic Block Store(Amazon EBS)의 지원을 받으며 고객 관리형 고객 마스터 키(CMK)를 사용하여 EBS 볼륨 스냅샷을 암호화합니다. 솔루션 설계자가 MSP 파트너의 AWS 계정과 AMI를 공유하는 가장 안전한 방법은 무엇입니까?
 A. 암호화된 AMI 및 스냅샷을 공개적으로 사용할 수 있도록 합니다. MSP 파트너의 AWS 계정이 키를 사용할 수 있도록 CMK의 키 정책을 수정합니다.
 B. AMI의 launchPermission 속성을 수정합니다. MSP 파트너의 AWS 계정과만 AMI를 공유하십시오. MSP 파트너의 AWS 계정이 키를 사용할 수 있도록 CMK의 키 정책을 수정합니다.
 C. AMI의 launchPermission 속성 수정 MSP 파트너의 AWS 계정과만 AMI를 공유합니다. 암호화를 위해 MSP 파트너가 소유한 새 CMK를 신뢰하도록 CMK의 키 정책을 수정합니다.
 D. 소스 계정에서 MSP 파트너의 AWS 계정에 있는 Amazon S3 버킷으로 AMI를 내보냅니다. MSP 파트너가 소유한 CMK로 S3 버킷을 암호화하고 MSP 파트너의 AWS 계정에서 AMI를 복사하고 시작합니다.
 답: A

NO.36 회사에서 VPC 내의 데이터베이스와 통신할 웹 애플리케이션을 AWS에서 호스팅하려고 합니다. 애플리케이션은 가용성이 높아야 합니다. 솔루션 아키텍트는 무엇을 추천해야 합니까?
 A. 두 개의 Amazon EC2 인스턴스를 생성하여 로드 밸런서 뒤에 웹 서버를 호스팅한 다음 데이터베이스를 대규모 인스턴스에 배포합니다.
 B. 웹 서버용 Auto Scaling 그룹을 사용하여 여러 가용 영역에 로드 밸런서를 배포한 다음 여러 가용 영역에 Amazon RDS를 배포합니다.
 C. 웹 서버용 Auto Scaling 그룹이 있는 퍼블릭 서브넷에 로드 밸런서를 배포한 다음 프라이빗 서브넷의 Amazon EC2 인스턴스에 데이터베이스를 배포합니다.
 D. Auto Scaling 그룹이 있는 두 개의 웹 서버를 배포하고 두 개의 웹 서버를 가리키는 도메인을 구성한 다음 여러 가용 영역에 데이터베이스 아키텍처를 배포합니다.
 답: B

NO.37 회사에 동일한 AWS 계정 내 us-west-2 리전에 위치한 두 개의 VPC가 있습니다. 회사는 이러한 VPC 간의 네트워크 트래픽을 허용해야 합니다. 매월 약 500GB의 데이터 전송이 VPC 간에 발생합니다. 이러한 VPC를 연결하는 가장 비용 효율적인 솔루션은 무엇입니까?'
 A. AWS Transit Gateway를 구현하여 VPC 연결 VPC 간 통신에 Transit Gateway를 사용하도록 각 VPC의 라우팅 테이블 업데이트
 B. VPC 간에 AWS Site-to-Stte VPN 터널을 구현합니다. VPC 간 통신에 VPN 터널을 사용하도록 각 VPC의 라우팅 테이블 업데이트
 C. VPC 간에 VPC 피어링 연결을 설정합니다. VPC 간 통신에 VPC 피어링 연결을 사용하도록 각 VPC의 라우팅 테이블을 업데이트합니다.
 D. VPC 간에 1GB AWS Direct Connect 연결을 설정합니다. VPC 간 통신에 Direct Connect 연결을 사용하도록 각 VPC의 라우팅 테이블을 업데이트합니다.
 답: C

NO.38 회사의 웹사이트는 다운로드 가능한 과거 성과 보고서를 사용자에게 제공합니다. 웹 사이트에는 전 세계적으로 회사의 웹 사이트 요구 사항을 충족하도록 확장할 수 있는 솔루션이 필요합니다. 솔루션은 비용 효율적이어야 하고 인프라 리소스 프로비저닝을 제한하며 가능한 가장 빠른 응답 시간을 제공해야 합니다. 솔루션 설계자는 이러한 요구 사항을 충족하기 위해 어떤 조합을 권장해야 합니까?
 A. Amazon CloudFront 및 Amazon S3
 B. AWS Lambda 및 Amazon DynamoDB
 C. Amazon EC2 Auto Scaling이 있는 Application Load Balancer
 D. 내부 Application Load Balancer가 있는 Amazon Route 53
 답: A

NO.39 회사에 프로덕션 AWS 계정에 기밀 정보가 포함된 Amazon S3 버킷이 있습니다. 회사는 해당 계정에 대해 AWS CloudTrail을 활성화했습니다. 계정은 로그 사본을 Amazon CloudWatch Logs로 보냅니다. 회사는 읽기 및 쓰기 데이터 이벤트를 기록하도록 S3 버킷을 구성했습니다. 회사 감사자가 S3 버킷의 일부 객체가 삭제되었음을 발견했습니다. 솔루션 설계자는 감사자에게 객체를 삭제한 사람에 대한 정보를 제공해야 합니다. 솔루션 설계자는 이 정보를 제공하기 위해 무엇을 해야 합니까?
 A. CloudWatch Logs 필터를 생성하여 S3 버킷에 대한 S3 쓰기 API 호출을 추출합니다.
 B. Amazon Athena로 CloudTrail togs를 쿼리하여 S3 버킷에 대한 S3 쓰기 API 호출 식별
 C. AWS Trusted Advisor를 사용하여 콘텐츠를 삭제한 S3 쓰기 API 호출에 대한 보안 검사 수행
 D. AWS Config를 사용하여 S3 버킷의 구성 변경 추적 이 세부 정보를 사용하여 콘텐츠를 삭제한 S3 쓰기 API 호출을 추적합니다.
 답: B

NO.40 클라이언트와 서버 간의 통신을 위해 UDP를 사용하는 실시간 멀티플레이어 게임을 개발 중인 회사 개입 없이 확장되는 데이터베이스 솔루션의 점수 및 기타 비관계형 데이터 솔루션 설계자는 어떤 솔루션을 권장해야 합니까?
 A. 트래픽 분산에는 Amazon Route 53을, 데이터 저장에는 Amazon Aurora Serverless를 사용하십시오.
 B. 트래픽 분산에는 Network Load Balancer를 사용하고 데이터 저장에는 Amazon DynamoDB 온디맨드 사용
 C. 트래픽 분산에는 Network Load Balancer를 사용하고 데이터 저장에는 Amazon Aurora Global Database 사용
 D. 트래픽 분산에는 Application Load Balancer를 사용하고 데이터 저장에는 Amazon DynamoDB 글로벌 테이블 사용
 답: B

