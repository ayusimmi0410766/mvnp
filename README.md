mvn archetype:generate -DgroupId=com.example -
DartifactId=myapp -DarchetypeArtifactId=maven-archetypequickstart -DinteractiveMode=false
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
http://maven.apache.org/xsd/maven-4.0.0.xsd">
 <modelVersion>4.0.0</modelVersion>
 <groupId>com.example</groupId>
 <artifactId>myapp</artifactId>
 <version>1.0-SNAPSHOT</version>
 <dependencies>
 <!-- JUnit Dependency for Testing -->
 <dependency>
 <groupId>junit</groupId>
 <artifactId>junit</artifactId>
 <version>4.13.2</version>
 <scope>test</scope>
 </dependency>
 </dependencies>
 <build>
 <plugins>
 <!-- Maven Surefire Plugin for running tests -->
 <plugin>
 <groupId>org.apache.maven.plugins</groupId>
 <artifactId>maven-surefire-plugin</artifactId>
 <version>2.22.2</version>
 <configuration>
 <redirectTestOutputToFile>false</redirectTestOutputToFile>
 <useSystemOut>true</useSystemOut>
 </configuration>
 </plugin>
 </plugins>
 </build>
</project>
package com.example;
public class App {
 public int add(int a, int b) {
 return a + b;
 }
 public static void main(String[] args) {
 App app = new App();
 int result = app.add(2, 3);
 System.out.println("2 + 3 = " + result);
 System.out.println("Application executed
successfully!");
 }
}
package com.example;
import org.junit.Assert;
import org.junit.Test;
public class AppTest {
 @Test
 public void testAdd() {
 App app = new App();
 int result = app.add(2, 3);
 System.out.println("Running test: 2 + 3 = " + result);
 Assert.assertEquals(5, result);
 }
}
mvn compile
mvn test 
mvn package 
  exper 3-------------
  gradle init --type java-applicationgradle 
  plugins {
 kotlin("jvm") version "1.8.21"
 application
}
repositories {
 mavenCentral()
}
dependencies {
 implementation(kotlin("stdlib"))
 testImplementation("junit:junit:4.13.2")
}
application {
 mainClass.set("com.example.MainKt")
}
tasks.test {
 useJUnit()
 testLogging {
 events("passed", "failed", "skipped")
 exceptionFormat =
org.gradle.api.tasks.testing.logging.TestExceptionFormat.FULL
 showStandardStreams = true
 }
 outputs.upToDateWhen { false }
}
java {
 toolchain {
 languageVersion.set(JavaLanguageVersion.of(17))
 }
}
package com.example
fun addNumbers(num1: Double, num2: Double): Double {
 return num1 + num2
}
fun main() {
 val num1 = 10.0
 val num2 = 5.0
 val result = addNumbers(num1, num2)
 println("The sum of $num1 and $num2 is: $result")
 package com.example
import org.junit.Assert.*
import org.junit.Test
class MainTest {
 @Test
 fun testAddNumbers() {
 val num1 = 10.0
 val num2 = 5.0
 val result = addNumbers(num1, num2)
 assertEquals("The sum of $num1 and $num2 should be 15.0", 15.0,
result, 0.001)
 }
}

gradle build
gradle test gradle run
plugins {
 id 'application'
}
application {
 mainClass = 'com.example.AdditionOperation'
}
repositories {
 mavenCentral()
}
dependencies {
 testImplementation 'junit:junit:4.13.2'
}
test {
 outputs.upToDateWhen { false }
 
 testLogging {
 events "passed", "failed", "skipped"
 exceptionFormat "full"
 showStandardStreams=true
 }
 }
 package com.example;
public class AdditionOperation {
 public static void main(String[] args) {
 double num1 = 5;
 double num2 = 10;
 double sum = num1 + num2;
 System.out.printf("The sum of %.2f and
%.2f is %.2f%n", num1, num2, sum);
 }
}
package com.example;
import org.junit.Test;
import static org.junit.Assert.*;
public class AdditionOperationTest {
 @Test
 public void testAddition() {
 double num1 = 5;
 double num2 = 10;
 double expectedSum = num1 + num2;
 double actualSum = num1 + num2;
 assertEquals(expectedSum, actualSum,
0.01);
 }
experiment 4-------------------------
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchemainstance"

xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
http://maven.apache.org/xsd/maven-4.0.0.xsd">
 <modelVersion>4.0.0</modelVersion>
 <groupId>com.example</groupId>
 <artifactId>maven-example</artifactId>
 <version>1.0-SNAPSHOT</version>
 <dependencies>
 <dependency>
 <groupId>junit</groupId>
 <artifactId>junit</artifactId>
 <version>4.12</version>
 <scope>test</scope>
 </dependency>
 </dependencies>
 <build>
 <plugins>
 <plugin>
 <groupId>org.apache.maven.plugins</groupId>
 <artifactId>maven-compiler-plugin</artifactId>
 <version>3.8.1</version>
 <configuration>
 <source>1.8</source>
 <target>1.8</target>
 </configuration>
 </plugin>
 </plugins>
 </build>
</project>
package com.example;
public class App {
 public static void main(String[] args) {
 System.out.println("Hello, Maven");
 System.out.println("This is the simple realworld
example....");
 int a = 5;
 int b = 10;
 System.out.println("Sum of " + a + " and " + b + " is "
+ sum(a, b));
 }
 public static int sum(int x, int y) {
 return x + y;
 }
}
mvn clean install
mvn exec:java -Dexec.mainClass="com.example.App"
gradle init
plugins {
 id 'java'
}
group = 'com.example'
version = '1.0-SNAPSHOT'
repositories {
 mavenCentral()
}
dependencies {
 testImplementation 'junit:junit:4.12'
}
task run(type: JavaExec) {
 main = 'com.example.App'
 classpath = sourceSets.main.runtimeClasspath
}
gradle --refresh-dependencies
>gradle build --no-configuration-cache
gradle build 
gradle run
exp 6-----
clean compile test package
exp7------------------------
Windows feature on or off
Click on windows subsystem
linux
wsl --list --online
wsl --install --distribution Ubuntu24.04
wsl
sudo apt update
sudo apt install ansible -y
ssh-keygen
mkdir ansible-localhost
cd ansible-localhost
nano hosts.ini
[local]
localhost ansible_connection=local
ansible all -i hosts.ini -m ping
- name: Install and run nginx on localhost
 hosts: local
 become: yes
 tasks:
 - name: Install nginx
 apt:
 name: nginx
 state: present
 update_cache: yes
 - name: Start nginx
 service:
 name: nginx
 state: started
 enabled: yes
 nano
index.html

index.html
<!DOCTYPE html>
<html>
<head>
 <title>My Custom Nginx Page</title>
</head>
<body>
 <h1> Hello from Ansible!</h1>
 <p>This is a custom web page deployed using
Ansible!</p>
</body>
</html>
---
- name: Install and run nginx on localhost
 hosts: localhost
 become: yes
 tasks:
 - name: Install nginx
 apt:
 name: nginx
 state: present
 update_cache: yes
 - name: Copy custom index.html
 copy:
 src: index.html
 dest: /var/www/html/index.html
 owner: www-data
 group: www-data
 mode: '0644'
 - name: Start nginx service
 service:
 name: nginx
 state: started
 enabled: yes
 ansible
playbook -i hosts.ini ansible.yml
exp8----------------------------------------------------
sudo apt update
 -> sudo apt install ansible -y
 * Create Ansible files in WSL
 mkdir Ansible-lab
 cd Ansible-lab
 sudo apt
install default-jdk -y
java --version
 nano
inventory.ini
[local]
localhost ansible_connection=local
deploy.yml
- name: Deploy JAR from Ansible Jenkins
 hosts: local
 become: true
 tasks:
 - name: Copy JAR from Jenkins workspace
 copy:
 src:
/mnt/c/ProgramData/Jenkins/.jenkins/workspace/JENKINSPR
OJECT/target/myapp-1.0-SNAPSHOT.jar
 dest: /home/itishree/ansible-deploy/myapp-1.0-
SNAPSHOT.jar # Changed destination path
 mode: 0755
 - name: Run JAR in Background
 shell: nohup java -jar /home/itishree/ansibledeploy/myapp-1.0-SNAPSHOT.jar > app.log 2>&1 &
 ansibleplaybook -i inventory.ini deploy.yml --ask-become-pass
 <?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- Project Identification -->
    <groupId>com.example</groupId>
    <artifactId>myapp</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <name>My Application</name>
    <url>http://maven.apache.org</url>

    <!-- Properties -->
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <!-- Dependencies -->
    <dependencies>
        <!-- JUnit Dependency for Testing -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <!-- Build Configuration -->
    <build>
        <plugins>
            <!-- Compiler Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>${maven.compiler.source}</source>
                    <target>${maven.compiler.target}</target>
                </configuration>
            </plugin>

            <!-- JAR Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.2.0</version>
                <configuration>
                    <archive>
                        <manifest>
                            <addClasspath>true</addClasspath>
                            <mainClass>com.example.App</mainClass>
                        </manifest>
                    </archive>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
$ cat app.log
