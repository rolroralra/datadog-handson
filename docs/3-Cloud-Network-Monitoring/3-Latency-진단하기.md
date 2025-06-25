현재 Storedog 애플리케이션은 응답이 느리거나, 오류가 발생하거나, 아예 응답하지 않을 수도 있는 상태입니다. 이슈의 원인은 Storedog 애플리케이션의 코드 버그 / 사용 중인 시스템 리소스 부족 / 의존하는 타 서비스의 문제 / 서비스 간 네트워크 연결의 문제 등 다양할 수 있습니다. 이번 실습은 **Cloud Network Monitoring**(CNM)에 대한 것이므로, 네트워크 분석 페이지에서 문제를 진단하는 것부터 시작하겠습니다.

1. **Analytics** 탭을 클릭하여 Network Analytics(네트워크 분석) 페이지로 돌아갑니다.
    
2. 검색 바를 초기화합니다.
    
3. **Summary Graphs(요약 그래프)** 섹션에서 다음 세 개의 그래프를 확인합니다: **Volume Sent(송신 트래픽)**, **TCP Retransmits % (TCP 재전송 비율)**, **RTT (왕복 시간, Round Trip Time)**
    
4. **TCP Retransmits %** 부분을 클릭하여 **TCP Retransmits**로 변경하고, **RTT**를 클릭하여 **TCP Latency**(지연 시간)으로 변경합니다. :
    
    [![Network page showing retransmits and slow round trip times](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c25ce6ac7ea3281cde2f91211769e450/assets/03-cnm/storedog_rtt_retransmits.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c25ce6ac7ea3281cde2f91211769e450/assets/03-cnm/storedog_rtt_retransmits.png)
    
    오른쪽 두 개의 그래프에서 두 가지 문제가 확인됩니다: **높은 TCP 재전송(Retransmits) 발생**, 특정 서비스에서 상대적으로 **높은 네트워크 지연 시간(Latency)**.
    
    Retransmits(재전송)은 전송 실패한 TCP 패킷을 재전송하는 횟수를 의미합니다. 막대 그래프 위에 마우스를 올리면 재전송 횟수 및 발생한 흐름(Flow)을 확인할 수 있습니다.
    
    Latency(지연 시간)은 TCP 프레임이 전송된 후 승인될 때까지 걸리는 시간을 의미합니다. 그래프의 점 위에 마우스를 올려 해당 흐름에서 발생한 지연 시간을 확인할 수 있습니다.
    

위 그래프를 통해, 문제가 있는 Flow에서 공통적으로 나타나는 서비스가 `discounts-service`라는 것을 유추할 수 있습니다. 이를 확인하기 위해 네트워크 흐름 테이블(Flows Table)에서 **Retransmits(재전송량)**, **Volume Sent(송신량)**, **Latency(지연 시간)** 값을 비교해 보겠습니다.

1. **TCP** 열에서 **Latency(지연 시간)** 열을 클릭하여, 내림차순(높은 값부터)으로 정렬합니다. `discounts-service`의 지연 시간이 가장 높은 것을 확인할 수 있습니다.
    
    [![Network flows table sorted by latency.](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/01cb5267a7634ef9515fccd14e035a60/assets/03-cnm/high_latency.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/01cb5267a7634ef9515fccd14e035a60/assets/03-cnm/high_latency.png)
    
2. **Retransmits(재전송)** 열을 클릭하여 정렬합니다. `discounts-service`와 관련된 흐름에서 가장 많은 재전송이 발생했음을 확인할 수 있습니다.
    
    [![Network flows table sorted by retransmits.](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/191b66dcd9cf3599a8b8da2f9ea6061a/assets/03-cnm/high_retransmits.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/191b66dcd9cf3599a8b8da2f9ea6061a/assets/03-cnm/high_retransmits.png)
    
    CNM은 **Application Performance Monitoring(APM)과 연동**되므로, 네트워크 Flow와 관련된 애플리케이션 코드 트레이스를 직접 확인할 수 있습니다. 이 기능은 네트워크 메트릭을 분석할 때 애플리케이션 내부 문제를 깊이 조사하는 데 유용합니다.
    
3. 재전송 관련 애플리케이션 트레이스를 확인하기 위해, 재전송이 가장 많이 발생한 `discounts-service`와 `store-frontend` 간의 흐름을 클릭하여 해당 흐름의 세부 정보 패널을 엽니다:
    
    [![Flow details side panel showing flow details between store-frontend and discounts-service](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/96f58575c777e68eb493727ec91e2018/assets/03-cnm/flow_detail_side_panel.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/96f58575c777e68eb493727ec91e2018/assets/03-cnm/flow_detail_side_panel.png)
    
4. 패널 하단의 **Traces** 탭을 클릭하여, 해당 Flow와 관련된 트레이스를 확인합니다. (패널의 크기는 가로 구분선을 드래그하여 조정할 수 있습니다.)
    
    > Note
    > 
    > 트레이스가 표시되지 않는다면, 시간 범위를 `1 hour(지난 1시간)`로 설정해 보세요.
    
5. 트레이스 목록에서 하나를 클릭하면 재전송이 발생한 시간 동안 기록된 APM 트레이스의 세부 정보 패널이 열립니다.
    
6. 트레이스 세부 정보 패널을 닫습니다.
    
    트레이스 페이지에서 스크롤을 통해 오류(Error) 또는 비정상적으로 긴 Duration(실행 시간)을 가진 트레이스를 찾습니다. **Duration(실행 시간)** 기준으로 정렬하면, 문제가 발생한 트레이스를 더 쉽게 찾을 수 있습니다. `Spree::HomeController#index` 트레이스가 자주 문제가 되는 것을 확인할 수 있습니다.
    
    [![Traces sorted by duration](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/47f84775553bc6c869a8069e385e8214/assets/03-cnm/traces-by-duration.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/47f84775553bc6c869a8069e385e8214/assets/03-cnm/traces-by-duration.png)
    
7. 느린 트레이스를 클릭하여 Flame Graph를 확인할 수 있습니다:
    
    [![Flame graph for a slow trace Home controller trace](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/4d9c8786a75eeb83f130bac6a1e3445f/assets/03-cnm/apm_discounts_span.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/4d9c8786a75eeb83f130bac6a1e3445f/assets/03-cnm/apm_discounts_span.png)
    
    Flame Graph를 보면 `Spree:HomeController#index`가 `discounts` 서비스에 `GET` 요청을 보내는 데 비정상적으로 긴 시간이 소요된 것을 확인할 수 있습니다. 애플리케이션 내부 오류는 없고, 응답을 기다리는 빈 Span이 많은 것이 확인됩니다.
    
    또한 PostgreSQL 데이터베이스에서 대부분의 실행 시간이 소요되는 트레이스도 다수 확인할 수 있습니다. 하지만 쿼리 실패(Failed Query) 또는 애플리케이션 오류(Application Error)가 발생한 것은 아닌 것으로 보입니다.
    
    [![Apparently slow postgres queries](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/8c8bed70e6696e1c30817f55acabf0f5/assets/03-cnm/apparently_slow_postgres.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/8c8bed70e6696e1c30817f55acabf0f5/assets/03-cnm/apparently_slow_postgres.png)
    

네트워크 페이지에서 네트워크 Flow를 살펴보고 다른 느린 APM 트레이스를 확인하는데 시간을 써 봅시다. 그리고, `advertisements-service`와 관련된 네트워크 Flow도 살펴봅시다. 지연시간이나, 재전송이 늘어났는지 확인해볼 수 있겠습니다.

분석을 더 해보면, `discounts-service` 컨테이너의 네트워크 연결이 비정상적으로 작동하여 `database` 및 `store-frontend` 간의 패킷 손실(Packet Loss)이 발생하고 있음을 의심할 수 있습니다. 실제 운영 환경에서는 Docker 호스트 레벨까지 내려가 네트워크 진단(Network Diagnostics)을 수행하여 이 문제의 근본 원인을 파악해야 할 수도 있습니다.

이번 실습에서는 아래 명령어를 실행하여 문제를 해결할 수 있습니다.

1. 랩 터미널에서 다음 명령어를 실행합니다:
    
    bash
    
    copy
    
    run
    
    ```
    fixnetwork
    ```
    
2. Network Analytics(네트워크 분석) 페이지로 돌아가서, 재전송 횟수(Retransmits) 및 평균 왕복 시간(Round Trip Time, RTT)이 점진적으로 감소하는 것을 확인합니다.
    
    [![Retransmits and latency trending downward](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c6b1e2b246e4650d05f33001953e2b37/assets/03-cnm/retransmits_latency_downward.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c6b1e2b246e4650d05f33001953e2b37/assets/03-cnm/retransmits_latency_downward.png)
    
    > Note
    > 
    > 이 변화가 반영되는 데 5분 이상 걸릴 수 있습니다.
    

재전송과 지연 시간이 0에 가까워지는 것을 확인하면, 다음 섹션으로 이동하시면 됩니다.