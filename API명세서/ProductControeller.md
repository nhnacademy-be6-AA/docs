## 상품 API

### DTO 구조
<details>
<summary>
Product.StockStatus
</summary>

|name|type|description|
| --- | ---- | --- |
|SALE | String | 판매중 |
SOLD_OUT | String | 매진 (재입고 불확실) |
OUT_OF_STOCK | String | 재고 없음 |
</details>


<details>
<summary>
ProductRequest
</summary>

| name         | type       | description               | required |
| ------------ | ---------- | ------------------------- | ---- |
| stock        | int        | 재고량                    | 예   |
| productName  | String     | 상품명                    | 예   |
| description  | String     | 상품 설명                 | 아니오 |
| price        | int        | 가격                      | 예   |
| forwardDate  | String     | 날짜 (형식: YYYY-MM-DD)   | 아니오 |
| thumbnailPath| String     | 썸네일 이미지 경로        | 아니오 |
| stockStatus  | StockStatus(String)| 재고 상태                 | 예   |
| categoryId   | int        | 카테고리 ID               | 예   |
</details>

<details>
<summary>
ProductUpdateRequest
</summary>

| name          | type                  | description     | required |
| ------------- | --------------------- | -------------- | ---- |
| stock         | int                   | 재고량           | 예   |
| productName   | String                | 상품명           | 예   |
| description   | String                | 설명             | 아니오 |
| price         | int                   | 가격             | 예   |
| thumbnailPath | String                | 썸네일 이미지 경로  | 아니오 |
| stockStatus   | Product.StockStatus   | 재고 상태           | 예   |
| categoryId    | int                   | 카테고리 ID         | 예   |
</details>

<details>
<summary>
ProductResponse
</summary>

| name         | type                | description             | required |
| ------------ | ------------------- | ----------------------- | ---- |
| id           | int                 | 상품 ID                 | 예   |
| stock        | int                 | 재고량                  | 예   |
| productName  | String              | 상품명                  | 예   |
| description  | String              | 설명                    | 아니오 |
| price        | int                 | 가격                    | 예   |
| forwardDate  | LocalDate           | 날짜 (형식: YYYY-MM-DD) | 아니오 |
| score        | int                 | 점수                    | 아니오 |
| thumbnailPath| String              | 썸네일 이미지 경로      | 아니오 |
| stockStatus  | Product.StockStatus | 재고 상태               | 예   |
| category     | CategoryResponse    | 카테고리 정보           | 예   |
| tags         | List\<TagResponse\>   | 태그 리스트             | 아니오 |
</details>

<details>
<summary>
CategoryResponse
</summary>

| name            | type              | description     | 필수 |
| --------------- | ----------------- | --------------- | ---- |
| id              | int               | 카테고리 ID     | 예   |
| name            | String            | 카테고리 이름   | 예   |
| parentCategory  | CategoryResponse  | 상위 카테고리   | 아니오 |
</details>

<details>
<summary>
TagResponse
</summary>

| name            | type              | description     | 필수 |
| --------------- | ----------------- | --------------- | ---- |
| id              | int               | 태그 ID     | 예   |
| name            | String            | 태그 이름   | 예   |
</details>

<details>
<summary>
BookRequest
</summary>

| name         | type    | description                       | 필수 |
| ------------ | ------- | --------------------------------- | ---- |
| title        | String  | 제목                              | 예   |
| description  | String  | 설명                              | 아니오 |
| isbn         | String  | ISBN 값                           | 예   |
| publisher    | String  | 출판사                            | 예   |
| publishDate  | String  | 날짜 (형식: YYYY-MM-DD)           | 아니오 |
| productId    | Integer | 상품 ID                           | 예   |
</details>

<details>
<summary>
BookResponse
</summary>

| name         | type            | description        | required |
| ------------ | --------------- | ------------------ | -------- |
| id           | long            | ID                 | 예       |
| title        | String          | 제목               | 예       |
| authors      | List\<String\>    | 저자 목록          | 예       |
| description  | String          | 설명               | 아니오   |
| isbn         | String          | ISBN 값            | 예       |
| publisher    | String          | 출판사             | 예       |
| publishDate  | LocalDate       | 출판 날짜          | 예       |
| product      | ProductResponse | 상품 정보          | 아니오   |

</details>

<details>
<summary>
ProductBookResponse
</summary>

| name    | type            | description  | required |
| ------- | --------------- | ------------ | -------- |
| product | ProductResponse | 상품 정보    | 예       |
| book    | BookResponse    | 책 정보      | 아니오   |

</details>




---

### 응답 상태 코드
<details>
<summary>http 상태 코드</summary>

| 상태 코드 | 설명                 | 응답 타입          |
| --------- | ------------------------- | ------------------- |
| 200       | 요청 성공 |         ProductResponse        |
|        |  |         CategoryResponse        |
|        |  |         TagResponse        |
|        |  |         BookResponse        |
|        |  |         ProductBookResponse        |
| 400       | 잘못된 데이터 타입으로 요청  |              |
| 404       | 없는 상품 요청  | String  |  |
| 409       | 이미 존재하는 id로 등록 요청  | String |

</details>

---




### 상품 추가 :

> ![](https://img.shields.io/static/v1?label=&message=POST&color=green) <br />
> buzz-book.store:**8090/api/products**

| Transaction | Specification | name      | type           | description                        | required |
|-------------|----------------|-----------|----------------|------------------------------------|----------|
| Request     | body           | productReq| ProductRequest | 추가할 상품의 정보 | yes      |
| Response    | body           | ProductResponse |          | 추가된 상품의 정보   |          |





### 조건으로 상품 목록 조회 :

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/products**

| Transaction | Specification | name     | type                | description                    | required |
|-------------|----------------|----------|---------------------|--------------------------------|----------|
| Request     | parameter      | status   | Product.StockStatus | 상품 상태                      | no       |
|             | parameter      | name     | String              | 상품 이름                      | no       |
|             | parameter      | pageNo   | Integer             | 페이지 번호 (기본값: 0)        | no       |
|             | parameter      | pageSize | Integer             | 한 페이지에 보여질 아이템 수 (기본값: 10) | no       |
| Response    | body           |          | Page\<ProductResponse\> | 조회된 상품 목록              |          |



### 상품 조회 :

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/products/{id}**

| Transaction | Specification | name | type | description            | required |
|-------------|----------------|------|------|------------------------|----------|
| Request     | path variable  | id   | int  | 주어진 id(int)         | yes      |
| Response    | body           |      | ProductResponse | 상품 정보 |          |


### 상품 수정 :

> ![](https://img.shields.io/static/v1?label=&message=PUT&color=orange) <br />
> buzz-book.store:**8090/api/products/{id}**

| Transaction | Specification | name        | type                | description                    | required |
|-------------|----------------|-------------|---------------------|--------------------------------|----------|
| Request     | path variable  | id          | int                 | 주어진 id(int)                 | yes      |
|             | body           | productReq  | ProductUpdateRequest| 업데이트할 상품 정보(ProductUpdateRequest) | yes      |
| Response    | body           |             | ProductResponse     | 업데이트된 상품 정보           |          |


### 상품 삭제 :

데이터가 물리적으로 삭제되지는 않음.
(product.product_status=SOLD_OUT, product.stock=0)

> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/products/{id}**

| Transaction | Specification | name | type | description            | required |
|-------------|----------------|------|------|------------------------|----------|
| Request     | path variable  | id   | int  | 주어진 id(int)         | yes      |
| Response    | body           |      |      |                        |          |


---

### 도서 조회 :

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/books/{id}**

| Transaction | Specification | name | type | description            | required |
|-------------|----------------|------|------|------------------------|----------|
| Request     | path variable  | id   | long | 주어진 id(long)        | yes      |
| Response    | body           |      | BookResponse | 도서 정보 |          |


### 도서 추가 :

> ![](https://img.shields.io/static/v1?label=&message=POST&color=green) <br />
> buzz-book.store:**8090/api/books**

| Transaction | Specification | name      | type        | description                        | required |
|-------------|----------------|-----------|-------------|------------------------------------|----------|
| Request     | body           | bookReq   | BookRequest | 추가할 도서의 정보(BookRequest)    | yes      |
| Response    | body           |           | BookResponse| 추가된 도서의 정보                 |          |


### 도서 삭제 :

데이터가 물리적으로 삭제되지는 않음.
(product.product_status=SOLD_OUT, product.stock=0, book.product_id=null)

> ![](https://img.shields.io/static/v1?label=&message=DELETE&color=red) <br />
> buzz-book.store:**8090/api/books/{id}**

| Transaction | Specification | name | type | description            | required |
|-------------|----------------|------|------|------------------------|----------|
| Request     | path variable  | id   | long | 주어진 id(long)        | yes      |
| Response    | body           |      | BookResponse | 삭제된 도서의 정보 |          |


### 조건으로 책 목록 조회 :

> ![](https://img.shields.io/static/v1?label=&message=GET&color=blue) <br />
> buzz-book.store:**8090/api/books**

| Transaction | Specification | name       | type    | description                        | required |
|-------------|----------------|------------|---------|------------------------------------|----------|
| Request     | parameter      | pageNo     | Integer | 페이지 번호 (기본값: 0)            | no       |
|             | parameter      | pageSize   | Integer | 한 페이지에 보여질 아이템 수 (기본값: 10) | no       |
|             | parameter      | hasProduct | Boolean | 상품으로 등록된 책들만 조회할지 여부 (기본값: false) | no       |
|             | parameter      | productId  | Integer | 상품 id(int)로 책을 조회할 경우 사용 | no       |
| Response    | body           |            | Page\<BookResponse\> | 조회된 책 목록                   |          |

































