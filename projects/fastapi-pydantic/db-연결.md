# DB 연결

```python
from sqlalchemy import create_engine
import urllib.parse

class DatabaseConnector:
    def __init__(self):
        self.engine = self._createEngine()

    def _createEngine(self):
        password = urllib.parse.quote("YOUR_PASSWORD")
        engine = create_engine(f"mysql+pymysql://root:{password}@localhost:3306/study", echo=True)
        return engine
    
    def get_engine(self):
        return self.engine
```
