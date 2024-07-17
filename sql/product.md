### 상품 테이블 관련 sql문

```
CREATE TABLE category (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(20) NOT NULL,
    parent_id INT,
    FOREIGN KEY (parent_id) REFERENCES category(id)
);

CREATE TABLE publisher (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);


CREATE TABLE book (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    description TEXT,
    isbn VARCHAR(13) NOT NULL,
    publisher_id INT NOT NULL,
    publish_date DATE,
    product_id INT,
    FOREIGN KEY (publisher_id) REFERENCES publisher(id),
    FOREIGN KEY (product_id) REFERENCES product(id)
);
CREATE TABLE product (
    id INT AUTO_INCREMENT PRIMARY KEY,
    stock INT NOT NULL,
    price INT,
    forward_date DATE,
    score INT,
    thumbnail_path VARCHAR(255),
    description text,
    category_id INT NOT NULL,
    product_name VARCHAR(255) NOT NULL,
    stock_status varchar(20) NOT NULL,
    FOREIGN KEY (category_id) REFERENCES category(id)
);

CREATE TABLE author (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL
);

CREATE TABLE book_author (
    id INT AUTO_INCREMENT PRIMARY KEY,
    author_id INT NOT NULL,
    book_id BIGINT NOT NULL,
    FOREIGN KEY (author_id) REFERENCES author(id),
    FOREIGN KEY (book_id) REFERENCES book(id)
);

CREATE TABLE review (
    id INT AUTO_INCREMENT PRIMARY KEY,
    content VARCHAR(255) NOT NULL,
    picture_path VARCHAR(255),
    order_detail_id BIGINT NOT NULL,
    review_score INT NOT NULL,
    review_create_date DATETIME NOT NULL
);


CREATE TABLE review (
	id	int	NOT NULL primary key auto_increment,
	content	varchar(255)	NOT NULL,
	pricture_path	varchar(255)	NULL,
	review_score	int	NOT NULL,
	review_created_at	datetime	NOT NULL,
	order_detail_id	bigint	NOT NULL,
    foreign key (order_detail_id) references order_detail(id)
    );
    

CREATE TABLE tag (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(20) NOT NULL
);

CREATE TABLE product_tag (
    tag_id INT NOT NULL,
    product_id INT NOT NULL,
    PRIMARY KEY (tag_id, product_id),
    FOREIGN KEY (tag_id) REFERENCES tag(id),
    FOREIGN KEY (product_id) REFERENCES product(id)
);
```

주문의 리뷰
```
CREATE TABLE review (
	id	int	NOT NULL primary key auto_increment,
	content	varchar(255)	NOT NULL,
	pricture_path	text	NULL,
	review_score	int	NOT NULL,
	review_created_at	datetime	NOT NULL,
	order_detail_id	bigint	NOT NULL,
    foreign key (order_detail_id) references order_detail(id)
    );
```
