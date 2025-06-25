# Datadog에서 트레이스 확인하기
컨테이너화된 애플리케이션에서 APM을 어떻게 설정하는지 살펴보았으니, 이제 생성된 트레이스를 Datadog에서 직접 확인해 보겠습니다.

1. [Datadog](https://app.datadoghq.com/)에 실습용 계정으로 로그인하세요. 기억이 나지 않거나, 필요할 때는 터미널에서 `creds` 명령어를 실행하면 Datadog 실습 계정 정보를 확인할 수 있습니다.
    
2. Log의 경우, Datadog 에서 활성화되지 않았다면 먼저 활성화해야 합니다.
    
    메인 메뉴에서, [Logs](https://app.datadoghq.com/logs)를 클릭합니다.
    
3. **Get Started** 버튼을 클릭하세요:
    
    [![Discover Datadog Log Management page](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/108095757d00aa8b34243605784dbe1e/assets/01-apm/enable-log-management.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/108095757d00aa8b34243605784dbe1e/assets/01-apm/enable-log-management.png)
    
4. 팝업 창에서 **Get Started** 버튼을 다시 클릭하세요:
    
    [![Start using Log Management popup modal](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/d50f2ad301685acc9043e8348e1d9cf3/assets/01-apm/log-management-modal.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/d50f2ad301685acc9043e8348e1d9cf3/assets/01-apm/log-management-modal.png)
    
5. 로그가 활성화되면 **Log Explorer**를 통해, 수집된 로그 이벤트를 확인할 수 있습니다:
    
    [![Log Explorer page with logs coming in](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/2a094fce93fb7c4366eb3deb94ac02d8/assets/01-apm/log-explorer-page.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/2a094fce93fb7c4366eb3deb94ac02d8/assets/01-apm/log-explorer-page.png)
    
    이제 서비스 카탈로그(Service Catalog)를 확인해 보겠습니다.
    
6. 왼쪽의 **메인 메뉴**에서 **APM**을 찾아 마우스를 올린 후, [Services](https://app.datadoghq.com/services)를 클릭합니다.
    
    > Important
    > 
    > 최근 2주 내에 다른 워크숍이나 Learning Center 과정을 수강했다면, 다른 환경이 실행 중일 수 있습니다. `env:dd101-sre` env가 올바르게 선택되었는지 확인하세요!:[![Service Catalog page with env:dd101-sre environment selected](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/7f476eb48b8d44d1f10b1125db23ae23/assets/01-apm/service-catalog-env.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/7f476eb48b8d44d1f10b1125db23ae23/assets/01-apm/service-catalog-env.png)
    
7. `docker-compose.yml` 파일에서 살펴본 `discounts-service` 및 Storedog의 다른 서비스들까지 확인할 수 있습니다. :
    
    [![Discounts and database in APM Service Catalog](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5b5b70b1a822482e2b7881b60fa7d0ea/assets/01-apm/discounts_apm_services.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5b5b70b1a822482e2b7881b60fa7d0ea/assets/01-apm/discounts_apm_services.png)
    
    만약 서비스가 보이지 않는다면, 브라우저를 새로고침하세요. (처음 APM을 설정하는 경우, 몇분 정도 소요될 수 있습니다.)
    
    또한, `docker-compose.yml`에서 APM 구성을 하지 않은 `active_record` 및 `database` 같은 서비스도 보일 수 있습니다. 이런 서비스들이 어떻게 Trace를 보냈을까요? **이 서비스들은 직접 트레이스를 전송하는 것은 아닙니다.** 하지만 APM이 활성화된 서비스에서 이들과 통신하는 과정이 캡처되므로, 이 캡처된 내역을 토대로 서비스 및 트레이스에 포함되어 표시됩니다.
    
8. 목록에서 **discounts-service** 위에 마우스를 올린 후, **Service Page** 버튼을 클릭합니다. 그러면 `discounts-service`의 세부 정보 페이지가 열립니다.
    
    왼쪽 상단에서 env가 `env:dd101-sre`로 설정되어 있는지 확인하세요. 또한 Operation이 `operation:flask.request`로 설정되어 있어야 합니다. :
    
    [![discounts-service page showing scope set to env:dd101-sre and operation:flask.request](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/d87530f3c33aaba6c06815fa3460aa06/assets/01-apm/apm-discounts-service.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/d87530f3c33aaba6c06815fa3460aa06/assets/01-apm/apm-discounts-service.png)
    
9. 좌측 탭 **Endpoints** 까지 스크롤하세요. 여기서 서비스 애플리케이션에서 트레이싱하고 있는 모든 엔드포인트를 확인할 수 있습니다. 이 서비스는 하나의 엔드포인트, `GET /discount` 가 존재합니다.
    
    [![Discounts service resources](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/3d45d58f5757ee1f0fd0420ad3fab260/assets/01-apm/discounts_apm_services_endpoints.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/3d45d58f5757ee1f0fd0420ad3fab260/assets/01-apm/discounts_apm_services_endpoints.png)
    
10. [APM > Traces](https://app.datadoghq.com/apm/traces)로 이동하세요. 검색 필드에 `env:dd101-sre`만 입력되어 있는지 확인합니다.
    
    여기에서 APM 구성을 통해 **최근 15분간 캡처된 트레이스의 실시간 스트림**을 볼 수 있습니다.
    
    [![Discounts APM traces](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/198fbd223fd4508a60c953154857c832/assets/01-apm/discounts_apm_traces.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/198fbd223fd4508a60c953154857c832/assets/01-apm/discounts_apm_traces.png)
    
11. `discounts-service`의 트레이스만 확인하기 위해, 왼쪽 패싯(Facets) 패널의 **Service** 섹션에서 `discounts-service`를 클릭하세요. 그러면 `service:discounts-service`로 태깅된 트레이스만 필터링됩니다.
    
12. 특정 `discounts-service` 트레이스를 클릭하면, 해당 트레이스의 세부 정보 패널이 열립니다. 여기서 **Flame Graph**를 확인할 수 있습니다. 이 그래프는 트레이스에서 각 서비스가 처리하는 데 걸린 시간을 Span을 통해 시각적으로 나타냅니다:
    
    [![Discounts APM trace flame graph](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/87d6fe003eaa4fb101cb8582866b774b/assets/01-apm/discounts_apm_traces_flamegraph.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/87d6fe003eaa4fb101cb8582866b774b/assets/01-apm/discounts_apm_traces_flamegraph.png)
    
    이 트레이스가 `discounts-service`의 `/discount` 엔드포인트를 캡처하고 있지만, 요청이 여기서 시작되지 않은 것을 주목하세요. **Flame Graph의 최상단**을 보면 `store-frontend` 서비스의 `Spree:HomeController#index` 엔드포인트가 루트 스팬(root span)으로 표시됩니다. 이는 Storedog의 홈페이지를 제공하는 엔드포인트입니다. `store-frontend`, `discounts-service` 서비스 모두 APM이 활성화되어 있기 때문에, Datadog은 **요청이 시작된 시점부터 종료될 때까지 전체 워크플로우를 하나의 트레이스로 조립하여 보여줄 수 있습니다.**