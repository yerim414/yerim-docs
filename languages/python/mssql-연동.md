# mssql 연동

이번에 python과 mssql을 연동해보게 되었다.  mysql, mongo는 많이 써보았지만 mssql은 처음이다!!

[https://python-tds.readthedocs.io/en/latest/#](https://python-tds.readthedocs.io/en/latest/#)

```bash
pip install python-tds
```

```bash
**import pytds**

# 데이터베이스 연결 설정
server = 'localhost'  # 호스트명/IP
port = 1433                 # MSSQL 포트 (기본값: 1433)
database = 'MS_TEST'       # 데이터베이스 이름
user = 'SA'                 # 사용자
password = 'YOUR_PASSWORD'      # 비밀번호

try:
    # pytds를 사용하여 MSSQL 연결
    with pytds.connect(server=server, database=database, user=user, password=password, port=port) as conn:
        print("Connected to MSSQL database!")
        
        # 커서를 생성하여 쿼리 실행
        with conn.cursor() as cursor:
            cursor.execute("SELECT * FROM DEPARTMENT")
            rows = cursor.fetchall()
            
            # 결과 출력
            for row in rows:
                print(row)
                
        
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    print("종료")
    
```
