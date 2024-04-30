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
