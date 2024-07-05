# Buzz-book Coupon API 명세서

---

## 쿠폰 내역 API

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

### 쿠폰 조회

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8091/api/coupons/{couponId}**
<details>
<summary>details</summary>

#### Request

#### Response

```json
{
  "id": 0,
  "createDate": "2024-07-04",
  "expireDate": "2024-07-04",
  "status": "used",
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

### 쿠폰 수정

> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8091/api/coupons/{couponId}**

<details>
<summary>details</summary>

#### Request
```json
{
  "status": "used"
}
```

#### Response

```json
{
  "id": 0,
  "createDate": "2024-07-04",
  "expireDate": "2024-07-04",
  "status": "used",
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

### 회원 쿠폰 조회

> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8091/api/coupons/condition**

<details>
<summary>details</summary>

#### Request
```json
[
  {
    "couponCode": "string",
    "couponPolicyId": 1
  }
]
```

#### Response

```json
[
  {
    "id": 0,
    "createDate": "2024-07-04",
    "expireDate": "2024-07-04",
    "status": "used",
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
]
```
</details>
<br />

---

## 쿠폰 정책 API

### 쿠폰 정책 조건 조회

> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8091/api/coupons/policies/condition**

<details>
<summary>details</summary>

#### Request
```json
{
  "pageable": {
    "offset": 0,
    "sort": {
      "empty": true,
      "sorted": true,
      "unsorted": true
    },
    "paged": true,
    "pageNumber": 0,
    "pageSize": 0,
    "unpaged": true
  },
  "discountTypeName": "string",
  "isDeleted": "string",
  "couponTypeName": "string"
}
```

#### Response

```json
{
  "totalPages": 0,
  "totalElements": 0,
  "first": true,
  "last": true,
  "size": 0,
  "sort": {
    "empty": true,
    "sorted": true,
    "unsorted": true
  },
  "content": [
    {
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
  ],
  "number": 0,
  "pageable": {
    "offset": 0,
    "sort": {
      "empty": true,
      "sorted": true,
      "unsorted": true
    },
    "paged": true,
    "pageNumber": 0,
    "pageSize": 0,
    "unpaged": true
  },
  "numberOfElements": 0,
  "empty": true
}
```
</details>
<br />

### 쿠폰 정책 조회

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8091/api/coupons/policies**

<details>
<summary>details</summary>

#### Request

#### Response

```json
{
  "globalCouponPolicies": [
    {
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
  ],
  "specificCouponPolicies": [
    {
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
  ],
  "categoryCouponPolicies": [
    {
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
  ]
}
```
</details>
<br />

### 특정 도서 쿠폰 정책 조회

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8091/api/coupons/policies/specifics/{bookId}**

<details>
<summary>details</summary>

#### Request

#### Response

```json
[
  {
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
]
```
</details>
<br />

### 쿠폰 정책 생성

> ![](https://img.shields.io/static/v1?label=&message=POST&color=brightgreen) <br />
> buzz-book.store:**8091/api/coupons/policies**

<details>
<summary>details</summary>

#### Request

```json
{
  "name": "string",
  "discountType": "string",
  "discountRate": 0,
  "discountAmount": 20000,
  "standardPrice": 500000,
  "maxDiscountAmount": 0,
  "period": 0,
  "startDate": "string",
  "endDate": "string",
  "couponType": "string",
  "targetId": 0
}
```

#### Response

```json
{
  "id": 0,
  "name": "string"
}
```
</details>
<br />

### 쿠폰 정책 수정

> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8091/api/coupons/policies{couponPolicyId}**

<details>
<summary>details</summary>

#### Request

```json
{
  "endDate": "2024-07-04"
}
```

#### Response

```json
{
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
```
</details>
<br />

### 쿠폰 정책 수정

> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8091/api/coupons/policies{couponPolicyId}**

<details>
<summary>details</summary>

#### Request

#### Response

</details>
<br />