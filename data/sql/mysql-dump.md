# MYSQL Dump

MySQL 덤프(MYSQL Dump)는 데이터베이스의 구조와 데이터를 백업하거나 복구하기 위해 사용되는 명령어나 도구입니다. 덤프는 일반적으로 SQL 스크립트 형식으로 생성되며, 이를 사용하여 데이터베이스를 백업하고, 필요할 때 데이터를 복구할 수 있습니다.

### 사용법

```sql
mysqldump -u 사용자이름 -p 데이터베이스이름 > 백업파일명.sql
```

- **`u 사용자이름`**: MySQL 서버에 연결할 사용자 이름
- **`p`**: 사용자 비밀번호를 입력하도록 요청합니다. 비밀번호를 입력하려면 **`p`** 뒤에 공백 없이 입력하거나, **`p`**를 생략하고 **`p`** 옵션 없이 입력합니다.
- **`데이터베이스이름`**: 백업할 데이터베이스의 이름
- **`백업파일명.sql`**: 생성할 백업 파일의 이름 및 경로

```sql
mysqldump -u root -p my_database > my_database_backup.sql
```

**`root`** 사용자로 MySQL 서버에 접속하여 **`my_database`** 데이터베이스의 구조와 데이터를 백업한 후, **`my_database_backup.sql`** 파일에 저장합니다. 실행하면 비밀번호를 입력하도록 요청됩니다.

```sql
mysqldump -u root -p --all-databases > all_databases_backup.sql
```

**`root`** 사용자로 MySQL 서버에 접속하여 모든 데이터베이스의 구조와 데이터를 백업한 후, **`all_databases_backup.sql`** 파일에 저장합니다.
