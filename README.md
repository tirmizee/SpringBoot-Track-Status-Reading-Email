# SpringBoot-Track-Status-Reading-Email

### Concept

1. ออกแบบตารางฐานข้อมูลโดยมี Field "สำหรับเก็บสถานะการอ่านอีเมล"

2. สร้าง api สำหรับอัพเดทสถาะการอ่านอีเมล

3. เมื่อมีการส่งอีเมลให้เพิ่มข้อมูลลงในตารางดังกล่าว พร้อมกับแนบ tag 

        <img style="display:none" src="https://yoursite/emailIdOrToken"width="1" height="1">

ลงใน tempplate email พร้มกับระบุ url ให้เรียกมาที่ api อัพเดทสถาะการอ่านอีเมลของเรา

4. เมื่อผู้ที่ได้รับเมลเปิดอ่าน ระบบจะทำการ render template email ส่งผลให้ tag ต่างๆ ถูกเรียกใช้พ้อมกับ url อัพเดทสถานะการอ่านอีเมลที่เราแนบเข้าไป

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
