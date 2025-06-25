Datadog이 로그를 파싱하여 저장하므로, **공통 태그 및 속성**이 자동으로 **Facets 패널**에 나타납니다. 그 외에도, 로그 세부 정보 패널에서 특정 태그를 선택하여 **Custom Facet**으로 추가할 수도 있습니다.

[![Animation showing the process of creating a facet from a log attribute](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/fce5fbf425a9d165b50dbcc542069957/assets/02-logs/create-facet.gif)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/fce5fbf425a9d165b50dbcc542069957/assets/02-logs/create-facet.gif)

1. 로그 목록에서 하나의 로그를 클릭하여 로그 세부 정보 패널을 엽니다.
    
2. **Event Attributes(이벤트 속성)** 섹션에서 `process` 속성을 확인한 후, `name`을 클릭하고 **Create facet for @process.name**을 선택합니다.
    
    **Add facet(패싯 추가)** 창이 나타납니다.
    
3. **Add(추가)** 버튼을 클릭합니다.
    
    패싯이 성공적으로 추가되었다는 메시지가 표시되면, 로그 세부 정보 패널을 닫습니다.
    
4. 페이지 상단의 **검색 필드**를 초기화하고, 시간 범위를 `Past 15 Minutes`으로 설정합니다.
    
5. 왼쪽의 Facets 목록에서 하단으로 스크롤하여 내려갑니다. **OTHERS** 패싯 그룹에서 **process.name** 패싯을 확장합니다.
    
    새로운 패싯이 나타나려면 새로운 로그가 수집 및 처리될 때까지 잠시 기다려야 할 수 있습니다. 이후, 로그 항목에서 이 속성의 값이 표시됩니다:
    
    [![New process.name facet](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/03d38aa3490e2912af2c02ca05d6a708/assets/02-logs/process_name_facet.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/03d38aa3490e2912af2c02ca05d6a708/assets/02-logs/process_name_facet.png)
    
6. `bootstrap`을 선택하여, `process.name` 속성 값이 `bootstrap`인 로그만 필터링합니다.
    

사용 가능한 태그 및 속성은, 로그에 할당된 태그와 로그에서 추출된 속성에 따라 달라집니다. 이를 활용하여 검색 컨텍스트를 효과적으로 구성할 수 있습니다.