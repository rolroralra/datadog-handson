Datadog의 **지속적 프로파일러(Continuous Profiler)** 는 강력한 APM 기능 중 하나입니다. 이 기능은 단순한 트레이스를 넘어 애플리케이션의 **시스템 리소스 소비**에 대한 인사이트를 제공합니다. CPU 시간, 메모리 할당, 파일 I/O, 가비지 컬렉션, 네트워크 처리량 등 다양한 정보를 확인할 수 있습니다.

이러한 메트릭은 다음과 같은 목적에 사용 가능합니다:

- **애플리케이션 개발자**: 코드 성능을 평가하고 최적화하는 데 도움을 줍니다.
- **SRE(Site Reliability Engineer)**: 인프라에 영향을 미치는 문제를 심층적으로 분석할 수 있습니다. 이런 추가 정보의 확보를 통해 **더 나은 의사 결정**이 가능해지며, 서로 다른 팀에 더 효율적으로 협업할 수 있습니다.

Continuous Profiler는 이 외에도 **비효율적인 코드로 인한 비용 증가를 방지**하고, **리소스 할당 최적화**에 대한 인사이트를 제공할 수도 있습니다.

Datadog 라이브러리는 **Go, Java, Node, Python, Ruby**에서 프로파일링을 지원합니다. 각 언어별 프로파일링 구성 방법은 [프로파일링 문서](https://docs.datadoghq.com/tracing/profiler/)에서 확인할 수 있습니다.

1. **[APM > Profiles](https://app.datadoghq.com/profiling/search)** 로 이동합니다.
    
    > Note
    > 
    > 혹시 **"Getting Started"** 페이지가 나타난다면, 페이지를 새로고침하세요.
    
    [![APM profile page with advertisements-service and discounts-service.](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c881e6ff95a8a7a0a5542c753e6f9d2f/assets/01-apm/apm-profile-page.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/c881e6ff95a8a7a0a5542c753e6f9d2f/assets/01-apm/apm-profile-page.png)
    
2. **오른쪽 상단**의 시간 범위 드롭다운에서 `Past 15 Minutes`(지난 15분)을 선택합니다.
    
3. 왼쪽 패싯(Facet) 패널의 **Service** 섹션에서 `discounts-service` 및 `advertisements-service`가 선택되어 있는지 확인합니다.
    
4. **Visualize as** 옵션을 **Timeseries**(시계열)로 설정합니다. **시계열 그래프**를 통해 특정 시간 동안의 리소스 사용량 변화를 시각적으로 확인할 수 있습니다.
    
5. **Show** 옆의 `Avg of`를 클릭하고 `Sum`으로 변경합니다.
    
6. **Sum of** 옆의 드랍박스를 클릭하고 **CPU - Cores**로 변경합니다.
    
    [![Continuous Profiler page with dropdown menu showing CPU - Cores highlighted](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/ccfcfc4cc1069ad65657990be6ac768e/assets/01-apm/profiler-cpu.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/ccfcfc4cc1069ad65657990be6ac768e/assets/01-apm/profiler-cpu.png)
    
7. 이제 **discounts-service** 및 **advertisements-service**에서 사용된 CPU 코어 합계를 확인할 수 있습니다.
    
    [![Timeseries for the sum of CPU cores by service](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/1841c40dd39b7cf87160cc08e758ee2d/assets/01-apm/apm_profile_search.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/1841c40dd39b7cf87160cc08e758ee2d/assets/01-apm/apm_profile_search.png)
    
8. **Visualize as**를 **Profile List**(프로파일 목록)으로 변경한 후 `advertisements-service`의 프로파일을 클릭합니다. (version 2.2.0) 그러면 **세부 정보 패널**이 열립니다:
    
    [![Profile detail](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/cb5a3f41fd858ed8df208e5b7657f0e8/assets/01-apm/profile_detail.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/cb5a3f41fd858ed8df208e5b7657f0e8/assets/01-apm/profile_detail.png)
    
9. **Flame Graph**의 스팬(Span) 위에 마우스를 올려 추가 정보를 확인합니다.
    
10. 우측의 **Group by** 드롭다운을 클릭하여 `Function`을 다른 옵션으로 변경하여 BreakDown을 달리하여 확인이 가능합니다. 이를 통해 **다양한 파일, 라이브러리, 함수의 Performance를 비교**할 수 있습니다.
    

Continuous Profiler에 대해 중요한 것은 아래와 같습니다.

- **활성화 방법**을 이해해야 합니다.
- **제공하는 정보**를 숙지하고 활용해야 합니다.
- **Datadog의 강력한 도구 중 하나**이므로, 개발팀이 이 기능을 활용할 수 있도록 공유하세요!

---
이번 실습에서 우리는 다음과 같은 내용을 배웠습니다:

- Storedog의 모든 서비스에서 **APM을 활성화하는 방법**
- 유동적으로 **트레이스와 로그 간 이동하는 방법**
- APM에서 **profiling 기능을 제공**하는 것을 확인했으며, 필요한 경우 관련 문서 확인을 통해 Application에 어떻게 Profiling을 설정하는지도 배웠습니다. 이를 통해 **개발자가 코드 성능을 최적화하고 리소스 사용을 줄이는 데 도움을 줄 수 있는 도구**임을 이해할 수 있었습니다.

다음 실습이 소개되면, 화면 오른쪽 아래의 **Next(다음)** 버튼을 클릭하여 실습을 이어가세요.