# SpringBoot-Track-Status-Reading-Email

### Simple database design

    create table send_mail(
       id BIGINT NOT NULL AUTO_INCREMENT,
       title VARCHAR(255) NOT NULL,
       emp_id BIGINT,
       token VARCHAR(255),
       type VARCHAR(1),
       create_date DATE,
       update_date DATE,
       PRIMARY KEY (id),
       FOREIGN KEY (emp_id) REFERENCES employee(id)
    );
