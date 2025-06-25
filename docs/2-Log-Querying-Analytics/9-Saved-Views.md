검색 쿼리를 **저장된 뷰**(Saved Views)로 저장하면, 언제든지 쉽게 다시 불러올 수 있습니다:

1. 검색 필드를 초기화합니다.
    
2. Facets 패널에서 **Service** 아래의 `advertisements-service` 및 `discounts-service`를 선택하고, **Status** 아래에서 `Error`를 선택합니다..
    
3. 검색 필드 위의 **세 개의 점(⋮) 아이콘**을 클릭한 후, **'Save new view as...'** 를 선택합니다.
    
    **Views 패널**이 열리며, 저장된 뷰 목록이 표시됩니다. 여기에는 `My view` 외에도 PostgreSQL 통합에서 제공하는 **미리 정의된 뷰**가 포함될 수 있습니다:
    
    [![Save a new log search view](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/6ce9c25fd3ec61f894071ce47a462e41/assets/02-logs/save_new_view.png)](https://play.instruqt.com/assets/tracks/kccv27qqpk4s/6ce9c25fd3ec61f894071ce47a462e41/assets/02-logs/save_new_view.png)
    
4. **New view** 섹션에서 **Name** 필드에 다음을 입력합니다:
    
    copy
    
    ```
    Ads and Discounts Errors
    ```
    
    그런 다음 **Save(저장)** 버튼을 클릭합니다.
    
    새롭게 저장된 뷰가 목록에 나타납니다.
    
5. **My view** 를 클릭하면 검색 쿼리가 초기화되며 모든 로그를 다시 볼 수 있습니다.
    
    > Warning
    > 
    > 실수로 `Update your default view` 를 클릭하지 않도록 주의하세요!
    
6. 새로 생성한 **Ads and Discounts Errors** 뷰를 클릭하면, 이전에 저장한 대로 **검색 필드가 자동으로 채워지고 `advertisements-service` 및 `discounts-service`의 에러 로그만 표시**됩니다.
    
7. **Hide(숨기기)** 버튼을 클릭하여 Views 패널을 닫습니다.