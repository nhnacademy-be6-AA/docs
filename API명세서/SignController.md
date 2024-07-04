# Buzz-book Server Core API Account(User) 명세서

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)

## Core Api(User)
### 회원 관리 API

### 로그인 요청
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/account/login**

**설명**: 유저의 로그인 id를 이용해 login id와 encoded password를 준다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 요청 헤더는 JWT 인증을 필요로 하지 않습니다.

</details>

<details>
<SUMMARY>Body</SUMMARY>

| name     | type   | description        | 필수 |
|----------|--------|--------------------|----|
| loginId  | String | 유저의 로그인 ID       | 필수 |

</details>

</details>

**Response**

<details>
<summary>Body</summary>

| name     | type    | description | 필수 |
|----------|---------|-------------|----|
| password | String  | 비밀번호(인코딩)   | 필수 |
| loginId  | String  | 로그인 아이디     | 필수 |
| isAdmin  | boolean | 관리자 여부      |필수|

| 상태 코드 | 설명                                |
|-------|-----------------------------------|
| 200   | 로그인 ID와 인코딩된 비밀번호, 관리자 여부를 반환합니다. |
| 403   | 탈퇴한 유저의 로그인 요청입니다.                |

</details>

</details>

<br/>

---

### 회원가입 요청
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8090/api/account/register**

**설명**: 회원가입 처리용 POST 컨트롤러. 관리자는 따로 가입합니다.

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 요청 헤더는 JWT 인증을 필요로 하지 않습니다.

</details>

<details>
<SUMMARY>Body</SUMMARY>

| name                  | type   | description     | 필수 |
|-----------------------|--------|-----------------|----|
| loginId              | String | 로그인 아이디         | 예   |
| password                 | String | 유저 비밀번호         | 예   |
| name              | String | 유저 비밀번호(인코딩 필수) | 예   |
| contactNumber           | String | 유저 전화번호         | 예   |
|email|String| 이메일             |예|
|birthday|LocalDate| 생일              |예|

</details>

</details>

**Response**

<details>
<summary>Body(Void)</summary>

| 상태 코드 | 설명                                                       |
|-------|----------------------------------------------------------|
| 200   | 유저 회원가입이 성공적으로 처리되었습니다.                             |
| 400   | 잘못된 회원가입 요청입니다.                                           |

</details>

</details>

<br/>

---

### 로그인 성공 처리
> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/account/login**

**설명**: 로그인 성공 시 해당 회원 정보 리턴

<details>

**Request**
<details>
<details>
<SUMMARY>Header</SUMMARY>

**설명**: 요청 헤더는 JWT 인증을 필요로 하지 않습니다.

</details>

<details>
<SUMMARY>Body</SUMMARY>

| name     | type   | description        | 필수 |
|----------|--------|--------------------|----|
| loginId  | String | 유저의 로그인 ID       | 예   |

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

| 상태 코드 | 설명                              |
|-------|---------------------------------|
| 200   | 로그인에 성공한 유저 정보를 반환합니다.          |
| 400   | 잘못된 유저의 성공처리 요청                 |
| 500   | 서버 내부 오류로 인해 유저 정보를 반환할 수 없습니다. |

</details>

</details>

<br/>

---
