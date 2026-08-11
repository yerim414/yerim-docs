# sqlalchemy

[SQLAlchemy](https://www.sqlalchemy.org/)

**SQLAlchemy**는 Python에서 **데이터베이스와 상호작용하기 위한 ORM(Object-Relational Mapping)과 SQL Toolkit**을 제공하는 라이브러리

```python
pip install SQLAlchemy
```

1. **Core (SQL 표현 도구)**

- SQL 구문을 Python 코드로 작성할 수 있게 제공
- 쿼리문을 직접 작성하듯 명시적으로 다루고 싶을 때 사용
- **낮은 수준의 API**를 제공하며, 더 세밀한 제어가 가능

```python
from sqlalchemy import create_engine, text

engine = create_engine("sqlite:///test.db")
with engine.connect() as conn:
    result = conn.execute(text("SELECT * FROM users"))
```

1. ORM
- Python 클래스와 DB 테이블을 매핑
- 클래스를 통해 데이터베이스 레코드를 다룰 수 있다.
- 개발자 입장에서 더 직관적인 코드 작성 가능

```python
from sqlalchemy.orm import declarative_base

Base = declarative_base()

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True)
    name = Column(String)
```
