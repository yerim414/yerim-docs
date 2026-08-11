# Crontab

크론탭은 리눅스와 유닉스 시스템에서 주기적으로 실행해야 하는 작업을 자동화하는 데 사용되는 시스템이다.

크론탭은 시간 기반 스케줄러로, 정해진 시간에 지정된 명령을 실행하도록 설정할 수 있다.

### crontab 명령어

```bash
crontab -e

# 사용자 개인의 크론탭을 편집 텍스트 편집기가 열리고 사용자의 크론탭 파일을 수정할 수 있다.
```

```bash
crontab -l

#  사용자의 크론탭 목록을 출력한다.
```

```bash
crontab -r

# 사용자의 크론탭을 제거 실행 시 사용자의 모든 크론탭 설정이 삭제된다.
```

### 크론탭 작성법

```bash
* * * * * command_to_execute
- - - - -
| | | | |
| | | | +----- Day of the week (0 - 7) (Sunday is 0 or 7)
| | | +------- Month (1 - 12)
| | +--------- Day of the month (1 - 31)
| +----------- Hour (0 - 23)
+------------- Minute (0 - 59)
```

크론탭은 각 위치의 별이 지칭하는 설정이 다르다

참고로 지금 * * * * *은 매분 실행하겠다는 의미이다!!

예시를 통해서 알아보자

```bash
0 2 * * * /home/user/backup.sh

# 매일 새벽 2시 백업 파일 실행
```

```bash
0 3 * * 1 /usr/sbin/logrotate /etc/logrotate.conf

# 매주 월요일 새벽 3시에 /etc/logrotate.conf 파일을 사용하여 로그 파일을 회전시키는 작업을 실행
```

```bash
0 0 * * 0 /bin/systemctl restart apache2.service

# 일요일 자정 아파치 재시작
```

```bash
0 9 14 4 * /usr/bin/echo "생일 축하합니다!" | /usr/bin/mail -s "Happy Birthday!" user@example.com

#  매년 4월 14일 오전 9시에 사용자에게 생일 축하 메시지를 이메일로 보냅니다.
```

[Crontab.guru - The cron schedule expression generator](https://crontab.guru/#0_0_*_*_*)

여기서 원하는 시간대를 적으면 자동으로 크론작업 시간을 만들어 준다!!
