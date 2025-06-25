SLO는 애플리케이션 성능을 중심으로 명확한 목표를 지표로 활용할 수 있는 방법입니다. SLO를 통해 특정 메트릭 지표의 이력이 임계치 내로 목표 백분율 %를 얼마나 달성하였는지를 측정합니다. 이를 통해 서비스가 고객에 대해 얼만큼 성공적으로 제공되었는지 확인합니다.

SLO의 예시를 들자면, "특정 서비스는 7일 기간 내에 99%의 가동시간을 달성해야 한다." 등이 있겠습니다.

지금 생성한 discounts 서비스 요청시간 모니터를 이용하여, 이를 새로운 SLO(서비스 수준 목표)에 대한 서비스 수준 지표(SLI)로 사용할 수 있습니다.

discounts service의 SLO를 아래와 같이 직접 만들어 보겠습니다.:

1. [Service Mgmt > SLOs](https://app.datadoghq.com/slo/manage)로 이동합니다.
    
2. 우측 상단 **New SLO** 을 클릭합니다.
    
3. **Select how to measure your SLO**에서 `By Monitor Uptime`을 선택합니다.
    
4. **Select monitors** 드롭다운 메뉴에서, `Discounts 서비스 요청시간` 모니터를 선택합니다.
    
5. **Set your target & time window** 부분에서 기본값인 `7 days`와 `99.9`퍼센트를 그대로 유지합니다.
    
6. **Add name and tags** 부분에서 **Name**을 아래와 같이 입력합니다.:
    
    copy
    
    ```
    SLO: Discount 서비스 요청시간
    ```
    
    입력한 결과는 다음과 같습니다:
    
    [![New SLO page](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/d927074484ca230133b5ea1e1c4daaf0/assets/04-metrics-monitors/new_slo_page.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/d927074484ca230133b5ea1e1c4daaf0/assets/04-metrics-monitors/new_slo_page.png)
    
7. **Create & Set Alert**을 클릭합니다. 그러면 새 SLO 모니터를 만드는 페이지로 이동합니다.
    
8. **Select SLO** 부분에 이미 선택이 되어 있을 것입니다.
    
9. **Set alert conditions**에서 기본값을 유지합니다.
    
10. **Notify Your Team**에서 모니터 이름을 다음과 같이 지정합니다.:
    
    copy
    
    ```
    SLO: Discounts 서비스 요청시간
    ```
    
11. 다음 메시지를 메시지 텍스트 영역에 붙여넣으세요.:
    
    copy
    
    ```
    Discounts 요청시간 budget depleted(허용범위 초과)
    ```
    
12. 나머지 기본 설정은 그대로 유지합니다.
    
13. **Create**를 클릭하여 생성합니다. SLO 모니터 페이지가 표시될 것입니다.
    
14. SLO 모니터 페이지가 보일 것입니다. **SLO: Discount service request time**을 클릭하여 새 브라우저 창에서 SLO 사이드 패널을 엽니다.
    
    [![SLO Status and History tab in SLO details panel](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/75d842c2bb1fca82c6ebc694d71a4184/assets/04-metrics-monitors/slo_in_action.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/75d842c2bb1fca82c6ebc694d71a4184/assets/04-metrics-monitors/slo_in_action.png)
    

SLO가 개발업무의 우선순위를 정하는 데 어떻게 도움이 될 수 있는지 자세히 알아보려면 Datadog의 [SLO 공식문서](https://docs.datadoghq.com/monitors/service_level_objectives/)를 참조해보시면 좋겠습니다.

---
어떤 메트릭 지표를 사용할 수 있는지, 어떻게 그래프로 표현할 수 있는지, 그리고 그 그래프를 모니터와 대시보드로 어떻게 내보낼 수 있는지 알아보았습니다. Datadog 모니터를 사용하여 주요 지표에 대한 알림을 설정할 수 있었습니다. 대시보드를 사용하여 관련 데이터와 그래프를 한곳에 표시하여 쉽게 모니터링하고 공유할 수 있습니다.

강사의 안내에 따라, 우측 하단의 **Next** 버튼을 클릭하여 다음 랩을 진행하시기 바랍니다.