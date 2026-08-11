# missing 1 required positional argument

```python
TypeError: BaseRepository.update() missing 1 required positional argument: 'update_date’
```

**Python 함수/메서드를 호출할 때 필요한 인자가 빠졌을 때** 발생하는 전형적인 예외

나의 경우 보아하니 `update_date` 라는 메소드가 static 메소드로 만든것인데 데코레이터를 적어주지 않아 발생했던 오류 ㅠㅠ

`@staticmethod` 데코레이터를 추가하여 수정하였다.
