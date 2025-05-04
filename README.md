# Oracle
Tables :
----------
SQL Commands :


              DDL     -> DATA DEFINITION LANGUAGE
                          -CREATE , ALTER , DROP , FLASHBACK AND PURGE[ORACLE 10G] ,TTRUNCATE , RENAME
              DRL/DQL -> DATA RETRIEVAL LANGUAGE / DATA QUERY LANGUAGE 
                          -SELECT
              DML     -> DATA MANIPULATION LANGUAGE
                          -INSERT , UPDATE ,DELETE ,INSERT ALL AND MERGE[ORACLE 9I]
              TCL     -> TRANSACTION CONTROL LANGUAGE
                          -COMMIT , ROLLBACK ,SAVEPOINT
              DCL/ACL -> DATA CONTROL LANGUAGE/ACCESSING CONTROL LANGUAGE
                          -GRANT REVOKE


              Data Store=>
                          it is a location where we store the data.
                          ex:FILE,DB
              Database  =>
                          it ia a kind of data store with location and store organization's business data permanent
              DBMS      =>
                          It is like a Software to maintain the database safe and secure
              RDBMS     =>
                          It is like a Software to maintain database in the form of tables.

              Variable:  -it is temporary Storage.
              OBJECTS :  -it is temporary Storage.
              FILE    :  -it is permanent Storage.
              DATABASE:  -it is permanent Storage.

              FILE
              1.It is suitable for 1 user
              2.security is less
              3.it stores small amount of data
              
              DATABASE
              1.It is suitable for multiple users.
              2.security is high.
              3.It is suitable to store larger amounts of data

              📘 Evolution of DBMS (Database Management Systems)
              🕰️ Before 1960s
              📖 Data Storage: Physical Books, Paper records

              🕰️ 1960s
              💾 File Management Systems (FMS) introduced

                Data stored in flat files

                Example: Sequential, Indexed, and Direct Access Files

                🕰️ 1970s
                🌲 Hierarchical DBMS (e.g., IBM IMS – Info Management System)

                🔁 Network DBMS (e.g., CODASYL model)
                  → Uses complex pointers to represent relationships

                🧠 1976 – Game Changer
                👨‍🏫 Dr. E. F. Codd (IBM Scientist) introduced the Relational Model
                → Based on mathematical set theory & predicate logic
                → Gave birth to RDBMS (Relational DBMS)
                
                🚀 Oracle History
                Year	Milestone
                1977	💡 Larry Ellison, Bob Miner & Ed Oates founded Software Development Laboratories (SDL)
                1979	✅ First version of Oracle (v2) released (written in assembly language)
                1982	🔄 Company renamed to Relational Software Inc.
                1983	🔁 Final rename to Oracle Corporation and released Oracle v3 (in C language)



                🧾 RDBMS (Relational DataBase Management System)
                🏢 Company History
                Software Development Laboratories (SDL) → Founded by Larry Ellison & team

                Renamed to 👉 Relational Software Inc.

                Released: ✅ First version of ORACLE software

                Later renamed to 👉 Oracle Corporation

                📚 What is RDBMS?
                RDBMS stands for Relational Database Management System / Software

                It is a software used to create, manage, and manipulate databases in the form of tables.

                🔗 RDBMS Core Concept
                Term        	Meaning
                Relation    	Table
                Tuple	        Row
                Attribute    	Column

                🧰 Popular RDBMS Softwares & Their Companies
                RDBMS           Product	Developed By
                ---------------------------------
                Oracle           	Oracle Corporation
                SQL Server	      Microsoft
                DB2	              IBM
                PostgreSQL	      Postgre Forum
                MySQL	            Sun Microsystems (now Oracle)

               📝 Use of RDBMS:
                Store structured data in tables
                Define relationships using Primary/Foreign keys
                Enforce data integrity with constraints
                Support for SQL for querying and reporting

                Table (Relation / Entity):
                A table in a database is made up of rows and columns.
                It is also called a Relation or Entity.
                
                Column (Attribute / Property / Field):
                A column represents a particular attribute or property of the entity.
                It is a vertical representation of data.

                Row (Entity Instance / Tuple / Record):
                A row represents a single record or an instance of an entity in the table.
                It is a horizontal representation of data.

 Metadata:
             Metadata can be also called as "Data Definition".
             It is the data about the data.
             Example:
              Field Name, Table name, Data type, Field size


SQL:
           SQL => Structured Query Language.
           SQL is a query language.
           SQL is used to write the queries to communicate with ORACLE DB.
           QUERY => request / command / instruction
           QUERY is a request that is sent to DB SERVER.
           Example:
           SELECT ename, sal FROM emp;   => QUERY

 CREATE:
           CREATE command is used to create ORACLE DB Objects like tables, views, indexes, … etc

            Syntax to create the table:
               CREATE TABLE <table_name>
               (
               <column_name> <data_type> [,
               <column_name> <data_type> ,
              . 
              .]
               );
               [ ] Optional
               <> Any

                For WINDOWS OS,  latest version is: ORACLE 21C
                For LINUX OS, lest version is: ORACLE 23AI
                Till ORACLE 21C, we can create max of 1000 columns.
                In ORACLE 23AI, we can create max of 4096 columns.

                 Data Type tells,
                 •how much memory has to be allocated
                 •which type of data should be accepted


                 🔹 1. Character Data Types (Used for text)
                👉 These are used to store words, names, or any text.

                  Data Type            	      Description	                                    Example
                  CHAR(n)            	Fixed-size text (always uses n characters)	            'INDIA'
                  VARCHAR2(n)        	Variable-size text (up to n characters)	                'HYDERABAD'
                    LONG	            Very large text (older type, not recommended)	          'Details...'
                    CLOB	            Character Large Object (for huge texts)                	'Big content'
                  NCHAR(n)	          Fixed-size Unicode text (multi-language)	              'RAJU' (Unicode)
                  NVARCHAR2(n)	       Variable-size Unicode text	                             'TELANGANA' (Unicode)
                  NCLOB	               Large Unicode text	                                      'Unicode doc'

                ✅ Use VARCHAR2 for normal text.
                ✅ Use NCHAR or NVARCHAR2 for non-English languages (like Telugu, Hindi).

                🔹 2. Numeric / Integer Data Types (Whole numbers)
                👉 These store numbers without decimal points.

                Data Type	                Description                	   Example
                NUMBER(p)	                Number with total p digits    	12345
                INTEGER	                  Whole number	                  100
                INT	                      Same as INTEGER	                789

                🔹 3. Floating Point / Decimal Data Types (Decimal numbers)
                👉 These are for numbers with decimals.

                Data Type	                Description	                                Example
                NUMBER(p,s)	           Total p digits, with s after decimal	         15000.75
                FLOAT	                 Approximate decimal number	                     67.89
                BINARY_FLOAT	         Single-precision decimal number	               5.3
                BINARY_DOUBLE          Double-precision decimal number	               12000.00

                🔹 4. Date & Time Data Types
                👉 Used to store dates and timestamps.

                Data Type	                Description	                                Example
                DATE	                Date with time (up to seconds)	                25-DEC-23 or 25-DEC-23 10:30
                TIMESTAMP	            Date with fractional seconds	                  11-JUL-24 10:30:15.123456 AM
                INTERVAL	            Time difference (between two dates/times)	       5 days 3 hours

                🔹 5. Binary Data Types
                👉 Used for non-text data like files, images, audio, or videos.

                Data Type	                      Description	                             Example
                BLOB	                           Binary Large Object	                Image, video
                BFILE	                           File stored outside the database	    File reference
                RAW(n)	                         Binary data of n bytes	              Encoded data

                🧠 ASCII vs Unicode (Character storage types)
                ASCII = Stores only English characters (1 byte per character).

                Unicode = Supports English + other languages (e.g., Telugu, Hindi).


                🔹 1. CHAR(n)
                Used to store string values (text).

                n = Maximum number of characters.

                It stores fixed-length text.

                If the value is less than n, remaining space is filled with blank spaces.

                It is a fixed-length data type.

                ✅ Maximum size: 2000 bytes (or 2000 characters).

                ✅ Default size: 1 character if not mentioned.

                🔸 Example:
                |sql>CHAR(10)|
                If you insert 'RAM', it will store 'RAM ' (7 spaces after RAM).

                🔹 2. VARCHAR2(n)
                Also used to store string values.

                n = Maximum number of characters allowed.

                It stores variable-length text.

                Only stores exact characters given — no extra spaces added.

                It is a variable-length data type.

                ✅ Maximum size: 4000 bytes (or 4000 characters).

                ❌ No default size — you must specify the length.

                🔸 Example:
                sql>VARCHAR2(10)
                If you insert 'RAM', it stores exactly 'RAM' — no extra spaces.




           
Built-In Functions:
                    String Functions
                    Conversion
                    Date
                    Analytic
                    Number
                    Aggregate
                    special

Clauses:
                    GROUP BY
                    HAVING
                    ORDER BY
                    FETCH

Joins:
                    🔸 Inner Join (Equi & Non-Equi)

                    🔸 Left, Right, Full Outer Joins

                    🔸 Outer Join

                    🔸 Self Join

                    🔸 Cross Join

Sub Queries:
                      Non-Correlated 
                       Single Row SQ
                       Multi Row SQ
                       Inline View
                       Scalar
                       Correlated

Constraints:
                        Primary Key
                        Foreign Key
                        Check

Set Operators:
                        Union
                        Union All
                        Intersects
                        minus


VIEWS:
INDEXES:
SEQUENCES:
SYNONYMS:
MATERIALIZED VIEWS:
