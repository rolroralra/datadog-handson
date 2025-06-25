서로다른 다양한 소스에서 대량의 로그를 정리하는 것은 매우 번거로울 수 있습니다. 모든 로그 라인이 적절하게 태깅되어 있거나, 지능적으로 파싱되거나, 검색 쿼리에서 쉽게 참조될 수 있도록 설정되어 있지는 않습니다. 다행히도, 로그들은 보통 특정한 **패턴**이 존재하며, Datadog은 이를 자동으로 감지하여 **유사한 로그 라인을 그룹화**할 수 있습니다.

패턴 집계를 사용하면, **구조가 유사한 메시지를 포함하며, 같은 서비스에 속하고, 동일한 상태(Status)를 가진 로그**가 함께 그룹화됩니다. 이 패턴 뷰를 활용하면 반복적으로 발생하는 오류 패턴을 감지하고 덜 중요한 로그를 필터링하여 중요한 문제를 놓치지 않도록 도와줍니다.

1. 검색 쿼리를 초기화합니다.
    
2. **Group into** 옵션에서 `Patterns`를 선택합니다.
    
    그러면 감지된 로그 패턴이 표시되며, 빈도수를 기준으로 정렬되어 표시됩니다. 여기에서는 로그 개수(Count), 그룹화 기준(이 예시의 경우 `Status`, `Service`), 그리고 로그 메시지를 확인할 수 있습니다.
    
    [![Discounts and ads services logs aggregated by pattern](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5abcdb48dda47b2776cdf408084df988/assets/02-logs/ads_discounts_pattern_aggregation.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/5abcdb48dda47b2776cdf408084df988/assets/02-logs/ads_discounts_pattern_aggregation.png)
    
3. `service` 기준으로 그룹화하는 대신, 사용자 지정 패싯 `process.name`으로 그룹화해 보겠습니다.
    
    `by` 옵션에서, `service`로 선택된 부분을 `process.name`으로 변경합니다.
    
    [![Group logs into patterns and show a count of all logs by process.name](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/28be183f5d88d149b8595674a32cc7be/assets/02-logs/patterns-process-name.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/28be183f5d88d149b8595674a32cc7be/assets/02-logs/patterns-process-name.png)
    
    이전에 생성한 사용자 지정 패싯을 기준으로 패턴이 그룹화된 모습을 확인할 수 있습니다.
    
4. `status` 그룹핑 설정만 적용해서 상태 값마다의 패턴 그룹도 확인가능합니다.
    
    [![Group logs into patterns by status](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/862d936ce8ab6d420f994239650c616f/assets/02-logs/patterns-status.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/862d936ce8ab6d420f994239650c616f/assets/02-logs/patterns-status.png)
    
5. 로그 목록의 열(Columns) 헤더는 정렬이 가능합니다. COUNT(로그 개수) 헤더를 클릭해서 **가장 적게 발생한 패턴부터 정렬**되는 것도 확인할 수 있습니다.
    
6. 특정 패턴을 클릭하면 **패턴 세부 정보 패널**이 열립니다. 이 패널에서는 해당 패턴과 함께 **로그 샘플 목록**이 표시됩니다.
    
7. 패턴 세부 정보 패널에서 로그 샘플 중 하나를 클릭하면 **로그 세부 정보 패널**이 열립니다. 여기서 해당 로그 이벤트에 대한 세부 정보를 확인할 수 있습니다.
    
    로그 세부 정보 패널을 닫고, 패턴 세부 정보 패널로 돌아갑니다.
    
8. 패턴 세부 정보 패널 최상단의 "Show Parsing Rule" 버튼을 클릭합니다. 이는 **Grok**이라는 정규 표현식 기반의 구문 분석 언어로, Datadog의 로그 파이프라인에서 사용되는 파서 중 하나입니다.
    
    [![Show parsing rule in pattern details side panel](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/8cb25853289c94e246f860be789f905f/assets/02-logs/show-parsing-rule.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/8cb25853289c94e246f860be789f905f/assets/02-logs/show-parsing-rule.png)
    
    파싱 규칙(Parsing Rules)을 활용하면, 반-구조화된 로그 라인을 JSON 로그와 같이 구조화된 태그 객체로 변환하는 커스텀 파이프라인을 생성할 수도 있습니다. 이는 Datadog이 JSON Log를 자동으로 파싱하는 방법과 같은 방법입니다.
    
    Datadog이 자동으로 설정한 파이프라인을 확인하려면 **[Logs > Pipelines](https://app.datadoghq.com/logs/pipelines)** 페이지를 참고하세요.
    
    커스텀 파이프라인 생성은 이번 실습 범위를 벗어나지만, 더 깊이 학습하고 싶다면 [Pipelines 문서](https://docs.datadoghq.com/logs/log_configuration/pipelines/?tab=source)를 참고할 수 있습니다!
---
이번 실습에서 우리는 다음과 같은 내용을 배웠습니다:

- 태그(Tags), 속성(Attributes), 텍스트 문자열을 사용하여 **로그를 검색하고 필터링하는 방법**
- **사용자 지정 패싯(Custom Facets)과 저장된 뷰(Saved Views) 활용 방법**
- 필드(Field) 및 패턴(Pattern) 기반으로 **로그를 집계하고 시각화하는 방법**

다음 실습이 소개되면, 화면 오른쪽 아래의 **Next(다음)** 버튼을 클릭하여 실습을 이어가세요.