# Buzz-book Server API 명세서

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)

## Auth Server

### 토큰 발급 
 
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8100/api/auth/token**
 
<details>
<summary>detail</summary>
 
#### Request
 
##### Body
 
| name    | type   | description            | 필수 |
| :-----  | :----  | :--------------------- | --- |
| loginId | string | 사용자가 로그인한 아이디     | 필수 |
| role    | string | 사용자 권한               | 필수 |
| userId  | long   | db pk                  | 필수 |
 
#### Response

##### Header
 
<details>
<summary>200 Ok : 성공적으로 로그인 된 경우</summary>
  
| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `iat`, `exp`, `sub` 가 들어있음           |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |

`user_id` UUIDv4(string)
 
`iat` 발급시간(number)

`exp` 만료시간(number)

`sub` 토큰타입(string, <sub>'access_token' or 'refresh_token'</sub>)

</details>
</details>

<br />

### 로그아웃

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8100/api/auth/logout**

<details>
<summary>detail</summary>

##### Request

###### Headers

| name           | type   | description                | 필수 |
| :------------- | :----  | :------------------------- | --- |
| Authorization  | string | jwt access token            | 필수 |
| Refresh-Token  | string | jwt refresh token           | 필수 |

##### Response

###### Headers

<details>
<summary>200 Ok : 성공적으로 로그아웃 된 경우</summary>
</details>

<details>
<summary>400 Bad Request : 토큰 정보가 없는 경우</summary>
</details>

<details>
<summary>401 Unauthorized : 유효하지 않은 토큰인 경우</summary>
</details>
</details>

### 사용자 정보 가져오기

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8100/api/auth/info**

<details>
<summary>detail</summary>

##### Request

###### Headers

| name           | type   | description                | 필수 |
| :------------- | :----  | :------------------------- | --- |
| Authorization  | string | jwt access token           | 선택 |
| Refresh-Token  | string | jwt refresh token          | 선택 |


##### Response

###### Headers

<details>
<summary>200 Ok : 성공적으로 사용자 정보를 조회한 경우</summary>

| key           | value             | description                                                        | 
| :-----------  | :---------------  | :----------------------------------------------------------------- |
| Authorization | jwt access token  | 갱신된 jwt access token                                              |
| Refresh-Token | jwt refresh token | 갱신된 jwt refresh token                                             |

###### Body

| name    | type   | description                         |
| :-----  | :----  | :---------------------------------- |
| userId  | string | 사용자 ID                            |
| loginId | string | 사용자가 로그인한 아이디               |
| role    | string | 사용자 권한                           |
| iat     | number | 토큰 발급시간                          |
| exp     | number | 토큰 만료시간                          |
| sub     | string | 토큰 타입 ('access_token' or 'refresh_token') |

</details>

<details>
<summary>401 Unauthorized : 유효하지 않은 토큰인 경우</summary>

###### Body

| name    | type   | description              |
| :-----  | :----  | :----------------------- |
| message | string | "다시 로그인해주세요."    |
| error   | string | 에러 메시지               |

</details>
 </details>
 
