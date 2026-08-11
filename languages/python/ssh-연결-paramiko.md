# ssh 연결 paramiko

[Welcome to Paramiko! — Paramiko  documentation](https://www.paramiko.org/)

paramiko는 python으로 ssh 접속을 할 수 잇게 해주는 라이브러리이다.

```python
pip install paramiko
```

위 명령어로 설치한다.

기본 사용 방법

- `SSHClient` 객체 생성
- 호스트 키 자동 추가 설정
- `connect()`로 서버 접속
- `exec_command()`로 명령 실행
- 결과 받아오기
- 접속 종료

```python
import paramiko

# 1. SSHClient 객체 생성
ssh = paramiko.SSHClient()

# 2. 호스트 키 자동 추가 (처음 접속하는 서버일 경우)
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# 3. 서버 접속
ssh.connect(hostname='192.168.*.*', username='user', password='password', port=22)

# 4. 명령어 실행
stdin, stdout, stderr = ssh.exec_command('ls -al')

# 5. 결과 출력
print(stdout.read().decode())

# 6. 접속 종료
ssh.close()
```

2번의 경우는 서버 처음 접속할때 yes 그거..

파일 업로드 소스

```python
import paramiko

# 1. SSH 연결
ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect(hostname='192.168.*.*', username='user', password='password')

# 2. SFTP 세션 생성
sftp = ssh.open_sftp()

# 3. 파일 업로드
sftp.put('local_file.txt', '/home/user/remote_file.txt')

# 4. 파일 다운로드
sftp.get('/home/user/remote_file.txt', 'downloaded_file.txt')

# 5. 종료
sftp.close()
ssh.close()
```

참고로 접속하고자 하는 서버가 ssh를 허용하는지 확인하자. 보안때문에 22번 포트를안열어주는 경우도 있다.
