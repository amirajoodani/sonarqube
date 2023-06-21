# sonarqube
SonarQube is a Code Quality Assurance tool that collects and analyzes source code, and provides reports for the code quality of your project. It combines static and dynamic analysis tools and enables quality to be measured continually over time.
![sonarqube](https://github.com/amirajoodani/sonarqube/assets/42912741/866eb455-2891-4382-80ce-a60206b80124)

# How to run sonarqube with docker ? 
```
docker run -d -p 9000:9000 -p 9092:9092 sonarqube
```
# how to login to web ui ?
open sonarqube, by copying url below to your browser and use username and password as mentioned below <br>

http://localhost:9000 <br>

Username … admin <br>

Password … admin <br>

![sonarqube1](https://github.com/amirajoodani/sonarqube/assets/42912741/485f7f3e-eaef-4072-a9b1-5e029c4dd79a)

# how to scan django code with sonarqube ?
first we download scanner : <br> 
```
mkdir /downloads/sonarqube -p
cd /downloads/sonarqube
wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.2.0.1873-linux.zip
unzip sonar-scanner-cli-4.2.0.1873-linux.zip
mv sonar-scanner-4.2.0.1873-linux /opt/sonar-scanner
```
Edit the sonar-scanner.properties file: <br>
```
vi /opt/sonar-scanner/conf/sonar-scanner.properties
```
Configure the Sonarqube scanner to connect to your Sonarqube server: <br>
```
sonar.host.url=http://localhost:9000
sonar.sourceEncoding=UTF-8
```
We need to add the sonar-scanner command to the PATH variable.Let’s create a file to automate the required environment variables configuration : <br>
```
vi /etc/profile.d/sonar-scanner.sh
```
Here is the sonar-scanner.sh file content : <br>
```
#/bin/bash
export PATH="$PATH:/opt/sonar-scanner/bin"
```
![sonarqube2](https://github.com/amirajoodani/sonarqube/assets/42912741/5d4f9907-70b0-4d52-8c3e-e6bcddd3c3b3)

source command to add the sonar scanner command to the PATH variable: <br>
```
source /etc/profile.d/sonar-scanner.sh
```
Use the following command to verify if the PATH variable was changed as expected.<br>
```
env | grep PATH
```
Here is the command output: <br>
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/opt/sonar-scanner/bin
```
In our example, the /opt/sonar-scanner/bin directory was added to the PATH variable.Use the following to verify the Sonarqube scanner version installed.<br>
```
sonar-scanner -v
```
![sonarqube3](https://github.com/amirajoodani/sonarqube/assets/42912741/e92eb540-b5a3-4676-ae9c-d3c974344b0d)

Create a new project and token .In our example, we are going to analyse a popular open source project named: Django-blog <br>
![sonarqube4](https://github.com/amirajoodani/sonarqube/assets/42912741/a5937932-0bc6-4ccd-a5da-cc6640a0d3a6)

On the Next screen, select your project language.In our example, we selected the option: Other (JS, TS, Go, Python, PHP, ...) <br>

![sonarqube5](https://github.com/amirajoodani/sonarqube/assets/42912741/8a605421-057d-411d-99c3-be60d4df9860)

The system will show you the command-line that you should use to scan the Django-blog project.

go to the directory of your project and run that sonarqube gives you . it takes time to doing scan  : <br>
![sonarqube6](https://github.com/amirajoodani/sonarqube/assets/42912741/b2605a87-5393-46f2-a83e-a5b4d45e4967)
after a while you can see the result in web console: <br>
![sonarqube7](https://github.com/amirajoodani/sonarqube/assets/42912741/7dfdd2b5-8b84-49cc-a65c-b01649c2a084)






















