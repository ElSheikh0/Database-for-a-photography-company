CREATE TABLE Employees
  ( 
    SSN     NUMBER(20) NOT NULL primary key,
    F_name  VARCHAR(20) NOT NULL,
    L_name  VARCHAR(20)NOT NULL,
    gender  VARCHAR(10)NOT NULL,
    address VARCHAR(40)NOT NULL,
   
    hire_date DATE,
   
    salary     NUMBER(10) NOT NULL,
    depart_id  NUMBER(10)NOT NULL,
    supervises number(20)
  );
CREATE TABLE Employees_phone
  (
    SSN   NUMBER(20) NOT NULL,
    phone NUMBER(15),
     primary key(SSN,phone),
     FOREIGN KEY(SSN) References  employees(SSN)
  );
CREATE TABLE Dependent
  (
    SSN          NUMBER(20),
    name         VARCHAR2(20) NOT NULL,
    gender       VARCHAR2(10),
    relationship VARCHAR2(35),
    primary key(SSN,name),
    FOREIGN KEY(SSN) References  employees(SSN)
    
  );
create table Department (
                   dep_id number(15) ,
                   dep_name varchar2(30) NOT NULL,
                   mgr_start_date date  NOT NULL,
                   mgr_ssn number(20) not null,
               primary key(dep_id),
               FOREIGN KEY(mgr_ssn) References employees(SSN)
                  
                   );
              
create table Section(
            sec_id varchar2(15) primary key ,
            sec_name varchar2(90) Not NULL ,
            sec_location varchar2(45) Not NULL
            );
           
           
  create table Work_in (
                        SSN number(20) ,
                        sec_id varchar2(15) ,
                        hours number(4) ,
                        FOREIGN KEY(SSN) References employees(SSN),
                        FOREIGN KEY(sec_id) References section(sec_id),
                        primary key(SSN,sec_id)
                        );
                        
create table Cart(
        cart_id number(5) primary key not null
);


create table Customer(
         customer_id number(10) primary key not null,
         F_Name varchar2(20),
         L_Name varchar2(20),
         email varchar2(40)
     
);
create table Customer_phone(
       customer_id number(10), 
       phone number(15),
       primary key(customer_id,phone),
       FOREIGN KEY(customer_id) References customer(customer_id)
        
);
create table Paymet(
          pay_id number(10) not null primary key,
          pay_type varchar2(30),
          cart_id number(20) unique,
          customer_id number(10),
           FOREIGN KEY(customer_id) References customer(customer_id),
           FOREIGN KEY(cart_id) References cart(cart_id)
      
   
);
create table Product(
          pro_id number(5)  not null ,
          cart_id number(5)  ,
          Name varchar2(30) not null,
          price number(8,2) not null check(price>0),
          product_type varchar2(40) not null ,
          description varchar2(90),
          sec_id varchar2 (15) not null  ,
        FOREIGN KEY(sec_id) References section(sec_id),
        FOREIGN KEY(cart_id) References cart(cart_id),
        
        primary key(pro_id)
);               


  /* ------------------------------------------------------------------------------------------------------ */
  
  
--11111Mang 10
INSERT
INTO Employees (SSN, F_name, l_name, gender, address,  hire_date, salary, depart_id, supervises)
VALUES
  (202017001 ,'saad' , 'samir' ,'male' ,'cairo' ,'13 may 1997' ,6000 , 10 , null
  );

  --2222Mang 11
INSERT
INTO Employees (SSN, f_name, l_name, gender, address,  hire_date, salary, depart_id, supervises)
VALUES
  (202017002 ,'mohammed' , 'samir' ,'male' ,'cairo' ,'13 may 1998' ,6500 , 11 , null
  );
  --33333 Mang 12
INSERT
INTO Employees (SSN, f_name, l_name, gender, address,  hire_date, salary, depart_id, supervises)
VALUES
  (202017003 ,'saad' , 'mohamed' ,'male' ,'cairo' ,'13 may 1997' ,8000 , 12 , null
  );
  --4444444super 10
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (202017004 ,'ahmed' , 'samir' ,'male' ,'giza' ,'13 may 1992' ,6000 , 10 , null
  );
  
  --5555555super 11
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (202017005 ,'sara' , 'ahmed' ,'female' ,'cairo'  ,'13 aug 1990' ,3000 , 11 ,null
  );
  
  --6666666super 12
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (202017006 ,'soha' , 'samir' ,'female' ,'cairo' ,'13 may 1995' ,4000 , 12 , null
  );
  --777777
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (202017007 ,'wezza' , 'osama' ,'male' ,'cairo' ,'13 may 1997' ,10000 , 11 , 202017005
  );
  --8888888
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (202017008 ,'mohy' , 'ahmed' ,'male' ,'cairo'  ,'13 may 1987' ,9000 , 10 ,202017004
  );
  
  --99999
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (202017009 ,'osama' , 'samir' ,'male' ,'cairo'  ,'13 may 1997' ,6000 , 12 ,202017006
  );
  --101010
INSERT
INTO Employees (SSN, f_name, l_name, gender, address, hire_date, salary, depart_id, supervises)
VALUES
  (2020170010 ,'gana' , 'ayman' ,'female' ,'cairo'  ,'13 may 2000' ,4500 , 10 , 202017004
  );
  /* ------------------------------------------------------------------------------------------------------ */
  
  /*dep*/
  --10
    INSERT
INTO department (dep_id, mgr_ssn ,dep_name, mgr_start_date )
VALUES
 ( 10,202017001,'IT','14 AUG 2016');
  
--11
      INSERT
INTO department (dep_id,mgr_ssn , dep_name, mgr_start_date )
VALUES
        ( 11,202017002,'security','14 aug 2017');
  --12
   INSERT
INTO department (dep_id,mgr_ssn , dep_name, mgr_start_date )
VALUES
        ( 12,202017003, 'sales','15 may 2015');
  
   /* ------------------------------------------------------------------------------------------------------ */
  /*-------------------------------------*/
     /*insert depen*/   
insert
into dependent(ssn, name, gender, relationship)
values(2020170010,'khaled','male','son');
insert
into dependent(ssn, name, gender, relationship)
values(2020170010,'Nada','female','daughter');
----------------------
insert
into dependent(ssn, name, gender, relationship)
values(202017009,'yousef','male','son');

/*------------------------------------*/
  /*insert emp phone*/
        insert 
        into employees_phone(ssn, phone)
        values(202017001,01120253132);
        -------------------------------
         insert 
        into employees_phone(ssn, phone)
        values(202017001,01520253132);
        -------------------------------
         insert 
        into employees_phone(ssn, phone)
        values(202017002,01110253132);
        -------------------------------
         insert 
        into employees_phone(ssn, phone)
        values(202017003,01120243132);
        -------------------------------
        insert 
        into employees_phone(ssn, phone)
        values(202017004,011020243132);
        -------------------------------
        insert 
        into employees_phone(ssn, phone)
        values(202017005,01720243132);
        -------------------------------
        insert 
        into employees_phone(ssn, phone)
        values(202017006,01120253132);
        -------------------------------
        insert 
        into employees_phone(ssn, phone)
        values(202017007,010020243132);
        -------------------------------
        insert 
        into employees_phone(ssn, phone)
        values(202017008,011020243132);
        -------------------------------
         insert 
        into employees_phone(ssn, phone)
        values(202017009,01102028832);
        -------------------------------
         insert 
        into employees_phone(ssn, phone)
        values(2020170010,011020255132);
        -------------------------------
 
  /*inser into sec*/
  insert 
  into section(sec_id, sec_name, sec_location)
  values ('A1','Cameras','1st floor');
  ----
  insert 
  into section(sec_id, sec_name, sec_location)
  values ('A2','Stands','1st floor');
  ------
  insert 
  into section(sec_id, sec_name, sec_location)
  values ('B1','Lens','2nd floor');
  -------
  insert 
  into section(sec_id, sec_name, sec_location)
  values ('B2','Softboxes','2nd floor');
  /*----------------------------------------------------------------------------------*/

 
  /*--------insert customer----------*/
  insert into customer (customer_id, f_name, l_name, email)
  values ( 50, 'wael' , 'ghoneem'  ,'waelghoneemxyz1@gmail.com');
 ----------------
  insert into customer (customer_id, f_name, l_name, email)
  values ( 51, 'ahmed' , 'ghoneem'  ,'ahemdghoneemxyz2@gmail.com');
-----------------
  insert into customer (customer_id, f_name, l_name, email)
  values ( 52, 'mohammed' , 'ahmed'  ,'mohahmed@gmail.com');
-----------------
  insert into customer (customer_id, f_name, l_name, email)
  values ( 53, 'mona' , 'mohammed'  ,'monamoha@gmail.com');
 -----------------
  insert into customer (customer_id, f_name, l_name, email)
  values ( 54, 'ahmed' , 'mohamed'  ,'ahmedmoha@gmail.com');
  ------------------
  insert into customer (customer_id, f_name, l_name, email)
  values ( 55, 'nada' , 'ahmed'  ,'nadahmed@gmail.com');

 /*insert customer phone*/
        insert 
        into customer_phone(customer_id, phone)
        values(50,01220455132);
        -------------------------------
        insert 
        into customer_phone(customer_id, phone)
        values(51,01220455133);
        -------------------------------
        insert 
        into customer_phone(customer_id, phone)
        values(52,01220455134);
        -------------------------------
        insert 
        into customer_phone(customer_id, phone)
        values(53,01220455135);
        -------------------------------
        insert 
        into customer_phone(customer_id, phone)
        values(54,01220455136);
        -------------------------------
        insert 
        into customer_phone(customer_id, phone)
        values(55,01220455137);
        -------------------------------

 
 /*insert cart*/
  insert into cart (cart_id)
  values (1);
  --------------------------
  insert into cart (cart_id)
  values (2);
  --------------------------
  insert into cart (cart_id)
  values (3);
  --------------------------
  insert into cart (cart_id)
  values (4);
  --------------------------
  insert into cart (cart_id)
  values (5);
  --------------------------
  insert into cart (cart_id)
  values (6);

 /*insert paymet*/
  --- id from 2 to...
  insert into paymet(pay_id, pay_type, cart_id, customer_id)
  values (2,'debit card',1,50);
  ----------------------
  insert into paymet(pay_id, pay_type, cart_id, customer_id)
  values (3,'debit card',2,51);
  --------------------
  insert into paymet(pay_id, pay_type, cart_id, customer_id)
  values (4,'cash',3,52);
  ---------------------------
  insert into paymet(pay_id, pay_type, cart_id, customer_id)
  values (5,'cash',4,53);
  ------------------
  insert into paymet(pay_id, pay_type, cart_id, customer_id)
  values (6,'credit card',5,54);
  ---------------
  insert into paymet(pay_id, pay_type, cart_id, customer_id)
  values (7,'credit card',6,55);
  /*------------------------------------------------*/

  /*--------------------------------------------*/
  
    /*insert product*/
    /*106 >>*/
INSERT
INTO product (pro_id, cart_id, name, price, product_type, description, sec_id)
VALUES (106, null,'lens M10',1800, 'Lens', 'The most compatible lens for you.','B1');
----------------------------------
INSERT
INTO product (pro_id, cart_id, name, price, product_type, description, sec_id)
VALUES (107, 1,'lens M10',1800, 'Lens', 'The most compatible lens for you.','B1');
----------------------------------
INSERT
INTO product (pro_id, cart_id, name, price, product_type, description, sec_id)
VALUES (108, 2,'Light stand M2', 500, 'Stand', 'The best budget-friendly light stand.','A2');
----------------------------------
INSERT
INTO product (pro_id, cart_id, name, price, product_type, description, sec_id)
VALUES (109, null,'Light stand M3',1200, 'Stand', 'A light stand for true professionals.','A2');
----------------------------------
INSERT
INTO product (pro_id, cart_id, name, price, product_type, description, sec_id)
VALUES (110, null,'Camera F3912',3000, 'Camera', 'The camera designed to suit your needs.','A1');
----------------------------------
INSERT
INTO product (pro_id, cart_id, name, price, product_type, description, sec_id)
VALUES (111, 3,'Softbox F20 Pro',500, 'Sotbox', 'The softbox designed carefully and professionally to suit your needs.','B2');
----------------------------------

   /* ------------------------------------------------------------------------------------------------------ */

   /*insert work in*//////////////////
INSERT
INTO work_in (ssn, sec_id, hours) 
VALUES
        (202017001,'A1',10);
  -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours) 
VALUES
        (202017001,'A2',5);
  -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017002,'B1',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017003,'B2',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017004,'A2',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017005,'B1',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017006,'A2',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017007,'A2',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017008,'B1',13);
        ----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017009,'B2',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (202017009,'B1',3);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (2020170010,'A1',13);
        -----------------------------
INSERT
INTO work_in (ssn, sec_id, hours)
VALUES
        (2020170010,'B1',2);
        -----------------------------
  /*----------------------------------------------------------------------*/



