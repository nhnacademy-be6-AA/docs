# Buzz-book Server API 명세서

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)

## Auth Server

### 토큰 발급 
 
> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br>
> buzz-book.store:**8082/api/auth/token**
 
<details>
<summary>detail</summary>
 
#### Request
 
##### Body
 
| name    | type   | description            | required     |
| :-----: | :----: | :--------------------- | :---:        |
| loginId | string | 사용자가 로그인한 아이디 | **Required** |
| role    | string | 사용자 권한             | **Required** |
 
#### Response

##### Header
 
<details>
<summary>200 Ok : 성공적으로 로그인 된 경우</summary>
  
| key           | value             | description                                                        | 
| :-----------: | :---------------: | :----------------------------------------------------------------- |
| Authorization | jwt access token  | jwt access token `user_id`, `role`, `iat`, `exp`, `sub` 가 들어있음 |
| Refresh-Token | jwt refresh token | jwt refresh token                                                  |
 
`iat` 발급시간(number)

`exp` 만료시간(number)

`sub` 토큰타입(string, <sub>'access_token' or 'refresh_token'</sub>)

</details>

<br />
 
 
