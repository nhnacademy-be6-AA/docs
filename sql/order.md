DROP TABLE IF EXISTS `user`;
DROP TABLE IF EXISTS `order`;
DROP TABLE IF EXISTS `wrapping`;
DROP TABLE IF EXISTS `order_status`;
DROP TABLE IF EXISTS `bill_log`;
DROP TABLE IF EXISTS `order_detail`;
DROP TABLE IF EXISTS `delivery_policy`;
DROP TABLE IF EXISTS `payment_log`;

CREATE TABLE `user` (
    `id` bigint NOT NULL AUTO_INCREMENT,
    `name` varchar(50) NOT NULL,
    PRIMARY KEY (`id`)
);


CREATE TABLE `wrapping` (
    `id` int NOT NULL AUTO_INCREMENT,
    `paper` varchar(20) NOT NULL COMMENT '예)박스,종이 포장 등등',
    `price` int NOT NULL,
    PRIMARY KEY (`id`)
);

CREATE TABLE `order_status` (
    `id` int NOT NULL AUTO_INCREMENT,
    `name` varchar(10) NOT NULL,
    `update_date` datetime NOT NULL,
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
    `delivery_policy_id` int NOT NULL,
    `user_id` bigint NOT NULL COMMENT '회원 고유 ID (AUTO_INCREMENT)',
    `price` int NOT NULL,
    `request` varchar(200) NULL,
    `address` varchar(200) NOT NULL,
    `address_detail` varchar(200) NULL,
    `zipcode` int NOT NULL,
    `desired_delivery_date` datetime NULL,
    `receiver` varchar(20) NOT NULL,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`delivery_policy_id`) REFERENCES `delivery_policy` (`id`),
    FOREIGN KEY (`user_id`) REFERENCES `user` (`id`)
);


CREATE TABLE `order_detail` (
    `id` bigint NOT NULL AUTO_INCREMENT,
    `product_id` bigint NOT NULL,
    `order_id` bigint NOT NULL,
    `order_status_id` int NOT NULL,
    `package_id` int NOT NULL,
    `price` int NOT NULL,
    `quantity` int NOT NULL,
    `wrap` boolean NOT NULL DEFAULT false,
    `create_date` datetime NOT NULL,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`product_id`) REFERENCES `product` (`id`),
    FOREIGN KEY (`order_id`) REFERENCES `order` (`id`),
    FOREIGN KEY (`order_status_id`) REFERENCES `order_status` (`id`),
    FOREIGN KEY (`package_id`) REFERENCES `wrapping` (`id`)
);

CREATE TABLE `bill_log` (
    `id` bigint NOT NULL AUTO_INCREMENT,
    `payment` varchar(20) NOT NULL,
    `price` int NOT NULL,
    `payment_date` datetime NOT NULL,
    `status` varchar(20) NOT NULL COMMENT 'ENUM(결제전, 결제완료, 결제 취소, 환불, 결제실패)',
    `payment_key` binary(16) NOT NULL,
	`order_id` bigint NOT NULL,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`order_id`) REFERENCES `order` (`id`)
);

CREATE TABLE `payment_log` (
    `id` int NOT NULL AUTO_INCREMENT,
    `bill_id` bigint NOT NULL,
    `name` varchar(20) NOT NULL,
    `price` int NOT NULL,
    PRIMARY KEY (`id`),
    FOREIGN KEY (`bill_id`) REFERENCES `bill_log` (`id`)
);