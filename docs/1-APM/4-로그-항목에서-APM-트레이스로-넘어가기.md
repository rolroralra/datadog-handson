APM 트레이스에서 연관 로그로 이동하는 방법을 배웠으므로, 이번에는 **로그 항목에서 연관 APM 트레이스로 이동**하는 방법을 살펴보겠습니다:

1. **Log Explorer** 페이지로 돌아가서, 검색 필드를 지우고 시간 범위를 **Past 15 Minutes** 로 설정하여 최신 로그를 확인합니다.
    
2. 왼쪽 패싯(Facets) 패널의 **Service** 섹션에서 `discounts-service`를 클릭합니다. 그러면 `discounts-service`에서 생성된 로그만 표시됩니다.
    
3. `discounts-service` 로그 중 "Discounts available..." 메시지가 포함된 로그 항목을 클릭하여 로그 세부 정보 패널을 엽니다.
    
4. 로그 세부 정보 패널에서 **Trace** 탭을 클릭합니다.
    
    해당 로그에 연결된 APM 트레이스가 **로그 세부 정보 패널 내에서 바로 표시**됩니다!
    
    [![Traces in logs](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/e0bd4535d1059ebc4a4b977ae1a5e19b/assets/01-apm/discounts_apm_traces_in_logs.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/e0bd4535d1059ebc4a4b977ae1a5e19b/assets/01-apm/discounts_apm_traces_in_logs.png)
    
5. **View Trace in APM** 버튼을 클릭하면 APM 트레이스 세부 정보 패널에서 트레이스를 확인할 수 있습니다.
    

이를 통해 이제 APM 트레이스와 로그 간을 자유롭게 오갈 수 있습니다.