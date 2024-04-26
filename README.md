# ora23ctutorialcontainer

**[Introduction:]**

This free to use under the FREE License as outlined by Oracle
https://docs.oracle.com/en/database/oracle////oracle-database/23/xeinl/licensing-restrictions.html#GUID-805EFC1E-BED8-447C-8125-06459DF50AFC

is a 23c Tutorial Database, with sample Schemas and Datasets under the PDB - FREEPDB1 - Enjoy!

**[Pre-reqs]**

Docker Desktop (Windows,Linux,macOS)

I have tried to build x86/AMD64 image for max compatibility and accessibility. Please let me know if you run into any issues. Thanks!

**[Steps to acquire the image]**

Access the image: docker pull anilmahadev/ora23ctutorial:latest

Once the container has booted up - 

run the command 

**docker run -itd --name <your container name> -p <your host port>:<container port>  anilmahadev/ora23ctutorial:latest **

Give the container a couple of minutes to start as it needs to start the Oracle Process and Database initialization.

Once in, run the following commands to verify that listener is running :

**. oraenv **
Accept the defaults hitting the enter key

Now run 
**lsnrctl status**

Now run **setPassword.sh** by adding your custom password

Wait for the process to finish

Now run **sqlplus / as sysdba**

you are now in the **Root Container aka $CDBROOT**


**[Switching to FREEPDB1]
**
type at sqlplus prompt: show pdbs;

You should see **FREEPDB1**

you will need to switch to the FREEPDB1 pluggable database;

Connected to:
Oracle Database 23c Free Release 23.0.0.0.0 - Develop, Learn, and Run for Free
Version 23.3.0.23.09

**SQL> alter session set container=freepdb1;
**
Session altered.

**SQL> conn OT/OT@FREEPDB1;
**Connected.
SQL>

**SELECT * FROM TAB;**

**SQL> SELECT * FROM TAB;

TNAME
--------------------------------------------------------------------------------
TABTYPE        CLUSTERID
------------- ----------
CONTACTS
TABLE

COUNTRIES
TABLE

CUSTOMERS
TABLE
**

**SQL> SELECT * FROM ORDERS;

  ORDER_ID CUSTOMER_ID STATUS               SALESMAN_ID ORDER_DAT
---------- ----------- -------------------- ----------- ---------
         2           4 Shipped                          26-APR-15
         3           5 Shipped                          26-APR-17
         6           6 Shipped                          09-APR-15
         7           7 Shipped                          15-FEB-17
         8           8 Shipped                          14-FEB-17
         9           9 Shipped                          14-FEB-17
        10          44 Pending                          24-JAN-17
        11          45 Shipped                          29-NOV-16
        12          46 Shipped                          29-NOV-16
        13          47 Shipped                          29-NOV-16
        14          48 Shipped                          28-SEP-17
**
you should now be able to query the OT Schema sample tutorial Database.

**This example has been taken from Oracletutorial.com - Due Credit goes to them.**




