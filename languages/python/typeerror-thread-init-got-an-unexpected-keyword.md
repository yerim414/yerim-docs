# TypeError: Thread.init() got an unexpected keyword argument 'Target'

파이썬 하다보면 잘 보이는 오류 중 하나이다. 올바르지 않은 키워드를 입력해서 그런것

나의 경우는 `Thread` 클래스의 생성자에 올바르지 않은 키워드 인자를 전달했을 때 발생한것이다.

`Thread` 클래스는 `target` 속성을 사용하여 스레드가 실행할 함수를 지정합니다. 하지만 난 `Target`라는 오타가있었다 ㅜㅜ

```python
async def getLog():
    while True:
        parserLog = colSysLog.find({"parserFlag": "N"}).sort([("_id", -1)]).limit(7000)
        if parserLog == None:
            parseFlag = False
        else:
            parseFlag = True
            for log in parserLog:
                #await logParsing(log)
                colSysLog.update_one({"_id":log["_id"]}, {"$set":{"parserFlag":"P"}})
                thread = threading.Thread(Target=run_thread, args=[log])
                thread.start()

loop = asyncio.get_event_loop()
loop.run_until_complete(getLog())
```

`threading.Thread(Target=run_thread, args=[log])`에서 `Target`를 `target`으로 수정해야 한다.
