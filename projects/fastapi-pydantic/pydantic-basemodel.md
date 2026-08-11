# Pydantic - BaseModel

[Welcome to Pydantic - Pydantic](https://docs.pydantic.dev/latest/#why-use-pydantic)

Pydantic은 Python에서 가장 널리 사용되는 데이터 검증 라이브러리입니다.

## 주요기능

- **유효성 검사 (Validation)**: Pydantic은 모델을 정의할 때 **각 필드에 대한 유효성 검사**를 자동으로 수행합니다. 예를 들어, 문자열이 아닌 데이터가 들어오면 오류를 발생시킵니다.
- **데이터 직렬화 및 역직렬화**: Python 객체를 **JSON**, **dict**와 같은 다른 형식으로 변환하거나 그 반대의 작업을 쉽게 할 수 있습니다.
- **타입 힌트 지원**: Pydantic은 Python의 **타입 힌트**를 적극적으로 사용하여 코드의 가독성을 높이고, **정적 분석**을 용이하게 합니다.

1. 설치
    
    ```python
    pip install pydantic
    ```
    

1. Sample
    
    ```python
    from pydantic import BaseModel, EmailStr, ValidationError
    
    class User(BaseModel):
        name: str
        email: EmailStr
        age: Optional[int] = None
    
    try:
        user = User(name="Jane Doe", email="invalid-email")
    except ValidationError as e:
        print(e)
    ```
    
    pydantic은 유효성 검사 시 **자동으로 오류를 발생**시키므로 try-exception으로 처리 가능하다.
    
    위 소스는 email 값이 올바른 형식이 아니므로 validation error가 발생!!
    
    ```python
    from datetime import datetime
    
    from pydantic import BaseModel, PositiveInt
    
    class User(BaseModel):
        id: int  
        name: str = 'John Doe'  
        signup_ts: datetime | None  
        tastes: dict[str, PositiveInt]  
    
    external_data = {
        'id': 123,
        'signup_ts': '2019-06-01 12:22',  
        'tastes': {
            'wine': 9,
            b'cheese': 7,  
            'cabbage': '1',  
        },
    }
    
    user = User(**external_data)  
    
    print(user.id)  
    #> 123
    print(user.model_dump())  
    """
    {
        'id': 123,
        'name': 'John Doe',
        'signup_ts': datetime.datetime(2019, 6, 1, 12, 22),
        'tastes': {'wine': 9, 'cheese': 7, 'cabbage': 1},
    }
    """
    ```
