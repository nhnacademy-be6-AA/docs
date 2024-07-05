# Buzz-book Server Core API Cart 명세서

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)

## Core Api
### 장바구니 조회(비회원/회원)
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/cart**

**설명**: 카트 ID로 장바구니 내용을 가져옵니다.(회원은 userId, 비회원은 uuid)

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 비회원 요청 시 헤더에 JWT 토큰을 포함하지 않으며, 회원 요청 시 JWT 토큰을 포함합니다.

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

</details>

<details>
<SUMMARY>Parameters</SUMMARY>

| name | type   | description      | 필수 |
|------|--------|------------------|------|
| uuid | String | 장바구니 UUID       | 예   |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| name                  | type    | description | 필수 |
|-----------------------|---------|-------------|----|
| productId                | int  | 상품 식별번호     | 예   |
| productName                  | String  | 상품이름        | 예   |
| quantity                 | int  | 수량          | 예   |
| price               | int | 가격          | 예   |
| thumbnailPath               | String  | 썸네일 경로      | 예   |
|canWrap|boolean| 포장여부        |예|

| 상태 코드 | 설명                        | 응답 타입                      |
|-------|---------------------------|----------------------------|
| 200   | 장바구니 내용이 성공적으로 조회되었습니다.   | `List<CartDetailResponse>` |
| 400   | 잘못된 uuid혹은 userId의 요청입니다. |                            |
| 401   | jwt 토큰인증에 실패했습니다. |                            |

</details>

</details>

<br/>

---

### 장바구니 내용물 생성
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/cart/detail**

**설명**: 장바구니 내용을 추가합니다. 상품과 상품 갯수가 필요합니다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 비회원 요청 시 헤더에 JWT 토큰을 포함하지 않으며, 회원 요청 시 JWT 토큰을 포함합니다.

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

</details>
<details>
<SUMMARY>Parameters</SUMMARY>

| name | type   | description      | 필수 |
|------|--------|------------------|------|
| uuid | String | 장바구니 UUID       | 예   |

</details>

<details>
<SUMMARY>Body</SUMMARY>

| name                  | type   | description        | 필수 |
|-----------------------|--------|--------------------|----|
| productId             | Long   | 상품 ID              | 예   |
| quantity              | Integer| 상품 수량             | 예   |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| 상태 코드 | 설명                                                       |
|-------|----------------------------------------------------------|
| 200   | 장바구니 내용이 성공적으로 추가되었습니다.                              |
| 400   | 잘못된 요청입니다.                                             |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---

### 장바구니 물건 제거
> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/cart/detail/{detailId}**

**설명**: 장바구니 내용을 제거합니다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 비회원 요청 시 헤더에 JWT 토큰을 포함하지 않으며, 회원 요청 시 JWT 토큰을 포함합니다.

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

</details>
<details>
<SUMMARY>Parameters</SUMMARY>

| name      | type | description     | 필수 |
|-----------|------|-----------------|------|
| uuid      | String | 장바구니 UUID      | 예   |
| detailId  | Long | 제거할 장바구니 내용 ID | 예   |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| name                  | type    | description | 필수 |
|-----------------------|---------|-------------|----|
| productId                | int  | 상품 식별번호     | 예   |
| productName                  | String  | 상품이름        | 예   |
| quantity                 | int  | 수량          | 예   |
| price               | int | 가격          | 예   |
| thumbnailPath               | String  | 썸네일 경로      | 예   |
|canWrap|boolean| 포장여부        |예|

| 상태 코드 | 설명                                | 응답 타입                      |
|-------|-----------------------------------|----------------------------|
| 200   | 장바구니 내용이 성공적으로 제거되었습니다.         | `List<CartDetailResponse>` |
| 400   | 잘못된 요청입니다.                        |                            |
| 401   | jwt 토큰인증에 실패했습니다.         |                            |

</details>

</details>

<br/>

---

### 장바구니 물건 모두 제거
> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/cart**

**설명**: 장바구니 내용을 모두 제거합니다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 비회원 요청 시 헤더에 JWT 토큰을 포함하지 않으며, 회원 요청 시 JWT 토큰을 포함합니다.

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

</details>
<details>
<SUMMARY>Parameters</SUMMARY>

| name | type   | description      | 필수 |
|------|--------|------------------|------|
| uuid | String | 장바구니 UUID       | 예   |

</details>

</details>

**Response**

<details>
<summary>Body(Void)</summary>

| 상태 코드 | 설명                                                       |
|-------|----------------------------------------------------------|
| 200   | 장바구니 내용이 성공적으로 모두 제거되었습니다.                        |
| 400   | 잘못된 요청입니다.                                             |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---

### 장바구니 내용 변경
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/cart/detail/{detailId}**

**설명**: 장바구니 내용을 변경합니다. Create와 유사합니다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 비회원 요청 시 헤더에 JWT 토큰을 포함하지 않으며, 회원 요청 시 JWT 토큰을 포함합니다.

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

</details>

<details>
<SUMMARY>Path Variable</SUMMARY>

| name      | type    | description     | 필수 |
|-----------|---------|-----------------|--|
| detailId  | Long    | 변경할 장바구니 내용 ID | 예 |

</details>

<details>
<SUMMARY>Parameters</SUMMARY>

| name      | type    | description     | 필수 |
|-----------|---------|-----------------|--|
| uuid      | String  | 장바구니 UUID      |  |
| quantity  | Integer | 새로운 상품 수량     | 예 |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| 상태 코드 | 설명                    |
|-------|-----------------------|
| 200   | 장바구니 내용이 성공적으로 변경되었습니다. |
| 400   | 잘못된 요청입니다.            |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---

### 회원 ID로 카트 UUID 조회
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/cart/uuid**

**설명**: (JWT) 회원 ID로 카트 UUID를 조회합니다. 회원만 가능하다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: JWT 토큰을 통해 인증인가와 유저를 확인합니다.

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| name      | type    | description   | 필수 |
|-----------|---------|---------------|--|
| uuid      | String  | 회원의 장바구니 UUID |  |

| 상태 코드 | 설명                                                       |
|-------|----------------------------------------------------------|
| 200   | 회원 ID로 카트 UUID가 성공적으로 조회되었습니다.                      |
| 400   | 잘못된 요청입니다.                                             |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---

### 비회원 장바구니 생성
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/cart/guest**

**설명**: 비회원 장바구니를 생성합니다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 요청 헤더는 필요하지 않습니다.

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| name      | type    | description   | 필수 |
|-----------|---------|---------------|--|
| uuid      | String  | 회원의 장바구니 UUID |  |

| 상태 코드 | 설명                                                       |
|-------|----------------------------------------------------------|
| 200   | 비회원 장바구니가 성공적으로 생성되었습니다.                           |
| 400   | 잘못된 요청입니다.                                             |

</details>

</details>

<br/>

---
