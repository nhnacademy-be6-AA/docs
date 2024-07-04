## 주문 API

### 주문 생성
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders**

**설명**: 새로운 주문을 생성합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value            | description              | 
| :------------ | :--------------- | :----------------------- |
| Authorization | jwt access token | jwt access token 포함     |

**Body**

| name           | type   | description         | 필수 |
| -------------- | ------ | ------------------- | ---- |
| userId         | int    | 사용자 식별번호       | 예   |
| bookId         | int    | 도서 식별번호         | 예   |
| quantity       | int    | 주문 수량            | 예   |
| deliveryPolicy | String | 배송 정책            | 예   |
| wrapping       | String | 포장 옵션            | 아니오|

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 201       | 주문이 성공적으로 생성되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 주문 조회
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/id**

**설명**: 주문을 조회합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                | 
| :------------ | :---------------- | :------------------------- |
| Authorization | jwt access token  | jwt access token 포함       |

**Body**

| name     | type   | description      | 필수 |
| -------- | ------ | ---------------- | ---- |
| orderId  | int    | 주문 식별번호       | 예   |

</details>

<details>
<summary>Response</summary>

| name           | type   | description         | 필수 |
| -------------- | ------ | ------------------- | ---- |
| orderId        | int    | 주문 식별번호         | 예   |
| userId         | int    | 사용자 식별번호       | 예   |
| bookId         | int    | 도서 식별번호         | 예   |
| quantity       | int    | 주문 수량            | 예   |
| deliveryPolicy | String | 배송 정책            | 예   |
| wrapping       | String | 포장 옵션            | 예   |
| status         | String | 주문 상태            | 예   |
| createdAt      | String | 주문 생성 날짜         | 예   |
| updatedAt      | String | 주문 수정 날짜         | 예   |

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 주문이 성공적으로 조회되었습니다. | `OrderResponse`          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 모든 주문 조회
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/orders/all**

**설명**: 모든 주문을 조회합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description              | 
| :------------ | :---------------- | :----------------------- |
| Authorization | jwt access token  | jwt access token 포함     |

</details>

<details>
<summary>Response</summary>

| name           | type   | description         | 필수 |
| -------------- | ------ | ------------------- | ---- |
| orderId        | int    | 주문 식별번호         | 예   |
| userId         | int    | 사용자 식별번호       | 예   |
| bookId         | int    | 도서 식별번호         | 예   |
| quantity       | int    | 주문 수량            | 예   |
| deliveryPolicy | String | 배송 정책            | 예   |
| wrapping       | String | 포장 옵션            | 예   |
| status         | String | 주문 상태            | 예   |
| createdAt      | String | 주문 생성 날짜         | 예   |
| updatedAt      | String | 주문 수정 날짜         | 예   |

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 모든 주문이 성공적으로 조회되었습니다. | `List<OrderResponse>`    |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 주문 수정
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/orders**

**설명**: 기존 주문을 수정합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                | 
| :------------ | :---------------- | :------------------------- |
| Authorization | jwt access token  | jwt access token 포함       |

**Body**

| name           | type   | description         | 필수 |
| -------------- | ------ | ------------------- | ---- |
| orderId        | int    | 주문 식별번호         | 예   |
| quantity       | int    | 주문 수량            | 예   |
| deliveryPolicy | String | 배송 정책            | 예   |
| wrapping       | String | 포장 옵션            | 아니오|

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 주문이 성공적으로 수정되었습니다. | `OrderResponse`          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 주문 취소
> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/orders**

**설명**: 기존 주문을 취소합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description              | 
| :------------ | :---------------- | :----------------------- |
| Authorization | jwt access token  | jwt access token 포함     |

**Body**

| name    | type   | description    | 필수 |
| ------- | ------ | -------------- | ---- |
| orderId | int    | 주문 식별번호     | 예   |

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 주문이 성공적으로 취소되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

## 운임비 정책 API

### 운임비 정책 조회
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/delivery-policy/id**

**설명**: 운임비 정책을 조회합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                  | 
| :------------ | :---------------- | :--------------------------- |
| Authorization | jwt access token  | jwt access token 포함         |

**Body**

| name      | type   | description        | 필수 |
| --------- | ------ | ------------------ | ---- |
| policyId  | int    | 운임비 정책 식별번호   | 예   |

</details>

<details>
<summary>Response</summary>

| name          | type   | description         | 필수 |
| ------------- | ------ | ------------------- | ---- |
| policyId      | int    | 운임비 정책 식별번호   | 예   |
| policyName    | String | 운임비 정책 이름       | 예   |
| policyDetail  | String | 운임비 정책 상세       | 예   |

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 운임비 정책이 성공적으로 조회되었습니다. | `DeliveryPolicyResponse` |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 운임비 정책 모두 조회
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/orders/delivery-policy/all**

**설명**: 모든 운임비 정책을 조회합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                  | 
| :------------ | :---------------- | :--------------------------- |
| Authorization | jwt access token  | jwt access token 포함         |

</details>

<details>
<summary>Response</summary>

| name          | type   | description         | 필수 |
| ------------- | ------ | ------------------- | ---- |
| policyId      | int    | 운임비 정책 식별번호   | 예   |
| policyName    | String | 운임비 정책 이름       | 예   |
| policyDetail  | String | 운임비 정책 상세       | 예   |

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 모든 운임비 정책이 성공적으로 조회되었습니다. | `List<DeliveryPolicyResponse>` |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 운임비 정책 생성
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/delivery-policy**

**설명**: 새로운 운임비 정책을 생성합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                  | 
| :------------ | :---------------- | :--------------------------- |
| Authorization | jwt access token  | jwt access token 포함         |

**Body**

| name          | type   | description         | 필수 |
| ------------- | ------ | ------------------- | ---- |
| policyName    | String | 운임비 정책 이름       | 예   |
| policyDetail  | String | 운임비 정책 상세       | 예   |

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 201       | 운임비 정책이 성공적으로 생성되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 운임비 정책 수정
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/orders/delivery-policy**

**설명**: 기존 운임비 정책을 수정합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                  | 
| :------------ | :---------------- | :--------------------------- |
| Authorization | jwt access token  | jwt access token 포함         |

**Body**

| name          | type   | description         | 필수 |
| ------------- | ------ | ------------------- | ---- |
| policyId      | int    | 운임비 정책 식별번호   | 예   |
| policyName    | String | 운임비 정책 이름       | 예   |
| policyDetail  | String | 운임비 정책 상세       | 예   |

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 운임비 정책이 성공적으로 수정되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 운임비 정책 삭제
> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/orders/delivery-policy**

**설명**: 기존 운임비 정책을 삭제합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                  | 
| :------------ | :---------------- | :--------------------------- |
| Authorization | jwt access token  | jwt access token 포함         |

**Body**

| name      | type   | description        | 필수 |
| --------- | ------ | ------------------ | ---- |
| policyId  | int    | 운임비 정책 식별번호   | 예   |

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 운임비 정책이 성공적으로 삭제되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

## 포장 API

### 포장 추가
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/orders/wrapping**

**설명**: 주문에 포장을 추가합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                | 
| :------------ | :---------------- | :------------------------- |
| Authorization | jwt access token  | jwt access token 포함       |

**Body**

| name        | type   | description       | 필수 |
| ----------- | ------ | ----------------- | ---- |
| orderId     | int    | 주문 식별번호       | 예   |
| wrappingId  | int    | 포장 식별번호       | 예   |

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 포장이 성공적으로 추가되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

---

### 포장 삭제
> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/orders/wrapping**

**설명**: 주문에서 포장을 삭제합니다.

<details>
<summary>Request</summary>

**Header**

| key           | value             | description                | 
| :------------ | :---------------- | :------------------------- |
| Authorization | jwt access token  | jwt access token 포함       |

**Body**

| name        | type   | description       | 필수 |
| ----------- | ------ | ----------------- | ---- |
| wrappingId  | int    | 포장 식별번호       | 예   |

</details>

<details>
<summary>Response</summary>

**상태 코드**

| 상태 코드 | 설명                          | 응답 타입                |
| --------- | ----------------------------- | ------------------------ |
| 200       | 포장이 성공적으로 삭제되었습니다. |                          |
| 400       | 잘못된 요청입니다.                |                          |
| 401       | jwt 토큰 인증에 실패했습니다.       |                          |

</details>

