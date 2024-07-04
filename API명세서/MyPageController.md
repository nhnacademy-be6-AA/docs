
# Buzz-book Server Core API Account(User) 명세서

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)

## Core Api(User)

### 마이페이지 컨트롤러 API 명세서
#### 기본 URL: `/api/account/mypage`

### 비밀번호 변경
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/account/mypage/password**

**설명**: 사용자의 비밀번호를 변경합니다. 새 비밀번호는 인코딩된 비밀번호만 받습니다.

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

| name                  | type   | description        | 필수 |
|-----------------------|--------|--------------------|----|
| oldPassword           | String | 이전 비밀번호            | 필수 |
|      newPassword| String | 새로운 비밀번호(인코딩 필수)   | 필수 |
|             confirmPassword          | String | 새로운 비밀번호의 확인(인코딩X) | 필수 |

</details>

</details>

**Response**

<details>
<summary>Body(VOID)</summary>


| 상태 코드 | 설명                                                       |
|-------|----------------------------------------------------------|
| 200   | 비밀번호가 성공적으로 변경되었습니다                                      |
| 400   | 새로운 비밀번호와 비밀번호 확인이 다르거나 잘못된 유저의 요청이거나 입력한 이전 비밀번호가 다릅니다. |
| 401   | jwt 토큰 인증에 실패했습니다.   |
---

</details>

</details>

<br/>

---

### 유저 정보 변경
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/account/mypage**

**설명**: 비밀번호를 제외한, 유저정보(이름, 연락처, 이메일)를 변경합니다.

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

| name          | type   | description | 필수 |
|---------------|--------|-------------|----|
| name          | String | 이름          | 필수 |
| contactNumber | String | 연락처(숫자만)    | 필수 |
| email         | String | 이메일         | 필수 |

</details>

</details>

**Response**

<details>
<summary>Body(VOID)</summary>

| 상태 코드 | 설명                   |
|-------|----------------------|
| 200   | 비밀번호가 성공적으로 변경되었습니다. |
| 400   | 잘못된 유저의 요청입니다.       |
| 401   | jwt 토큰 인증에 실패했습니다.   |
---

</details>

</details>

<br/>

---

### 유저 탈퇴
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/account/mypage/deactivate**

**설명**: 유저 계정을 탈퇴 처리합니다.

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

| name     | type   | description | 필수 |
|----------|--------|-------------|----|
| password | String | 비밀번호(인코딩X)  | 필수 |
| reason   | String | 탈퇴 이유       | 필수 |

</details>

</details>

**Response**

<details>
<summary>Body(VOID)</summary>

| 상태 코드 | 설명                        |
|-------|---------------------------|
| 200   | 유저가 성공적으로 탈퇴 처리되었습니다      |
| 400   | 잘못된 유저 요청 또는 패스워드가 틀렸습니다. |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>
---
### 유저 정보 조회
> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/account/mypage**

**설명**: 유저 ID를 기반으로 유저 정보를 조회합니다.

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

| name     | type        | description | 필수 |
|----------|-------------|-------------|----|
| id | Long        | 유저 식별 번호    | 필수 |
| loginId   | String      | 로그인 아이디     | 필수 |
|contactNumber| String      | 연락처         |필수|
|name| String      | 이름          |필수|
|email| String      | 이메일         |필수|
|birthday| LocalDate   | 생일          |필수|
|grade| Grade(Enum) | 등급          |필수|
|isAdmin| boolean     | 관리자 여부      |필수|

| 상태 코드 | 설명                   |
|-------|----------------------|
| 200   | 유저 정보가 성공적으로 조회되었습니다 |
| 400   | 잘못된 유저의 요청입니다.       |
| 401   | jwt 토큰인증에 실패했습니다.         |

</details>

</details>

<br/>

---






 
 
