# 키친포스

## 요구 사항

----

### 메뉴

- [X] 메뉴를 등록한다
    - [X] 메뉴의 가격은 0보다 크거나 같아야 한다.
    - [X] 메뉴는 메뉴그룹에 속해 있어야 한다.
    - [X] 하나 이상의 메뉴 상품이 있어야 한다.
    - [X] 요청한 메뉴 상품의 정보가 존재하지 않으면 안된다.
    - [X] 메뉴 상품의 갯수는 상품의 갯수와 같아야 한다.
    - [X] 요청 메뉴 상품의 갯수는 0개 이상이어야 한다.
    - [X] 메뉴의 가격이 요청한 메뉴상품들 총 가격보다 크면 안된다.
    - [X] 메뉴 이름이 반드시 있어야한다.
    - [X] 메뉴 이름에는 비속어가 포함될 수 없다.

- [X] 메뉴를 노출처리 할 수 있다.
    - [X] 메뉴의 가격이 각 메뉴상품의 갯수의 합보다 크면 노출이 되지 않는다.
- [X] 메뉴를 숨김처리 할 수 있다.

----

### 메뉴 그룹

- [X] 메뉴 그룹을 등록한다
    - [X] 메뉴 그룹 이름값을 필수로 갖는다.
- [X] 메뉴 그룹을 전체 조회할 수 있다.

----

### 상품

- [X] 상품을 등록한다.
    - [X] 상품 가격과 상품의 이름은 필수로 있어야 한다.
    - [X] 상품의 가격은 0보다 크거나 같아야 한다.
    - [X] 상품의 이름에는 비속어가 포함되면 안된다.

- [X] 상품 정보를 변경 한다.
    - [X] 변경하고자 하는 상품이 있어야한다.
    - [X] 상품 변경시 가격은 0보다 크거나 같아야한다.
    - [X] 메뉴 상품의 가격의 합이 메뉴의 가격보다 클 경우 메뉴의 판매를 중단(false)한다.

- [X] 상품의 전체 목록을 조회한다.

----

### 주문

- [X] 주문을 할 수 있다.
    - [X] 주문 방식은 `배달`, `포장`, `매장식사` 이 있으며 주문시 주문타입이 있어야 한다.
    - [X] 주문시 주문 메뉴는 반드시 있어야 한다.
    - [X] 주문시 주문 메뉴에 포함되는 메뉴들을 존재해야 한다.
    - [X] 조회된 메뉴의 갯수와 주문 메뉴에 포함된 메뉴의 갯수는 같아야 한다.
    - [X] 주문 방식이 `배달`, `포장` 인경우에는 주문한 메뉴의 갯수는 반드시 있어야한다.
    - [X] 주문 메뉴 목록에 해당하는 메뉴가 없다면 주문할 수 없다.
    - [X] 해당 메뉴가 미노출 상태라면 주문할 수 없다.
    - [X] 해당 메뉴의 가격과 주문 메뉴의 가격이 일치 하지 않으면 주문할 수 없다.
    - [X] 주문시 주문 상태는 `WAITING`이어야 한다.
    - [X] 주문 방식이 `배달`인 경우
        - [X] 배달하고자 하는 주소는 반드시 존재해야 한다.
    - [X] 주문 방식이 `매장 식사`인 경우
        - [X] 주문 테이블 ID를 기준으로 주문 테이블을 조회 가능.

    - [X] 주문 수락
      - [X] 주문 수락 시점에 주문 정보가 있어야 한다.
      - [X] 주문 수락시 OrderType 상태는 `WAITING` 이어야 한다.
      - [ ] 주문 타입이 `배달`인 경우
          - [X] 라이더에게 주문을 요청한다.
      - [ ] 정상적인 주문 상태라면 `WAITING` 에서 `ACCEPTED` 상태로 변경한다.

    - [ ] 주문이 도착하였을 경우
        - [ ] 주문 상태가 `ACCEPTED`인 경우에만 `SERVED` 로 변경한다.

    - [ ] 배달을 시작한다
        - [ ] 배달 시작시 주문 상태가 `DELIVERY`, `SERVED`여야만 `DELIVERING`상태로 변경할 수 있다.

    - [ ] 배달을 완료한다.
        - [ ] 주문 상태가 `DELIVERING` 경우 `DELIVERED`상태로 변경 가능하다.

    - [ ] 주문이 완료되었다.
        - 주문 방식이 `배달` 인 경우
            - [ ] 주문 상태가 `DELIVERED`인 경우에만 주문 상태를 `COMPLETED`로 변경할 수 있다.
        - 주문 방식이 `포장` 또는 `매장식사` 인 경우
            - [ ] 주문 상태가 `SERVED`인 경우에만 주문 상태를 `COMPLETED`로 변경할 수 있다.
        - 만약 주문 방식이 `매장식사` 인 경우
            - [ ] 주문에 해당하는 주문 테이블을 찾아서 해당 주문 테이블을 빈상태로 초기화한다.
    - [ ] 주문 정보롤 전체 조회 할 수 있다.

----

### 주문테이블

- [ ] 주문 테이블을 생성한다.
    - [ ] 주문 테이블의 이름은 필수로 있어야 한다.

- [ ] 주문 테이블의 착성 상태를 변경한다
    - [ ] 테이블의 상태를 착석 상태(false)로 변경한다
    - [ ] 테이블의 상태를 공석 상태(true)로 변경한다.
        - [ ] 주문 상태가 `COMPLETED`인 주문 테이블이 있다면 초기화 할 수 있다

- [ ] 주문 테이블이 공석아 아니라면 인원수의 변경이 가능하다.
    - [ ] 변경하고자 하는 테이블의 인원수는 0보다 크거나 같아야 한다.
    - [ ] 변경하고자 하는 테이블이 공석이면 변경할 수 없다.

- [ ] 주문 테이블을 전체 조회할 수 있다.

## 용어 사전

| 한글명 | 영문명 | 설명 |
| --- | --- | --- |
|  |  |  |

## 모델링
