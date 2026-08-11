# paramiko - xterm

[xterm](https://ko.wikipedia.org/wiki/Xterm)

**xterm**은 리눅스 및 유닉스 환경에서 가장 일반적인 터미널 에뮬레이터 중 하나이다.

Paramiko에서 invoke_shell을 사용할때 `term=’xterm’` 의 의미는 서버에 알려주는 터미널 환경 타입이 “xterm” 이 된다.

서버 입장에서는 “xterm” 이라는 터미널을 사용하는 유저가 접속한 것처럼 인식한다.

다른 터미널 타입도 있다.

| 터미널 타입 | 설명 |
| --- | --- |
| `vt100` | 오래된 터미널. 일부 장비에서 기본값. |
| `xterm` | 대부분의 시스템에서 표준으로 잘 작동. 컬러, 제어 시퀀스 다양함. |
| `linux` | 리눅스 콘솔 전용 |
| `ansi` | ANSI 표준 기반의 간단한 제어 시퀀스만 지원 |

```python
channel = ssh_client.invoke_shell(term='vt100')
```
