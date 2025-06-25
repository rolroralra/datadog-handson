모니터링을 위해 메트릭 지표를 계속 쳐다보고 있을 수는 없겠지요. Datadog Monitor를 통해 메트릭에 대해 알림을 설정할 수 있습니다.

discounts 서비스에 대한 Flask 요청시간이 2초를 초과하면 알림을 주는 Monitor를 만들어 보겠습니다.

1. 좌측 메뉴에서 [Monitors > New Monitor](https://app.datadoghq.com/monitors/create)로 이동합니다. Datadog이 제공하는 다양한 유형의 모니터를 확인하세요. 각 유형 위에 마우스를 올려놓으면 요약을 볼 수 있습니다.
    
2. **Metric**을 선택하여 메트릭 모니터를 만들어 보겠습니다.
    
3. 1번 **Choose the detection method** 부분에서 **Threshold Alert**으로 되어 있는 기본값을 이용하겠습니다.
    
4. 2번 **Define the metric** 부분에서 **Metric**을 선택해줍니다. 노란 입력창에서 `trace.flask.request` 메트릭을 선택하고 **From** 부분에서 `service:discounts-service`을 입력하여 쿼리를 설정합니다.
    
5. 3번 **Set alert conditions** 부분에서 **Alert threshold**에 `2`를 입력하고, **Warning threshold** 부분에 `1.5`를 입력하여 임계치를 설정합니다.
    
    현재까지 구성된 새로운 메트릭 모니터는 다음과 같은 형태여야 합니다.:
    
    [![새 Metric Monitor 만들기](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/a19eaee7d1b5ceedb810918b68782b14/assets/04-metrics-monitors/new-metric-monitor-so-far.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/a19eaee7d1b5ceedb810918b68782b14/assets/04-metrics-monitors/new-metric-monitor-so-far.png)
    
6. **Notify your team** 부분에서, monitor 이름을 다음과 같이 설정합니다:
    
    copy
    
    ```
    Discounts 서비스 요청시간
    ```
    
7. 알림을 받았을 때 discounts 서비스를 바로 확인할 수 있도록 APM 페이지의 링크가 포함되어 있다면 좋겠지요? 그리고 알림을 받아야 할 사용자나 메신저 채널도 정확히 지정할 수 있어야겠습니다.
    
    예를 들어, 마크다운으로 다음과 같은 내용을 입력할 수 있습니다.:
    
    copy
    
    ```
    이슈 트랜잭션 분석: [APM](https://app.datadoghq.com/apm/service/discounts-service/flask.request?env=dd101-sre&topGraphs=latency%3Alatency%2CbreakdownAs%3Apercentage%2Cerrors%3Acount%2Chits%3Acount&paused=false)
    
    분석 후 @incident@example.com에 업데이트 필요.
    ```
    
    > Warning
    > 
    > 랩에서 복사 및 붙여넣기 시에 서식이 깨질 수 있습니다. 위에 제공된 메시지와 유사한 메시지를 입력하여 실습해보시기 바랍니다.
    
    알림 텍스트 영역의 구문 문법에 대한 자세한 내용은 [Notifications 데이터독 공식문서](https://docs.datadoghq.com/monitors/notify/)에서 확인할 수 있습니다. 이 문서에서 Slack, PagerDuty 등과 같은 많은 메시지 서비스와의 알림설정 통합에 대한 내용도 설명드리고 있습니다.
    
8. 나머지 기본 설정은 그대로 유지하세요.
    
9. **Create**를 클릭하여 모니터를 생성합니다.
    
    생성된 모니터는 아래와 비슷하게 확인되어야 합니다.:
    
    [![Discounts service monitor](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/4d0e4c138cf4ed5c3bcf23ce1032d186/assets/04-metrics-monitors/discounts_service_monitor.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/4d0e4c138cf4ed5c3bcf23ce1032d186/assets/04-metrics-monitors/discounts_service_monitor.png)
    
    모니터 상태 화면에서 **EVALUATION GRAPH**와 **Status & History** 섹션에 데이터포인트가 나타나기까지 몇 분 시간이 소요됩니다.
    
10. 모니터 페이지 하단으로 스크롤하여 이벤트 **Events** 섹션을 살펴보세요. **Events** 섹션에는 생성과 업데이트 등 모니터와 관련된 모든 이벤트가 표시됩니다.
    

### 모니터와 APM

Datadog APM 페이지에서는 여러군데에서 해당 서비스에서 발생한 모니터의 상태를 자동으로 표시합니다. 이를 통해 연관된 알림설정을 확인하고 상태 페이지로 연결하기 쉽게끔 합니다.:

- [Service Catalog](https://app.datadoghq.com/services?env=dd101-sre) 페이지의 **MONITORS** 컬럼 :
    
    [![Monitor link in service catalog](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/446e3858f3a49da42f67e12ab2fad489/assets/04-metrics-monitors/green_in_service_list.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/446e3858f3a49da42f67e12ab2fad489/assets/04-metrics-monitors/green_in_service_list.png)
    
- 서비스 세부 정보 페이지 상단:
    
    [![Monitor indicator at the top of the service detail page](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/6dcc22347cee0336d66c1b3e79b04922/assets/04-metrics-monitors/monitor_link_service_detail.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/6dcc22347cee0336d66c1b3e79b04922/assets/04-metrics-monitors/monitor_link_service_detail.png)
    
- 서비스 맵 보기:
    
    [![Monitor green in service map](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5cdda9660ac65e792bfaac974de1df90/assets/04-metrics-monitors/green_in_service_map.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5cdda9660ac65e792bfaac974de1df90/assets/04-metrics-monitors/green_in_service_map.png)
    

위의 예시와 같이 APM 곳곳에서 모니터 상태를 확인함으로써 서비스와 관련된 중요한 주요 지표의 상태와 기록을 쉽게 확인할 수 있습니다.