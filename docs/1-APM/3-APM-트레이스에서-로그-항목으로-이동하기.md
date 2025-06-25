트레이스와 연관된 로그를 쉽게 확인해 보겠습니다.

1. 트레이스 세부 정보 패널 하단의 **Logs** 탭을 클릭합니다. 로그 표시 영역의 크기는 상단의 가로 구분선을 드래그하여 조정할 수 있습니다.
    
    > Note
    > 
    > "Get started with Log Management..."와 같은 메시지가 표시되면, 해당 링크를 클릭하여 로그 기능을 활성화하세요. 이후 **[APM > Traces](https://app.datadoghq.com/apm/traces?query=env%3Add101-sre%20service%3Adiscounts-service)** 페이지로 돌아가 `discounts-service` 트레이스를 다시 열고 **Logs** 탭을 클릭합니다.
    
    트레이스 실행 시간 동안 수집된 관련 로그가 표시됩니다:
    
    [![Discounts APM trace detail log tab](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/e595ff9fb5f90bb68cffb9772f7e593b/assets/01-apm/discounts_apm_traces_logs_tab.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/e595ff9fb5f90bb68cffb9772f7e593b/assets/01-apm/discounts_apm_traces_logs_tab.png)
    
2. 각 로그 항목 위에 마우스를 올려놓고, **Flame Graph**를 살펴보세요. 로그 항목이 생성된 정확한 지점을 나타내는 **수직선**을 확인할 수 있습니다. 이는 `DD_LOGS_INJECTION` 설정 옵션을 통해 활성화됩니다. `docker-compose.yml` 파일에서 옵션을 확인할 수도 있습니다.
    
3. **Logs** 테이블에서 **Hosts** 열의 맨 끝에 있는 **Open in Log Explorer** 아이콘을 클릭합니다. 아래 스크린샷을 확인하세요. :
    
    [![Open the traces logs in the explorer](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/ed18f5b133abdff92fb45c454585d6ae/assets/01-apm/discounts_trace_logs.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/ed18f5b133abdff92fb45c454585d6ae/assets/01-apm/discounts_trace_logs.png)
    
    그러면 새로운 탭에서 **Log Explorer** 페이지가 열리며, 해당 트레이스와 관련된 로그들이 `trace_id`를 기반으로 표시됩니다.
    
    [![Trace ID in log search field](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/14361de6bf4f5dfca3bf20c444b4691a/assets/01-apm/trace-id-in-log-search.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/14361de6bf4f5dfca3bf20c444b4691a/assets/01-apm/trace-id-in-log-search.png)
    
4. 검색 필드에 아래 필터를 추가하여 결과를 더욱 세분화할 수 있습니다:
    
    ```
    @filename:discounts.py
    ```
    
5. 로그 라인 중 하나를 클릭하면 상세 패널이 옆에 표시됩니다.
    
    [![Discounts trace to log line](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/4e8f4743ed4003ce6926dbedfc1db71e/assets/01-apm/discounts_trace_to_logline.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/4e8f4743ed4003ce6926dbedfc1db71e/assets/01-apm/discounts_trace_to_logline.png)
    
    `ddtrace` 라이브러리가 환경변수 `DD_LOGS_INJECTION=true`를 확인하면, 각 로그마다 트레이스 정보를 주입할 수 있도록 준비됩니다. [Datadog Python APM Client documentation](https://ddtrace.readthedocs.io/en/stable/index.html) 문서에서 파이썬 `ddtrace`에 대한 자세한 사항을 확인할 수 있습니다!
    
6. 패널을 다 확인하셨으면 닫아도 됩니다.