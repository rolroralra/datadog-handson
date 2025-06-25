**필드(Field) 집계**를 사용하면 검색 필터에 해당하는 모든 로그를 특정 **로그 패싯(Facet)의 값**을 기준으로 그룹화 할 수 있습니다. 이러한 그룹에서, 다음을 수행할 수 있습니다.

- 각 그룹의 **로그 개수 집계**
- 각 그룹에서 특정 패싯 값의 **고유 개수 집계**
- 각 그룹에서 특정 패싯의 **숫자 값에 대한 통계 연산 수행**

이러한 로그 집계를 통해 트렌드를 보다 명확하게 파악하고, 다양한 로그 패싯 간의 관계를 시각화하는 데 도움을 받을 수 있습니다.

1. **Log Explorer(로그 탐색기)** 페이지에서 **Views 패널**을 열고 이전에 저장한 **Ads and Discounts Errors** 뷰를 선택합니다.
    
2. 검색 필드 아래에 있는 **Group into** 행에서 `Fields`를 선택합니다.
    
    필터링된 로그 목록이 **Graph Visualization**(그래프 시각화)로 변경됩니다.
    
3. `Count Of`는 `all logs`로 설정하여 개수를 표시하고, `by`는 `service`를 선택하여 서비스 기준으로 그룹화합니다:
    
    [![Field aggregation of discounts and ads services](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/32e6334b3e19ffd608f30d36ee75a468/assets/02-logs/field_aggregate_ads_discounts.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/32e6334b3e19ffd608f30d36ee75a468/assets/02-logs/field_aggregate_ads_discounts.png)
    
    두 서비스의 에러 로그를 막대 그래프 형태로 시각화할 수 있게 되었습니다!
    
4. 그래프 위의 **Visualize as** 옵션이 기본적으로 `Timeseries(시계열)`로 설정되어 있습니다. 이제 다른 시각화 옵션을 선택하여 어떻게 표시되는지 확인해 보세요.
    
    예를 들어 **Top List**를 선택하면, 아래와 같은 형태로 표시됩니다:
    
    [![Click graph to view aggregated logs](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5c38246e4f653928845302fb0d325faa/assets/02-logs/view_logs_comprising_aggregate.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5c38246e4f653928845302fb0d325faa/assets/02-logs/view_logs_comprising_aggregate.png)
    
5. 시각화는 인터랙티브한 기능을 제공합니다. 각 행이나 그래프 하나하나를 클릭하여 해당 그룹 관련 집계 로그 목록이 사이드 패널에 표시할 수 있습니다:
    
    [![Aggregated logs detail panel](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/71d67ccd51c55223049ec88d031c8fb4/assets/02-logs/aggregated_logs_detail_side_panel.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/71d67ccd51c55223049ec88d031c8fb4/assets/02-logs/aggregated_logs_detail_side_panel.png)
    

## Exporting graphs (그래프 내보내기)

Datadog에서는 생성한 로그 시각화를 다른 기능으로 내보내서(Export) 연동/활용할 수 있습니다. 예를 들어, **모니터(Monitors), 대시보드(Dashboards), 노트북(Notebooks)에** 내보낼 수 있으며, 로그에서 Custom Metrics을 생성하거나, 집계된 데이터를 CSV 파일로 다운로드할 수도 있습니다.

1. **Visualize as**에서 `Timeseries`를 선택합니다.
    
2. 그래프 위의 **Save to Dashboard(대시보드에 저장)** 버튼을 클릭합니다.
    
3. 팝업된 Export 대화 상자에서, **New Dashboard**를 클릭합니다.
    
    [![Export logs to dashboard](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/e0610513921c13e033deece23c001b71/assets/02-logs/export_logs_to_dash.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/e0610513921c13e033deece23c001b71/assets/02-logs/export_logs_to_dash.png)
    
    `Save and Open` 버튼을 클릭하면 새롭게 생성된 대시보드로 이동하게 되며, 로그 시각화가 대시보드 위젯으로 표시됩니다. 나중에 이 대시보드를 활용할 수 있습니다.
    
4. 이제 **Visualize as**에서 `List`를 선택하여 기본 로그 목록 보기로 돌아갑니다.