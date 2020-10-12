# SpringBoot-Track-Status-Reading-Email

### Simple database design

<p align="center">
  <img src="https://user-images.githubusercontent.com/15135199/95685505-7cf84980-0c22-11eb-8573-8e4f1f0ab774.JPG" width="500">
</p>

#### script create table

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

    CREATE UNIQUE INDEX idx_token ON send_mail (token);
