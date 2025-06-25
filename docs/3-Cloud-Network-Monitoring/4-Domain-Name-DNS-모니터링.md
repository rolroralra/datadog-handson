CNM은 네트워크 Flow에 도메인 네임을 태깅(Tagging)하고, DNS 서버를 모니터링할 수 있는 기능을 제공합니다.

## 도메인 태그

Datadog은 네트워크 Flow의 대상 IP 주소를 도메인 네임으로 변환(Resolve)하려고 시도합니다. 이를 통해 도메인 수준에서 어떤 서비스와 통신하고 있는지 확인할 수 있습니다.

1. Network Analytics(네트워크 분석) 페이지에서 **검색 바**와 **View clients as / View servers as** 필드를 초기화합니다.
    
2. **View clients as** 옵션을 `container_name`으로 설정합니다.
    
3. **View servers as** 옵션을 `domain`으로 설정합니다.
    
    [![Network Analytics page with the view clients as field set to container_name and the view servers as field set to domain.](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/fb06c65830e22b6f2338e08a7126c06d/assets/03-cnm/view-container-domain.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/fb06c65830e22b6f2338e08a7126c06d/assets/03-cnm/view-container-domain.png)
    
    > Note
    > 
    > `domain` 옵션이 **View servers as** 목록에 표시되지 않는다면, 도메인 인덱싱이 완료될 때까지 더 기다려야 할 수 있습니다. 도메인 정보는 다른 패싯(Facet)보다 인덱싱 속도가 느리게 처리될 수 있으나, 곧 표시됩니다.
    
4. **Filter Traffic(트래픽 필터)** 설정에서 `Show N/A (Untagged traffic)` 옵션을 Disable 해서 태그가 없는 트래픽을 숨깁니다.
    
    [![Grouping by container name and domain, with Agent flows](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/34515216f6c2d38b1dd6646685e9cb13/assets/03-cnm/container_name_domain_with_agent.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/34515216f6c2d38b1dd6646685e9cb13/assets/03-cnm/container_name_domain_with_agent.png)
    
    Storedog 컨테이너에서 발생한 네트워크 Flow에서 CNM이 확인한 **도메인 네임**을 확인할 수 있습니다. 이때, `lab_datadog_1`에서 많은 트래픽이 발생하는 것을 볼 수 있습니다. 이는 Datadog Agent 컨테이너에서 발생하는 트래픽입니다. 또한 Datadog Agent가 트레이스, 로그, 프로세스 등의 데이터를 여러 `datadoghq.com` 서브도메인으로 전송하는 것을 확인할 수 있습니다.
    
5. **Filter Traffic** 설정에서 `Show traffic sent from the Datadog Agent and API(Agent 및 API에서 전송된 트래픽 표시)` 옵션을 비활성화합니다.
    
    [![Grouping by container name and domain, without Agent flows](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/1c3ebf287b8d6d6da6d7a0e0f5365fff/assets/03-cnm/container_name_domain_no_agent.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/1c3ebf287b8d6d6da6d7a0e0f5365fff/assets/03-cnm/container_name_domain_no_agent.png)
    
    이제는, `태깅된 컨테이너`에서 `태깅된 외부 도메인`으로 전송된 네트워크 Flow만 남아 있습니다. 즉, CNM이 도메인으로 변환한 트래픽만 확인 가능해졌습니다.
    
    여전히 일부 Datadog Agent에서 발생한 트래픽이 캡쳐되고 있지만, 이는 Network Time Protocol(NTP) 서비스로의 요청입니다. `datadoghq.com` 서브도메인과는 관련이 없습니다. 또 다른 Flow로는, Storedog 앱의 트래픽을 생성하는 `lab_puppeteer_1` 컨테이너가 있습니다.
    
6. **Show traffic sent from the Datadog Agent and API** 옵션을 다시 활성화합니다.
    
7. 왼쪽 패싯(Facets) 패널에서 "Domain" 섹션을 찾아 특정 도메인을 클릭합니다. 그러면 해당 도메인과 관련된 네트워크 Flow만 필터링됩니다.
    
8. 필터링된 Flow을 클릭하여 세부 정보를 확인합니다.
    

이 기능을 활용하면, **서비스가 예상된 도메인과 통신하는지 확인**할 수 있으며, **특정 도메인과 관련된 네트워크 Flow를 모니터링**할 수 있습니다.

## DNS 모니터링

CNM은 **DNS 트래픽 및 DNS 서버를 모니터링**할 수 있습니다. 이번 실습 환경에는 자체 DNS 서버가 포함되지 않았으므로, 모든 아웃바운드 DNS 요청은 Docker 호스트가 처리합니다. 그래도 해당 DNS 요청은 여전히 모니터링할 수 있습니다.

1. Network Analytics(네트워크 분석) 페이지에서, **DNS** 탭을 클릭하여 DNS 모니터링 페이지로 이동합니다.
    
2. 검색 바(Search bar)를 초기화합니다.
    
3. **View clients as** 및 **View servers as** 옵션을 `ip`로 설정합니다.
    
    [![DNS page viewing clients and servers as ip](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c3687566d537bca85c15a01025dd7e9e/assets/03-cnm/dns-monitoring-page.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c3687566d537bca85c15a01025dd7e9e/assets/03-cnm/dns-monitoring-page.png)
    
4. **Summary Graphs**(요약 그래프)에서 다음 세 개의 그래프를 확인합니다:
    
    - **# DNS Requests (DNS 요청 수)**
    - **% Errors by type (에러 유형별 비율)**
    - **Response time (Success) (응답 시간 - 성공 요청)**
    
    [![All DNS requests](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/60b7a42a38941461484b37c987436166/assets/03-cnm/all_dns_requests.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/60b7a42a38941461484b37c987436166/assets/03-cnm/all_dns_requests.png)
    
5. 결과 테이블에서 하나의 Flow를 클릭하여 해당 DNS 요청의 세부 정보 패널을 확인합니다.
    
6. **COMMON CLIENT TAGS(공통 클라이언트 태그)** 섹션에서 `dd101-sre-host` 태그를 확인할 수 있습니다. 이는 Docker daemon이 실행되는 실습 VM을 나타냅니다. Datadog Agent가 DNS 요청에 자동으로 추가한 태그들도 함께 확인할 수 있습니다.
    
    [![DNS details](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5422756318e67c1456d9b44ea4d7ad31/assets/03-cnm/dns_details.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5422756318e67c1456d9b44ea4d7ad31/assets/03-cnm/dns_details.png)
    

자체 DNS 서버를 운영하는 경우, 이 도구를 사용하여 **DNS 서버의 상태 및 인프라 내 Flow를 모니터링**할 수 있습니다.

---
이번 실습에서 우리는 다음과 같은 내용을 배웠습니다:

- Datadog Agent의 Docker 컨테이너에서 CNM을 활성화하는 방법
- Datadog에서 CNM 메트릭을 활용하여 서비스 간 네트워크 모니터링
- 네트워크 맵(Network Map)을 사용하여 Flow를 시각적으로 분석하는 방법
- CNM을 활용하여 서비스 간 네트워크 문제를 감지하는 방법
- 서비스가 통신하는 도메인을 모니터링하는 방법
- 인프라 내의 DNS 네트워크 Flow를 모니터링하는 방법

다음 실습이 소개되면, 화면 오른쪽 아래의 **Next(다음)** 버튼을 클릭하여 실습을 이어가세요.