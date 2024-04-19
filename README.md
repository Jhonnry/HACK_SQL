# HACK 1

create table countries(
  id_country serial primary key,
  name varchar(50) not null  
);

create table users(
 id_users serial primary key,
 id_country integer not null,
 email varchar(100) not null,
 name varchar (50) not null,
 foreign key (id_country) references countries (id_country)   
);

![SQL1 PRINT](https://github.com/Jhonnry/HACK_SQL/assets/147669752/921b59ef-e525-4708-8b74-103a2055f5d1)

# HACK 2

create table countries(
  id_country serial primary key,
  name varchar(50) not null  
);

create table users(
 id_users serial primary key,
 id_country integer not null,
 email varchar(100) not null,
 name varchar (50) not null,
 foreign key (id_country) references countries (id_country)   
);

insert into countries (name) values ('argentina') , ('colombia'),('chile');
select * from countries;

insert into users (id_country, email, name) 
  values (2, 'foo@foo.com', 'fooziman'), (3, 'bar@bar.com', 'barziman'); 
select * from users;

delete from users where email = 'bar@bar.com';

update users set email = 'foo@foo.foo', name = 'fooz' where id_users = 1;
select * from users;

select * from users inner join  countries on users.id_country = countries.id_country;

select u.id_users as id, u.email, u.name as fullname, c.name 
  from users u inner join  countries c on u.id_country = c.id_country;

  ![SQL2 PRINT](https://github.com/Jhonnry/HACK_SQL/assets/147669752/e0d40a30-c3da-4607-ad24-9dabda77cc90)

# HACK 3

  create table countries (
  id_country serial primary key,
  name varchar(100) not null,
  population integer
);

create tables priorities (
  id serial primary key,
  id_priority varchar(100) not null,
  id_name varchar(100) not null,
  description text
);
create table contact_request (
  id serial primary key,
  id_email varchar(100) not null,
  id_country varchar(100) not null,
  id_priority varchar(100) not null,
  name varchar(100) not null,
  detail varchar(100) not null,
  physical_address varchar(100) not null,
  message text,
  priority_id integer references priorities(id)
); 

![SQL3 PRINT](https://github.com/Jhonnry/HACK_SQL/assets/147669752/4af0d657-2e03-4153-bc16-0577d3e7f7f0)

# HACK 4

create table countries (
  id_country serial primary key,
  name varchar(100) not null,
  id integer
);

create table priorities (
  id serial primary key,
  id_priority varchar(100) not null,
  id_name varchar(100) not null,
  message text
);

create table contact_request (
  id serial primary key,
  id_email varchar(100) not null,
  id_country varchar(100) not null,
  id_priority varchar(100) not null,
  name varchar(100) not null,
  detail varchar(100) not null,
  physical_address integer references priorities(id)
);

insert into countries (id_country, name, id) values 
(1, 'venezuela', 1), 
(2, 'colombia', 2),
(3, 'chile', 3), 
(4, 'argentina', 4), 
(5, 'mexico', 5);

select * from countries;

insert into priorities (id_priority, id_name, message) values 
('priority1', 'name1', 'message1'),
('priority2', 'name2', 'message2'),
('priority3', 'name3', 'message3');

select * from priorities;

insert into contact_request (id_email, id_country, id_priority, name, detail) values
('jhon@jhon.com', 'venezuela', 'priority1', 'John Altuve', 'Detail 1'),
('lehidy@lehidy.com', 'colombia', 'priority2', 'Lehidy Altuve', 'Detail 2'),
('eroxy@roxy.com', 'chile', 'priority3', 'Roxy Altuve', 'Detail 3');

select * from contact_request;

delete from contact_request
where id = (select MAX(id) from contact_request);

update contact_request
set name = 'new name', detail = 'new netail'
where id = (select min(id) from contact_request);

![SQL4 PRINT](https://github.com/Jhonnry/HACK_SQL/assets/147669752/176145ab-1198-41e6-acd4-ab536d5c4141)

# HACK 5

create table countries (
  id_country serial primary key,
  name varchar(100) not null
);

create table roles (
  id_role serial primary key,
  name varchar(100) not null
);

create table taxes (
  id_tax serial primary key,
  percentage numeric(5,2) not null
);

create table offers (
  id_offer serial primary key,
  status varchar(100) not null
);

create table discounts (
  id_discount serial primary key,
  status varchar(100) not null,
  percentage numeric(5,2) not null
);

create table payments (
  id_payment serial primary key,
  type varchar(100) not null
);

create table customers (
  email varchar(100) primary key,
  id_country integer references countries(id_country),
  id_role integer references roles(id_role),
  name varchar(100) not null,
  age integer not null,
  password varchar(100) not null,
  physical_address varchar(100) not null
);

create table invoice_status (
  id_invoice_status serial primary key,
  invoice varchar(100) not null
);

create table products (
  id_product serial primary key,
  id_discount integer references discounts(id_discount),
  id_offer integer references offers(id_offer),
  id_tax integer references taxes(id_tax),
  name varchar(100) not null,
  details text,
  minimum_stock integer,
  maximum_stock integer,
  current_stock integer,
  price numeric(10,2) not null,
  price_with_tax numeric(10,2)
);

create table product_customers (
  id_product integer references products(id_product),
  id_customer varchar(100) references customers(email)
);

create table invoices (
  id_invoice serial primary key,
  id_customer varchar(100) references customers(email),
  id_payment integer references payments(id_payment),
  id_invoice_status integer references invoice_status(id_invoice_status),
  date date,
  total_to_pay numeric(10,2)
);

create table orders (
  id_order serial primary key,
  id_invoice integer references invoices(id_invoice),
  id_product integer references products(id_product),
  detail varchar(100),
  amount integer,
  price numeric(10,2)
);

![SQL5 PRINT](https://github.com/Jhonnry/HACK_SQL/assets/147669752/cd5abb56-8699-4100-affd-6960b169bab0)

# HACK 6

create table countries (
  id_country serial primary key,
  name varchar(100) not null
);

create table roles (
  id_role serial primary key,
  name varchar(100) not null
);

create table taxes (
  id_tax serial primary key,
  percentage numeric(5,2) not null
);

create table offers (
  id_offer serial primary key,
  status varchar(100) not null
);

create table discounts (
  id_discount serial primary key,
  status varchar(100) not null,
  percentage numeric(5,2) not null
);

create table payments (
  id_payment serial primary key,
  type varchar(100) not null
);

create table customers (
  email varchar(100) primary key,
  id_country integer references countries(id_country),
  id_role integer references roles(id_role),
  name varchar(100) not null,
  age integer not null,
  password varchar(100) not null,
  physical_address varchar(100) not null
);

create table invoice_status (
  id_invoice_status serial primary key,
  invoice varchar(100) not null
);

create table products (
  id_product serial primary key,
  id_discount integer references discounts(id_discount),
  id_offer integer references offers(id_offer),
  id_tax integer references taxes(id_tax),
  name varchar(100) not null,
  details text,
  minimum_stock integer,
  maximum_stock integer,
  current_stock integer,
  price numeric(10,2) not null,
  price_with_tax numeric(10,2)
);

create table product_customers (
  id_product integer references products(id_product),
  id_customer varchar(100) references customers(email)
);

create table invoices (
  id_invoice serial primary key,
  id_customer varchar(100) references customers(email),
  id_payment integer references payments(id_payment),
  id_invoice_status integer references invoice_status(id_invoice_status),
  date date,
  total_to_pay numeric(10,2)
);

create table orders (
  id_order serial primary key,
  id_invoice integer references invoices(id_invoice),
  id_product integer references products(id_product),
  detail varchar(100),
  amount integer,
  price numeric(10,2)
);

insert into countries (name) values ('venezuela'), ('colombia'), ('argentina');
insert into roles (name) values ('Role 1'), ('Role 2'), ('Role 3');
insert into taxes (percentage) values (10.0), (15.0), (20.0);
insert into offers (status) values ('Offer 1'), ('Offer 2'), ('Offer 3');
insert into discounts (status, percentage) values ('Discount 1', 5.0), ('Discount 2', 10.0), ('Discount 3', 15.0);
insert into payments (type) values ('Payment 1'), ('Payment 2'), ('Payment 3');
insert into customers (email, id_country, id_role, name, age, password, physical_address)
  VALUES ('customer1@example.com', 1, 1, 'Customer 1', 30, 'password1', 'Address 1'),
         ('customer2@example.com', 2, 2, 'Customer 2', 35, 'password2', 'Address 2'),
         ('customer3@example.com', 3, 3, 'Customer 3', 40, 'password3', 'Address 3');
insert into invoice_status (invoice) VALUES ('Invoice 1'), ('Invoice 2'), ('Invoice 3');
insert into products (id_discount, id_offer, id_tax, name, details, minimum_stock, maximum_stock, current_stock, price, price_with_tax)
  values (1, 1, 1, 'Product 1', 'Details 1', 10, 100, 50, 10.0, 11.0),
         (2, 2, 2, 'Product 2', 'Details 2', 20, 200, 150, 20.0, 22.0),
         (3, 3, 3, 'Product 3', 'Details 3', 5, 50, 30, 15.0, 18.0);
insert into product_customers (id_product, id_customer) values (1, 'customer1@example.com'), (2, 'customer2@example.com'), (3, 'customer3@example.com');
insert into invoices (id_customer, id_payment, id_invoice_status, date, total_to_pay)
  values ('customer1@example.com', 1, 1, current_date, 100.0),
         ('customer2@example.com', 2, 2, current_date, 200.0),
         ('customer3@example.com', 3, 3, current_date, 300.0);

delete from invoices where id_customer = 'customer3@example.com';

delete from product_customers where id_customer = 'customer3@example.com';

delete from customers where email = 'customer3@example.com';

update customers set name = 'Updated Name', age = 25 where email = 'customer2@example.com';

update taxes set percentage = percentage * 1.1;

update products set price = price * 1.1, price_with_tax = price_with_tax * 1.1;

![SQL6 PRINT](https://github.com/Jhonnry/HACK_SQL/assets/147669752/de171925-4560-4ee0-88f3-1b5ba234e8ef)



