# 퍼사드(Facade) 디자인 패턴

퍼사드(facade) 디자인 패턴은 복잡한 서비스시스템을 간단한 인터페이스로 감싸 사용자 또는 클라이언트가 보다 쉽게 사용할 수 있도록 도와주는 구조 패턴이다.

**복잡한 내부 구현을 숨기고 사용자에게 단순한 인터페이스만을 제공**

예시

PG 연동 작업시 카드결제, 결제 취소, 포인트 적립 등등.. 여러 api를 제공하는데 이를 사용하면 복잡해지고 어려워 질 것이다.

퍼사드 클래스를 만들어서 결재요청, 취소요청 만 할 수 있도록 생성한다.

```python
class PaymentAPI:
    def request_card_payment(self, card_info, amount):
        print(f"[카드 결제 요청] 카드정보: {card_info}, 금액: {amount}")
        return "결제완료"

    def cancel_card_payment(self, transaction_id):
        print(f"[카드 결제 취소 요청] 거래 ID: {transaction_id}")
        return "취소완료"

class PointAPI:
    def use_points(self, user_id, points):
        print(f"[포인트 사용] 사용자: {user_id}, 사용 포인트: {points}")
        return "포인트 차감 완료"

class LogAPI:
    def log_transaction(self, message):
        print(f"[로그 기록]: {message}")
```

위 소스는 PG에서 제공하는 api라고 가정한다!

```python
class PaymentFacade:
    def __init__(self):
        self.payment_api = PaymentAPI()
        self.point_api = PointAPI()
        self.log_api = LogAPI()

    def pay(self, user_id, card_info, amount, use_point=0):
        self.log_api.log_transaction("결제 시작")

        if use_point > 0:
            result = self.point_api.use_points(user_id, use_point)
            self.log_api.log_transaction(result)

        result = self.payment_api.request_card_payment(card_info, amount)
        self.log_api.log_transaction(result)

        return result

    def cancel(self, transaction_id):
        self.log_api.log_transaction("결제 취소 시작")
        result = self.payment_api.cancel_card_payment(transaction_id)
        self.log_api.log_transaction(result)
        return result
```

퍼사드 클래스를 통해 pay 메소드나 cancel 메소드만 호출하면 된다

사용자의 입장에선 PaymentFacade 클래스는 내부의 동작에 대해선 알 필요 없이 그냥 메소드 호출만 하면됨

코드의 재사용성이 증가할것이고 만약에 pg api가 바뀌게된다면.. 내부가 변경되는거니 외부엔 영향이 별로 크진 않을것같다.

그런데 어떤 서브시스템을 감싸고 노출시킬건지에 대한 설계랑 방식이 고려되어야할것같다.
