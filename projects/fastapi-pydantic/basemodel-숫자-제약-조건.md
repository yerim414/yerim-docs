# basemodel 숫자 제약 조건

[Fields - Pydantic](https://docs.pydantic.dev/latest/concepts/fields/#numeric-constraints)

```python
from pydantic import BaseModel, Field

class Foo(BaseModel):
    positive: int = Field(gt=0)
    non_negative: int = Field(ge=0)
    negative: int = Field(lt=0)
    non_positive: int = Field(le=0)
    even: int = Field(multiple_of=2)
    love_for_pydantic: float = Field(allow_inf_nan=True)
```

gt : gather then, 초과

lt : less then, 미만

ge : greater than or equal to, 이상

le : less than or equal to

multiple_of : 주어진 숫자의 배수, 위의 소스는 2의 배수만을 의미

allow_inf_nan : `'inf'`, `'-inf'`, `'nan'`  값 허용
