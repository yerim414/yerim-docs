# Put Patch 차이

Put과 Patch는 수정할 때 쓰이지만 수정방식이 다르다..

1. PUT - **Replace**
    
    Put은 전체를 교체 한다
    
    요청 하는 body값엔 모든 필드값을 가지고 있어야 한다.
    
    같은 요청을 여러 번 보내어도 결과가 동일하다(멱등성)
    
    참고로 누락된 필드, body값에 보내지 않은 필드는 null 로 덮어써질 수 있다.
    
    ```python
    {
    	"name" : "강아지",
    	"age" : 5,
    	"location" : "seoul"
    }
    
    # PUT의 body값
    {
    	"name" : "고양이",
    	"age" : 5
    }
    ```
    
    이런데이터가 있는데  바디값 에서 location field를 제외하고 보낸다 하면..
    
    ```python
    {
    	"name" : "고양이",
    	"age" : 5,
    	"location" : null
    }
    ```
    
    이처럼 location 값이 null이 될 수 잇따.
    
2. PATCH - **Update**
    
    일부 필드만을 수정한다.
    
    body엔 수정하고 싶은 필드만 보내면 된다.
    
    누락된 필드는 그대로 유지된다.
    
    ```python
    {
    	"name" : "강아지",
    	"age" : 5,
    	"location" : "seoul"
    }
    
    # PATCH의 body값
    {
    	"name" : "고양이",
    	"age" : 5
    }
    ```
    
    위 PUT에서 테스트 했던 예시데이터를 Patch로 보내게되면
    
    ```python
    {
    	"name" : "고양이",
    	"age" : 5,
    	"location" : "seoul"
    }
    ```
    
    Put에선 location이 null 이 되었지만 patch는 일부만 update하기 때문에 유지 된다.
