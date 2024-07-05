# Buzz-book Server Core API Account(User) 명세서

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)

## Core Api(User)
### 회원 주소 관리 API
### 주소 추가
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/account/address**

**설명**: 유저의 개인 주소 리스트를 추가합니다. user id를 넘겨야 합니다.

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

<details>
<SUMMARY>Body</SUMMARY>

| name                  | type    | description | 필수 |
|-----------------------|---------|-------------|----|
| address                | String  | 기본주소        | 예   |
| detail                  | String  | 상세주소        | 예   |
| alias                 | String  | 별칭          | 예   |
| zipCode               | Integer | 우편 번호       | 예   |
| nation               | String  | 나라 이름       | 예   |

</details>

</details>

**Response**

<details>
<summary>Body(Void)</summary>

| 상태 코드 | 설명                   |
|-------|----------------------|
| 200   | 주소가 성공적으로 추가되었습니다.   |
| 400   | 잘못된 유저의 주소 추가 요청입니다. |
| 401   | jwt 토큰인증에 실패했습니다.         |
| 406   | 주소갯수 한계에 달했습니다(10개)  |

</details>

</details>

<br/>

---

### 주소 삭제
> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/account/address/{addressId}**

**설명**: 유저의 개인 주소를 제거합니다. user id를 넘겨야 합니다.

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

<details>
<SUMMARY>Path Variable</SUMMARY>

| name      | type | description     | 필수 |
|-----------|------|-----------------|------|
| addressId | Long | 삭제할 주소의 ID | 예   |

</details>

</details>

**Response**

<details>
<summary>Body(Void)</summary>

| 상태 코드 | 설명                   |
|-------|----------------------|
| 200   | 주소가 성공적으로 삭제되었습니다.   |
| 400   | 잘못된 회원의 주소 삭제 요청입니다. |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---

### 주소 수정
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/account/address**

**설명**: 유저의 개인 주소를 수정합니다.

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

<details>
<SUMMARY>Body</SUMMARY>

| name    | type    | description | 필수 |
|---------|---------|-------------|----|
| id      | Long    | 주소 식별자      | 예   |
| address | String  | 기본주소        | 예   |
| detail  | String  | 상세주소        | 예   |
| alias   | String  | 별칭          | 예   |
| zipCode | Integer | 우편 번호       | 예   |
| nation  | String  | 나라 이름       | 예   |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| 상태 코드 | 설명                           |
|-------|------------------------------|
| 200   | 주소가 성공적으로 수정되었습니다.           |
| 400   | 잘못된 유저 혹은 주소id의 주소 수정 요청입니다. |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---

### 주소 리스트 조회
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/account/address**

**설명**: 유저 ID를 기반으로 유저의 개인 주소 리스트를 조회합니다.

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

| name    | type    | description | 필수 |
|---------|---------|-------------|----|
| id      | Long    | 주소 식별자      | 예   |
| address | String  | 기본주소        | 예   |
| detail  | String  | 상세주소        | 예   |
| alias   | String  | 별칭          | 예   |
| zipCode | Integer | 우편 번호       | 예   |
| nation  | String  | 나라 이름       | 예   |

| 상태 코드 | 설명                       |
|-------|--------------------------|
| 200   | 주소 리스트가 성공적으로 조회되었습니다.   |
| 400   | 잘못된 유저의 주소 리스트 조회 요청입니다. |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---
