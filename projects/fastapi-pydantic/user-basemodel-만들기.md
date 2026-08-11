# User Basemodel 만들기

User Basemodel을 만들면서 자세히 알아보기

```python
from pydantic import BaseModel, EmailStr, Field
from typing import Optional
from datetime import datetime

class User(BaseModel):
    username: str = Field(..., min_length=3, max_length=20)
    id: str = Field(..., min_length=5, max_length=15)
    password: str = Field(..., min_length=6)
    email: EmailStr
    active: bool = Field(default=True, description="활성화 여부")
    created_at: datetime = Field(default_factory=datetime, description="계정 생성 시각")
```

**User class 데이터 설명**

- username : 문자열 필드. 최소 3에서 최대 20자 까지 가능하다
- id : 문자열 필드, 최소 3자에서 15자 까지
- password : 문자열 필드, 최소 6자 부터 입력 가능하다
- email : EmailStr 타입은 이메일 주소가 올바른 형식인지 검증 한다.
- active : bool 타입, 기본값이 True 이다.
- created_at : 날짜 필드, 기본값은 datetime이다.

알아둬야 할 것!
**1. Field(…) 의 의미**

`...`은 **해당 필드가 필수(required)** 임을 명시한다. 간단하게 작성할 땐 `Field(...)` 없이 타입만 써도 되긴한다.

```python
username: str # 이것도 필수란 의미
username: str = "kitty" # 그러나 기본값이 작성되어 있으면 optional 값이다.
```

그러나 min_length나 description을 적게 되면 Field를 적어줘야한다. 그리고 Field 를 이용하여 필수값인지를 명확하게 구분지어줘도 나쁠건 없다

1. `default`와 `default_factory` 의 차이
    
    ```python
    active: bool = Field(default=True, description="활성화 여부")
    created_at: datetime = Field(default_factory=datetime, description="계정 생성 시각")
    ```
    
    **`default`는 고정된 지정값을 이용할때 사용**
    
    **`default_factory`는 동적으로 기본값을 생성할 때 사용 한다.**
    
    실행 시점마다 달라질 수 있는 날짜는 `dafault_factory`로 작성한다. default로 작성 시엔 오류 발생!
