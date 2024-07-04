## 결제 API

### 주문 하나에 딸린 결제 내역들 조회
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/bill-logs**

**설명**: 주문 하나에 딸린 결제 내역을 조회합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description               | 
| :-----------  | :---------------  | :-----------------------  |
| Authorization | jwt access token  | jwt access token 포함      |

**Body**

| name    | type   | description      | 필수 |
|---------|--------|------------------|------|
| orderId | Long   | 주문 ID           | 예   |

</details>

<details>
<summary>Response</summary>

| 상태 코드 | 설명                        |
|-----------|---------------------------|
| 200       | 결제 내역이 성공적으로 조회되었습니다. |
| 401       | jwt 토큰 인증에 실패했습니다.  |

</details>

---

### 관리자의 결제 내역 모두 조회
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/admin/bill-logs**

**설명**: 관리자의 결제 내역을 모두 조회합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description               | 
| :-----------  | :---------------  | :-----------------------  |
| Authorization | jwt access token  | jwt access token 포함      |

**Body**

| name    | type   | description      | 필수 |
|---------|--------|------------------|------|
| startDate | String | 조회 시작 날짜    | 예   |
| endDate   | String | 조회 끝 날짜      | 예   |

</details>

<details>
<summary>Response</summary>

| 상태 코드 | 설명                        |
|-----------|---------------------------|
| 200       | 결제 내역이 성공적으로 조회되었습니다. |
| 401       | jwt 토큰 인증에 실패했습니다.  |

</details>

---

### 결제 내역 추가
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/bill-log**

**설명**: 새로운 결제 내역을 추가합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description               | 
| :-----------  | :---------------  | :-----------------------  |
| Authorization | jwt access token  | jwt access token 포함      |

**Body**

| name    | type   | description      | 필수 |
|---------|--------|------------------|------|
| orderId | Long   | 주문 ID           | 예   |
| amount  | Double | 결제 금액          | 예   |
| method  | String | 결제 방법          | 예   |

</details>

<details>
<summary>Response</summary>

| 상태 코드 | 설명                        |
|-----------|---------------------------|
| 201       | 결제 내역이 성공적으로 추가되었습니다. |
| 400       | 잘못된 요청입니다.         |
| 401       | jwt 토큰 인증에 실패했습니다.  |

</details>
