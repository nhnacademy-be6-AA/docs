DROP TABLE IF EXISTS `bill_log`;
DROP TABLE IF EXISTS `order_detail`;
DROP TABLE IF EXISTS `order`;
DROP TABLE IF EXISTS `delivery_policy`;
DROP TABLE IF EXISTS `wrapping`;
DROP TABLE IF EXISTS `order_status`;

CREATE TABLE `wrapping` (
    `id` int NOT NULL AUTO_INCREMENT,
    `paper` varchar(20) NOT NULL COMMENT '예)박스,종이 포장 등등',
    `price` int NOT NULL,
    PRIMARY KEY (`id`)
);

CREATE TABLE `order_status` (
    `id` int NOT NULL AUTO_INCREMENT,
    `name` varchar(20) NOT NULL,
    `update_at` datetime NOT NULL,
    PRIMARY KEY (`id`)
);


CREATE TABLE `delivery_policy` (
    `id` int NOT NULL AUTO_INCREMENT,
    `name` varchar(20) NOT NULL,
    `standard_price` int NOT NULL,
    `policy_price` int NOT NULL,
    PRIMARY KEY (`id`)
);

CREATE TABLE `order` (
    `id` bigint NOT NULL AUTO_INCREMENT,
    `user_id` bigint COMMENT '회원 고유 ID (AUTO_INCREMENT)',
    `price` int NOT NULL,
    `request` varchar(200) NULL,
    `address` varchar(200) NOT NULL,
    `address_detail` varchar(200) NULL,
    `zipcode` int NOT NULL,
    `desired_delivery_date` date NULL,
    `receiver` varchar(20) NOT NULL,
    `order_str` varchar(50) NOT NULL,
    `sender` varchar(20) NOT NULL,
    `sender_contact_number` varchar(15) NOT NULL,
    `receiver_contact_number` varchar(15) NOT NULL,
    `order_email` varchar(30),
    `coupon_code` varchar(20),
    `delivery_rate` int not null,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`user_id`) REFERENCES `user` (`id`)
);


CREATE TABLE `order_detail` (
    `id` bigint NOT NULL AUTO_INCREMENT,
    `product_id` int NOT NULL,
    `order_id` bigint NOT NULL,
    `order_status_id` int NOT NULL,
    `wrapping_id` int,
    `price` int NOT NULL,
    `quantity` int NOT NULL,
    `wrap` boolean NOT NULL DEFAULT false,
    `create_at` datetime NOT NULL,
    `update_at` datetime NOT NULL,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`product_id`) REFERENCES `product` (`id`),
    FOREIGN KEY (`order_id`) REFERENCES `order` (`id`),
    FOREIGN KEY (`order_status_id`) REFERENCES `order_status` (`id`),
    FOREIGN KEY (`wrapping_id`) REFERENCES `wrapping` (`id`)
);

CREATE TABLE `bill_log` (
    `id` bigint NOT NULL AUTO_INCREMENT,
    `payment` varchar(20) NOT NULL,
    `price` int NOT NULL,
    `pay_at` datetime NOT NULL,
    `status` varchar(20) NOT NULL COMMENT 'ENUM(결제전, 결제완료, 결제 취소, 환불, 결제실패)',
    `payment_key` varchar(50),
	`order_id` bigint NOT NULL,
    `cancel_reason` varchar(255),
    PRIMARY KEY (`id`),
    FOREIGN KEY (`order_id`) REFERENCES `order` (`id`)
);
