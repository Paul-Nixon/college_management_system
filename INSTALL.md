# **Installation**
* [Java JDK 12.0.1 and Apache NetBeans 12.0](#java-jdk-12.0.1-and-apache-netbeans-12.0)
* [MySQL Download and Setup](#mysql-download-and-setup)
* [Connecting NetBeans to the MySQL Database](#connecting-netbeans-to-the-mysql-database)
  * [Importing My NetBeans Project](#importing-my-netbeans-project)
  * [Importing My MySQL Schema](#importing-my-mysql-schema)
  * [Connecting the NetBeans Project to the MySQL Schema](#connecting-the-netbeans-project-to-the-mysql-schema)<br></br>

# **Java JDK 12.0.1 and Apache NetBeans 12.0**
1. Download and install [Java JDK 12.0.1](https://www.oracle.com/java/technologies/javase/jdk12-archive-downloads.html)
2. Download and install [Apache NetBeans 12.0](https://netbeans.apache.org/download/nb120/nb120.html)<br></br>

# **MySQL Download and Setup**
1. Download and install [MySQL Installer 8.0.22](https://dev.mysql.com/downloads/windows/installer/8.0.html)
2. PLEASE [watch this video](https://www.youtube.com/watch?v=2Qi3b_Qu4Xo) while installing MySQL because doing so can easily get confusing. The following screenshot is what I currently have installed. Make sure you at least have everything except MySQL Notifier, MySQL for Excel, Connector/C++, and Connector/NET (you can download them later if desired).<br></br>
![Screenshot of my installed MySQL products](https://user-images.githubusercontent.com/42850145/100280255-78b39180-2f2d-11eb-8789-6e49d8f04114.PNG)

3. Open MySQL Workbench & click the plus icon next to MySQL Connections to create a new connection. If you want, change the connection name, username, and password to whatever you prefer, but always remember you can modify them by right-clicking the connection -> Edit Connection.<br></br>
![Image of MySQL Workbench home screen](https://user-images.githubusercontent.com/42850145/100280633-1d35d380-2f2e-11eb-9ca9-e0ffadff03c8.PNG)<br></br>
![Image of right-clicking a connection -> Edit Connection](https://user-images.githubusercontent.com/42850145/100280801-5ff7ab80-2f2e-11eb-8e74-3e0b21b2dc22.PNG)<br></br>

# **Connecting NetBeans to the MySQL Database**

## **Importing My NetBeans Project**
1. Download [my NetBeans project zip file](https://github.com/Paul-Nixon/college_management_system/blob/main/college_management_system_mysql_workbench_export.zip)
2. Open NetBeans -> File -> Import Project -> From ZIP -> Browse button next to the ZIP File text field -> Search for and click the downloaded ZIP file -> Import. Note that the Folder text field shows where the project will be saved.<br></br>
![Image of importing a ZIP file in NetBeans](https://user-images.githubusercontent.com/42850145/100280981-abaa5500-2f2e-11eb-990a-e7e27be2ca87.PNG)<br></br>

## **Importing My MySQL Schema**
1. Download [my MySQL schema](https://github.com/Paul-Nixon/college_management_system/blob/main/college_management_system_mysql_workbench_export.zip)
2. Open MySQL Workbench -> The new connection you created earlier -> Startup / Shutdown -> Start Server -> Refresh Status (you may or may not need to click the button more than once to ensure a connection has been estalished; The Information box in the bottom left corner should display the connection details)<br></br>
![Image of starting a MySQL Server](https://user-images.githubusercontent.com/42850145/100281163-02b02a00-2f2f-11eb-96a6-33662086a5ed.PNG)  

3. Schemas (label next to Administration) -> Right-click -> Create Schema -> Change the name (I recommend college_management_system) -> Change the charset to "ascii" -> Apply (click it again when the Apply SQL Script to Database window appears) -> Finish<br></br>
![Image of creating a new schema](https://user-images.githubusercontent.com/42850145/100281364-5fabe000-2f2f-11eb-80a5-a2bd5bb955f1.PNG)  

4. Administration -> Data Import/Restore -> Import from Self-Contained File -> Click the button next to the text field, search for the downloaded schema, and click one of the SQL/dump files -> Click the Default Target Schema drop-down box and select the schema you just created -> Import Progress -> Start Import -> Import the remaining files. The schema will now include each of the tables from their respective files.<br></br>
![Image of importing data in MySQL Workbench](https://user-images.githubusercontent.com/42850145/100281539-b9140f00-2f2f-11eb-9e5a-8a7470aef232.PNG)

## **Connecting the NetBeans Project to the MySQL Schema**  
1. Open the NetBeans project (if you haven't already) -> Scroll down the Projects tab -> Right-click Libraries -> Add JAR/Folder. On Windows, the path to the MySQL Connector/J JAR file is the following: Windows (C:) -> Program Files (x86) -> MySQL -> Connector J 8.0 (if you know the respective paths on Mac and Linux, post them as an [issue](https://github.com/Paul-Nixon/college_management_system/issues). When you find the file, click it -> Open. The driver enables the project to connect to the database server.<br></br>
![Image of the Add JAR/Folder window in NetBeans](https://user-images.githubusercontent.com/42850145/100281853-4192af80-2f30-11eb-991b-f8f40f9118d3.PNG)<br></br>
![Image of the MySQL Connector/J JAR file in Libraries](https://user-images.githubusercontent.com/42850145/100281732-160fc500-2f30-11eb-94d6-6284e36c712b.PNG)<br></br>

2. Services -> Right-click Databases -> Register MySQL Server. In the Basic Properties tab, ensure the server hostname and port number & admin username and password are the same as the MySQL connection you created earlier (if you're confused, on the MySQL Workbench home screen, the admin username is just below the connection name; the server hostname is left of the colon; the server port number is right of the colon; if you forgot the password, remember you can change it by right-clicking the connection -> Edit Connection).<br></br>
![Image of a MySQL connection's info](https://user-images.githubusercontent.com/42850145/100282028-861e4b00-2f30-11eb-9c63-32f812e9a62c.PNG)<br></br>

3. Click the Admin Properties tab. Click the Browse button next to the Path/URL to admin tool text field, follow the following path: Windows (C:) -> Program Files -> MySQL -> MySQL Server 8.0 -> bin, and click the "mysqladmin" app. Click the Browse button next to the Path to start command text field, follow the previous path, and click the "mysqld" app. Click the Browse button next to the Path to stop command text field, click the "mysqladmin" app again, and, in the Arguments field, type -u root stop. When finished, the Admin Properties tab should resemble the following figure. Click OK when you're satisfied.<br></br>
![Image of a finished Admin Properties tab](https://user-images.githubusercontent.com/42850145/100282394-1fe5f800-2f31-11eb-9673-fa14e31b06b7.PNG)<br></br>

4. Left-click Databases -> Right-click the MySQL Server node -> Start -> Enter the password to the MySQL connection -> OK. The server is now connected to the project. Note that the server needs to be running for this to work, and you will need to repeat this step every time you open NetBeans.<br></br>
![Image of the project not being connected to the MySQL Server](https://user-images.githubusercontent.com/42850145/100282555-74897300-2f31-11eb-9f26-3e91d89f4cc4.PNG)<br></br>
![Image of MySQL Server Properties window](https://user-images.githubusercontent.com/42850145/100282686-ad294c80-2f31-11eb-94f6-3a598cdccb2f.PNG)<br></br>
![Image of MySQL Server being connected to the NetBeans project](https://user-images.githubusercontent.com/42850145/100282724-bc0fff00-2f31-11eb-9db6-a212ba961edd.PNG)<br></br>

5. Projects -> databaseConnection.java. In the try block, the second statement needs to be slightly modified so the JFrame forms can access and modify the schema you created earlier in your MySQL connection. Here's how it should be changed:
```java
Connection conn = DriverManager.getConnection("jdbc:mysql://localhost/*insert schema name here*", "*insert admin username here*", "*insert admin password here*")
```
When you run the project, JFrame forms that need to access the schema will now be able to do so.
