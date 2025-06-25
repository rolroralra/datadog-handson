데이터독에서는, 수집된 모든 로그가 Process된 후 **Live Tail** 에서 실시간으로 표시됩니다. 이 로그는 인덱싱(또는 아카이빙) 되기 전의 모든 로그입니다. 이 기능을 통해 로그가 수집되자마자 즉시 확인할 수 있습니다! 하지만, 한 번 Live Tail에서 표시된 이전 로그를 나중에 다시 보려면, 해당 로그는 인덱싱이 되어 있어야만 합니다.

1. **시간 범위**를 `Live Tail`로 설정한 후, 로그 목록이 채워질 때까지 기다립니다.
    
    Live Tail 로그 목록에 표시되는 로그가 이전에 설정된 검색 쿼리와 일치하는 것도 참고하세요.
    
2. **검색 쿼리를 초기화**하고 새로운 로그가 수집될 때까지 기다립니다. Live Tail 목록에는 애플리케이션에서 수집된 **모든 로그**가 표시됩니다.
    
    Live Tail에서는 **검색 필드를 업데이트하여 쿼리를 변경**할 수 있습니다.:
    
    [![Saved views and custom facet in Live Tail](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/1ab5731829e504407e550c65b38276cd/assets/02-logs/saved_views_custom_facet_live_tail.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/1ab5731829e504407e550c65b38276cd/assets/02-logs/saved_views_custom_facet_live_tail.png)
    
3. 시간 범위를 `Past 15 minutes(지난 15분)`로 설정하고 **Log Explorer**(로그 탐색기)로 돌아갑니다.
    

로그 검색 및 필터링을 통해 원하는 로그만 확인하는 방법을 익혔으므로, 이제는 로그를 분석하기 위한 집계(Aggregation) 기능을 살펴보겠습니다.