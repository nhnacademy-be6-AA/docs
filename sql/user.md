### User 쪽 ddl

- login_id unique 부여 index 추가

```

DROP table if exists `address`;
CREATE TABLE `address` (
	`id`	bigint	NOT NULL,
	`user_id`	bigint	NOT NULL,
	`address`	varchar(255)	NOT NULL,
	`detail`	varchar(255)	NOT NULL,
	`zipcode`	int	NOT NULL,
	`nation`	varchar(50)	NOT NULL,
	`alias`	varchar(20)	NOT NULL
);

DROP table if exists `deactivation`;
CREATE TABLE `deactivation` (
	`user_id`	bigint	NOT NULL ,
	`reason`	varchar(50)	NOT NULL,
	`deactivation_date`	datetime	NOT NULL	DEFAULT NOW()
);

DROP table if exists `grade`;
CREATE TABLE `grade` (
	`id`	int	NOT NULL ,
	`name`	varchar(20)	NOT NULL,
	`standard`	int	NOT NULL,
	`benefit`	double	NOT NULL
);

DROP table if exists `user`;
CREATE TABLE `user` (
	`id`	bigint	NOT NULL,
	`login_id`	varchar(20)	NOT NULL unique,
	`name`	varchar(20)	NOT NULL,
	`contact_number`	varchar(15)	NOT NULL,
	`email`	varchar(255)	NOT NULL,
	`password`	varchar(255)	NOT NULL,
	`birthday`	DATE	NOT NULL,
	`create_date`	datetime	NOT NULL DEFAULT NOW(),
	`last_login_date`	datetime	NULL DEFAULT NOW(),
	`status`	varchar(10)	NOT NULL,
	`modify_date`	datetime	NULL DEFAULT NOW(),
	`grade_id`	int	NOT NULL,
	`is_admin`	boolean	NOT NULL
);

DROP table if exists `user_auth`;
CREATE TABLE `user_auth` (
	`id`	int	NOT NULL  ,
	`user_id`	bigint	NOT NULL ,
	`provider`	varchar(20)	NOT NULL ,
	`token`	varchar(255)	NOT NULL,
	`create_date`	datetime	NOT NULL
);

DROP table if exists `cart`;
CREATE TABLE `cart` (
	`id`	bigint	NOT NULL ,
	`user_id`	bigint	NULL,
	`update_date`	datetime	NOT NULL	DEFAULT NOW()
);

DROP table if exists `cart_detail`;
CREATE TABLE `cart_detail` (
	`id` 	bigint	NOT NULL ,
	`cart_id`	bigint	NOT NULL ,
	`quantity`	int	NOT NULL	DEFAULT 0,
	`product_id`	int	NOT NULL
);

DROP table if exists `wishlist`;
CREATE TABLE `wishlist` (
	`id`	bigint	NOT NULL ,
	`user_id`	bigint	NOT NULL,
	`product_id`	int	NOT NULL
);

ALTER TABLE `address` ADD CONSTRAINT `PK_ADDRESS` PRIMARY KEY (
	`id`
);

ALTER TABLE `address` MODIFY COLUMN id bigint auto_increment not null;

ALTER TABLE `deactivation` ADD CONSTRAINT `PK_DEACTIVATION` PRIMARY KEY (
	`user_id`
);

ALTER TABLE `grade` ADD CONSTRAINT `PK_GRADE` PRIMARY KEY (
	`id`
);

ALTER TABLE `grade` MODIFY COLUMN id int auto_increment not null;


ALTER TABLE `user` ADD CONSTRAINT `PK_USER` PRIMARY KEY (
	`id`
);

ALTER TABLE `user` MODIFY COLUMN id bigint auto_increment not null;


ALTER TABLE `user_auth` ADD CONSTRAINT `PK_USER_AUTH` PRIMARY KEY (
	`id`
);

ALTER TABLE `user_auth` MODIFY COLUMN id bigint auto_increment not null;

ALTER TABLE `cart` ADD CONSTRAINT `PK_CART` PRIMARY KEY (
	`id`
);

ALTER TABLE `cart` MODIFY COLUMN id bigint auto_increment not null;

ALTER TABLE `cart_detail` ADD CONSTRAINT `PK_CART_DETAIL` PRIMARY KEY (
	`id`
);

ALTER TABLE `cart_detail` MODIFY COLUMN id bigint auto_increment not null;

ALTER TABLE `wishlist` ADD CONSTRAINT `PK_WISHLIST` PRIMARY KEY (
	`id`
);

ALTER TABLE `wishlist` MODIFY COLUMN id bigint auto_increment not null;

ALTER TABLE `address` ADD CONSTRAINT `FK_user_TO_address_1` FOREIGN KEY (
	`user_id`
)
REFERENCES `user` (
	`id`
);

ALTER TABLE `deactivation` ADD CONSTRAINT `FK_user_TO_deactivation_1` FOREIGN KEY (
	`user_id`
)
REFERENCES `user` (
	`id`
);

ALTER TABLE `user_auth` ADD CONSTRAINT `FK_user_TO_user_auth_1` FOREIGN KEY (
	`user_id`
)
REFERENCES `user` (
	`id`
);

ALTER TABLE `user` ADD CONSTRAINT `FK_grade_TO_user_1` FOREIGN KEY (
	`grade_id`
)
REFERENCES `grade` (
	`id`
);

ALTER TABLE `cart` ADD CONSTRAINT `FK_user_TO_cart_1` FOREIGN KEY (
	`user_id`
)
REFERENCES `user` (
	`id`
);

ALTER TABLE `cart_detail` ADD CONSTRAINT `FK_cart_TO_cart_detail_1` FOREIGN KEY (
	`cart_id`
)
REFERENCES `cart` (
	`id`
);

ALTER TABLE `cart_detail` ADD CONSTRAINT `FK_product_TO_cart_detail_1` FOREIGN KEY (
	`product_id`
)
REFERENCES `product` (
	`id`
);

ALTER TABLE `wishlist` ADD CONSTRAINT `FK_user_TO_wishlist_1` FOREIGN KEY (
	`user_id`
)
REFERENCES `user` (
	`id`
);

ALTER TABLE `wishlist` ADD CONSTRAINT `FK_product_TO_wishlist_1` FOREIGN KEY (
	`product_id`
)
REFERENCES `product` (
	`id`
);

alter table `user` modify column `birthday` datetime;

```