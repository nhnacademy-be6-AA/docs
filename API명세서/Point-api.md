# Buzz-book Point API 명세서

## 포인트 정책 API

### 쿠폰 발급

> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8091/api/coupons**

<details>
<summary>detail</summary>

#### Request

```json
{
  "couponPolicyId": 1
}
```

#### Response

```json
{
  "id": 0,
  "couponCode": "string",
  "createDate": "string",
  "expireDate": "string",
  "couponStatus": "used",
  "couponPolicyResponse": {
    "id": 0,
    "name": "string",
    "discountType": "string",
    "discountRate": 0,
    "discountAmount": 0,
    "standardPrice": 0,
    "maxDiscountAmount": 0,
    "period": 0,
    "startDate": "2024-07-04",
    "endDate": "2024-07-04",
    "isDeleted": true,
    "couponTypeResponse": {
      "id": 0,
      "name": "string"
    }
  }
}
```
</details>
<br />

![](https://img.shields.io/static/v1?label=&message=GET&color=blue)
![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen)
![](https://img.shields.io/static/v1?label=&message=PUT&color=orange)
![](https://img.shields.io/static/v1?label=&message=DELETE&color=red)