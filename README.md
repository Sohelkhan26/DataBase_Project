**Art Work Management**

![Diagram for the Project](Assets/Diagram.png)

## Download Oracle database
> Download the  ([Oracle Database 11g Express Edition](https://www.oracle.com/database/technologies/xe-prior-release-downloads.html)) and install the software.
> Remember the password during the installation because this password is used for connecting the database account.


![alt text](Assets/installation.png)

> Open Run SQL Command line and type the following command and use to password set in the installation process. You may not see the password but don't worry it is getting typed.


```
connect system;
connect / as sysdba
```

>To change the password : 

```
alter user system identified by [password]
```

>To drop the table:

```
DROP TABLE [TABLE_NAME]
```

>CREATE ARTIST TABLE:

```
CREATE TABLE ARTIST(
ARTIST_ID INT PRIMARY KEY,
NAME VARCHAR(45),
BIRTHPLACE VARCHAR(80),
STYLE_OF_ART VARCHAR(100)
);
```

>CREATE ART_WORK TABLE :

```
CREATE TABLE ART_WORK(
ART_ID INT,
ARTWORK_ID INT PRIMARY KEY,
TITLE VARCHAR(50),
DATE_OF_CREATION DATE,
TYPE VARCHAR(100),
PRICE INT,
FOREIGN KEY (ART_ID) REFERENCES ARTIST(ARTIST_ID)
);
```

>CREATE CUSTOMER TABLE:

```
CREATE TABLE CUSTOMER(
ID INT PRIMARY KEY,
NAME VARCHAR(50),
ADDRESS VARCHAR(100),
PHONE INT,
PURCHASED_ID INT,
FOREIGN KEY (PURCHASED_ID) REFERENCES ART_WORK(ARTWORK_ID)
);
```

>GETTING THE INFORMATION OF THE ARTIST WHOSE ART-WORK IS PURCHASED BY John Doe:

```
SELECT * FROM ARTIST WHERE ARTIST_ID = (SELECT ART_ID FROM ART_WORK WHERE ARTWORK_ID = (SELECT ID FROM CUSTOMER WHERE NAME = 'John Doe'));
```
![NESTED SUBQUERY 1](Assets/NESTED%20SUB_Q%20(1).png)

>GETTING THE INFO OF THE ART WORK BOUGHT BY THE CUSTOMER WITH ID = 1:

```
SELECT * FROM ART_WORK WHERE ARTWORK_ID = (SELECT PURCHASED_ID FROM CUSTOMER WHERE ID = 1);
```
![NESTED SUBQUERY 2](Assets/NESTED%20SUB_Q%20(2).png)


>UPDATING DATA IN ARTIST TABLE USING NESTED SUBQUERY:

```
UPDATE ARTIST SET NAME = 'SOHEL' WHERE ARTIST_ID = (SELECT ART_ID FROM ART_WORK WHERE ARTWORK_ID = (SELECT PURCHASED_ID FROM CUSTOMER WHERE ID = 1));
UPDATE ARTIST SET NAME = 'Leonardo da Vinci' WHERE ARTIST_ID = 1;
```


>DELETING DATA FROM THE ARTIST TABLE:
```
INSERT INTO ARTIST (ARTIST_ID, NAME, BIRTHPLACE, STYLE_OF_ART) VALUES (10, 'Leonardo da Vinci', 'KUET', 'Renaissance');
DELETE FROM ARTIST WHERE ARTIST_ID = 10;
```

>ADD COLUMN :

```
ALTER TABLE ARTIST ADD ARTIST_ID INT PRIMARY KEY;
```

