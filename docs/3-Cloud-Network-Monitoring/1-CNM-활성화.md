이번 실습에서는 Datadog Agent 컨테이너가 이미 CNM을 사용할 수 있도록 구성되어 있습니다. 이 설정은 `docker-compose.yml` 파일에서 CNM 관련 **환경 변수 추가**를 통해 이루어졌습니다:

- `environment` 섹션에 `DD_SYSTEM_PROBE_NETWORK_ENABLED=true` 추가
- `volumes` 섹션에 `/sys/kernel/debug:/sys/kernel/debug` 추가
- 호스트 리소스에 접근할 수 있도록 `cap_add` 섹션 추가
- AppArmor 제한을 방지하기 위한 `security_opt` 섹션 추가

[![Docker compose file with CNM configuration](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/ea3ebfbf1943d37c66e345d8114edea4/assets/03-cnm/cnm_docker_compose.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/ea3ebfbf1943d37c66e345d8114edea4/assets/03-cnm/cnm_docker_compose.png)

`cap_add` 및 `security_opt` 섹션은 - CNM이 [eBPF](https://en.wikipedia.org/wiki/Berkeley_Packet_Filter#Extensions_and_optimizations)을 활용하기 때문에 필요합니다. eBPF는 **고성능 커널 레벨 인터페이스**로, Linux 시스템의 데이터 링크 계층을 접근하려면 추가 권한이 필요합니다.

일반 서버 호스트, Kubernetes, 또는 ECS에서 CNM을 구성하는 방식도 유사하며, 자세한 내용은 [CNM 설치 문서](https://docs.datadoghq.com/network_monitoring/performance/setup/?tab=docker)에서 확인할 수 있습니다.