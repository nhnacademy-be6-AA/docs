### 상품 테이블 관련 sql문

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
    publish_date DATETIME,
    id2 BIGINT,
    FOREIGN KEY (publisher_id) REFERENCES publisher(id)
);

CREATE TABLE product (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    stock INT NOT NULL,
    price DECIMAL(19, 2) NOT NULL,
    forward_date DATE,
    score INT,
    thumbnail_path VARCHAR(255),
    category_id INT NOT NULL,
    book_id BIGINT NOT NULL,
    FOREIGN KEY (category_id) REFERENCES category(id),
    FOREIGN KEY (book_id) REFERENCES book(id)
);

CREATE TABLE author (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
);

CREATE TABLE book_author (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    author_id BIGINT NOT NULL,
    book_id BIGINT NOT NULL,
    FOREIGN KEY (author_id) REFERENCES author(id),
    FOREIGN KEY (book_id) REFERENCES book(id)
);

CREATE TABLE review (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    content VARCHAR(255) NOT NULL,
    picture_path VARCHAR(255),
    product_id BIGINT NOT NULL,
    review_score INT NOT NULL,
    review_create_date DATETIME NOT NULL,
    FOREIGN KEY (product_id) REFERENCES product(id)
);

CREATE TABLE tag (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(20) NOT NULL
);

CREATE TABLE product_tag (
    tag_id INT NOT NULL,
    product_id BIGINT NOT NULL,
    PRIMARY KEY (tag_id, product_id),
    FOREIGN KEY (tag_id) REFERENCES tag(id),
    FOREIGN KEY (product_id) REFERENCES product(id)
);
