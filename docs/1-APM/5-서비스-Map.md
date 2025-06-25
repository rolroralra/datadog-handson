이전 섹션에서 Python의 `ddtrace` 라이브러리를 사용하는 **Storedog의 discounts 서비스**를 추적하는 방법을 배웠습니다. 이와 유사하게, **advertisements 서비스**도 같은 Python 라이브러리를 사용합니다. 반면, **frontend 서비스**는 Ruby 프레임워크로 구축되었습니다. 다행히 Datadog에서는 Ruby용 `ddtrace` 클라이언트도 제공합니다. IDE 탭에서, `docker-compose.yml` 파일을 열어 다른 언어의 서비스들이 APM에 어떻게 구성되었는지 확인할 수 있습니다.

이제 APM이 활성화된 모든 서비스가 서로 어떻게 상호작용하는지 **서비스 맵에서 확인**해 보겠습니다.

1. **[APM > Service Map](https://app.datadoghq.com/apm/map)** 페이지로 이동하여 서비스 간의 통신 흐름을 시각적으로 확인합니다:
    
    [![All the services map in cluster mode](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/b8bf58862a16c212d43d261c9e9021fb/assets/01-apm/service_map_cluster.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/b8bf58862a16c212d43d261c9e9021fb/assets/01-apm/service_map_cluster.png)
    
    > Note
    > 
    > 새롭게 계측된 서비스가 서비스 맵에 나타나기까지 시간이 걸릴 수 있습니다. 바로 보이지 않으면 잠시만 기다려 주세요.
    
2. 서비스 맵에는 두 가지 레이아웃이 있습니다: **Cluster** (작은 규모의 서비스 맵에 최적화) 와 **Flow** (더 큰 서비스 맵에 최적화).
    
    오른쪽 상단의 **Flow** 버튼을 클릭하여 레이아웃을 변경해 보세요:
    
    [![All the services map in flow mode](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/381605949d46f0cdb4f852a21240275e/assets/01-apm/service_map_flow.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/381605949d46f0cdb4f852a21240275e/assets/01-apm/service_map_flow.png)