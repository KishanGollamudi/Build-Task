# 🚀 Java Web Application: Build & Deploy Guide (Java 17 + Maven + Tomcat)

## Overview
This project is a **Java Web Application** designed to run on **Java 17**, built using **Maven**, and deployed on **Apache Tomcat**. The project demonstrates a basic Java web app structure, with a simple calculator implementation.

## Project Structure

JavaWebCalculator/
├── pom.xml
├── src/
│ ├── main/
│ │ ├── java/mypackage/Calculator.java
│ │ └── webapp/
│ │ ├── WEB-INF/web.xml
│ │ └── index.jsp
│ └── test/java/mypackage/CalculatorTest.java


- **pom.xml**: Maven project configuration.
- **Calculator.java**: Java class for your calculator logic.
- **index.jsp**: The homepage of the web application.
- **web.xml**: Web application configuration.
- **CalculatorTest.java**: Unit tests for the calculator.

## Prerequisites

### Step 1: Install Java 17

To install Java 17, run the following commands (for Ubuntu/Debian):

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```
java -version
# Output should be something like:
# openjdk version "17.0.x"...

Install Maven
```bash
sudo apt install maven -y
```
Verify Maven installation
```bash
mvn -v
```

Install Apache Tomcat
```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.110/bin/apache-tomcat-9.0.110.tar.gz
tar -xvzf apache-tomcat-9.0.110.tar.gz
```
Add Tomcat User for Manager Access
```bash
sudo vi tomcat/conf/tomcat-users.xml
```
Add the following inside <tomcat-users>
```bash
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<user username="admin" password="admin123" roles="manager-gui,manager-script"/>
```
Edit the context.xml file to allow remote access
```bash
sudo vi tomcat/webapps/manager/META-INF/context.xml
```
Comment out the IP restriction
```bash
<!--
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
       allow="127\.\d+\.\d+\.\d+|::1" />
-->
```
Update pom.xml for Java 17 is available in the pom.xml file in this repository

## Clean and Package the Application
### Navigate to your project directory
```bash
cd JavaWebCalculator
```
### Run the following Maven command to clean and package your application
```bash
mvn clean package
```

## Deploy the WAR to Apache Tomcat
### Option 1: Deploy via Manager Web Interface

### Go to: http://localhost:8080/manager/html

### Login using your admin/admin123 credentials.

### In the Deploy section, upload the .war file: target/webapp-0.2.war.

### Click Deploy.

## Deploy the WAR to Apache Tomcat
Transfer the WAR File to the Deploy Server

To copy the .war file from the build server to the deploy server, use WinSCP and PuTTY to transfer the .pem file and then use scp to copy the .war file.

Use WinSCP and PuTTY to upload the .pem file to your deploy server.

On the build server, use the following scp command to copy the .war file to the deploy server
```bash
scp -i git.pem /home/ubuntu/JavaWebCalculator/target/*.war ubuntu@3.231.144.26:/home/ubuntu/apache-tomcat-9.0.110/webapps/
```
## Test the Application
Open your browser and visit:

http://localhost:8080/webapp-0.2

You should see the index.jsp page of your web application.
## Screenshots
<img width="1078" height="690" alt="Image" src="https://github.com/user-attachments/assets/1605f858-af07-4aa4-b41c-c820c0f8c7f2" />
<img width="1040" height="463" alt="Image" src="https://github.com/user-attachments/assets/0cf8aed2-8823-4c3c-b173-01d76a9a29db" />
<img width="830" height="182" alt="Image" src="https://github.com/user-attachments/assets/6385cc16-f433-4e10-a345-558fa4ab6335" />
<img width="1649" height="303" alt="Image" src="https://github.com/user-attachments/assets/ad113e8b-4641-45fa-811c-6d65f63a85e9" />
<img width="765" height="245" alt="Image" src="https://github.com/user-attachments/assets/3e76b63e-d138-4c55-8eb7-885da2e9641e" />
<img width="1582" height="267" alt="Image" src="https://github.com/user-attachments/assets/8218917a-34f8-4538-80eb-26bcea013fff" />
<img width="1585" height="289" alt="Image" src="https://github.com/user-attachments/assets/c38fe332-e58e-48fa-85b6-fbf965c7b8ab" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/b730b12c-629c-4dbb-b4a0-42de4a6d0c82" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/90d90c9a-2a20-4bea-a81e-1ac00e839d28" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/dd3946c4-d4da-49ff-8c58-1b67222e0f14" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/07c81dab-72ff-4d57-a292-898811980321" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/a8901530-6286-4645-ad39-a4237d5cee3e" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/33b448d0-a807-4670-b744-404aa2ba6dff" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/e9ac6d65-7b00-4973-8b0d-09f119ddebc6" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/1054b9eb-9f99-44a7-9ef2-c83e9f8df908" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/5dabb767-d7b4-4820-b602-7af67321f434" />
<img width="1302" height="409" alt="Image" src="https://github.com/user-attachments/assets/f355d8d9-027b-471e-a73e-ff4376d6204f" />
<img width="1662" height="264" alt="Image" src="https://github.com/user-attachments/assets/1638d23a-55e1-4131-a8a6-860ba652f68e" />
