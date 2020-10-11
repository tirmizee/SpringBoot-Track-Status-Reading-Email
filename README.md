# SpringBoot-Track-Status-Reading-Email

### Simple database design

    create table customer (
       id BIGINT NOT NULL AUTO_INCREMENT,
       first_name VARCHAR(255) NOT NULL,
       last_name VARCHAR(255) NOT NULL,
       email VARCHAR(255),
       create_date DATE,
       update_date DATE,
       PRIMARY KEY (id)
    );

    create table send_mail(
       id BIGINT NOT NULL AUTO_INCREMENT,
       title VARCHAR(255) NOT NULL,
       customer_id BIGINT,
       token VARCHAR(255),
       type VARCHAR(1),
       is_read TINYINT(1),
       create_date DATE,
       update_date DATE,
       PRIMARY KEY (id),
       FOREIGN KEY (customer_id) REFERENCES customer(id)
    );
