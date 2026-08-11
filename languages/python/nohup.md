# nohup

nohup은 프로그램을 백그라운드에서 실행하고, 사용자가 로그아웃하거나 터미널 세션이 종로된 후에도 프로그램이 계속 실행되도록 합니다.

python 스크립트를 실행할 때 nohup을 사용하면 터미널을 닫아도 스크립트가 중단되지 않고 계속 실행됩니다.

```bash
nohup python your_script.py &
```

& 명령은 백그라운드에서 실행하도록 하는것

```bash
ps -ef | grep python

ps aux | grep python
```

실행한 프로세스를 확인하려면 위의 명령어로 확인가능 확인한 프로세스의 PID를 이용해 해당 프로세스가 더이상 필요없으면 kill 하면 된다.

```bash
nohup python your_script.py > output.log 2>&1 &
```

이 명령은 `my_script.py`의 출력을 `my_output.log` 파일에 기록합니다.
