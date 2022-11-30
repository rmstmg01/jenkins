### Jenkins
Jenkins is an open source automation server which can be used to automate all the tasks related to building, testing, and delivering or deploying software or application.
Jenkins provides hundreds of plugins to support building, deploying and automating any project.

In this tutorial, we are going to install Jenkins on Ubuntu 22.04 LTS hosted on a cloud provider Linode.

### Prerequisites
Pre-Installed Ubuntu 22.04 
User with sudo privileges

### Jenkins installation steps
#### 1. Install Java
Jenkins is a jave based application, so it requires Java 8 or later version to run without any issues. To check if Java is installed on your system, run the command:
```
$ java --version
```
If Java is not installed on your system, you will get following output:

![1](https://user-images.githubusercontent.com/11027110/204740180-4a376233-f0ad-4cf2-b04e-6ebb51833764.jpg)

To install Java on your system, execute the command:
```
$ sudo apt install -y openjdk-17-jre-headless
```
After the installation, once again verify that Java is installed:
```
$ java --version
```
![2](https://user-images.githubusercontent.com/11027110/204740557-e9f0a0c1-8456-41a1-ae65-a08b646e7d14.jpg)

Now, we have Java installed and we can proceed for Jenkins installation.

#### 2. Install Jenkins via its official repo
Import the Jenkins GPG key from Jenkins repository with following command:
```
$ curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
```
Now, configure Jenkins repository to the sources list file using echo and tee command as below:
```
$ echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

Now, update the system’s package list with following command:
```
$ sudo apt update
```
And install Jenkins with following command:
```
$ sudo apt install -y jenkins
```
![3](https://user-images.githubusercontent.com/11027110/204742571-0428f3c6-a2f4-421b-8bd5-8443e9f934f9.jpg)

Once the installation is complete, Jenkins starts automatically. Run the following command to check the status:
```
$ systemctl status jenkins
```
![4](https://user-images.githubusercontent.com/11027110/204742988-67390021-6133-4282-9404-da3759738a01.jpg)

If Jenkins is not running for any reason, run following command to start it:
```
$ sudo systemctl start jenkins
```
#### 4. Configure firewall rules for Jenkins
Jenkins listens on port 8080 by default, so you need to make sure that port is opened in firewall. As ubuntu has UFW firewall, we need to run following command to allow port 8080 on ufw firewall:
```
$ sudo ufw allow 8080/tcp
```
Reload the firewall to effect the changes.
```
$ sudo ufw reload
```
To confirm that port 8080 is open on the firewall, run following command:
```
$ sudo ufw status
```
![5](https://user-images.githubusercontent.com/11027110/204744727-4c851ace-92ab-4abe-bee9-c30b9405db52.jpg)

We see that port 8080 is opened in firewall now.
#### 5. Setup Jenkins
Now, try to browse jenkins server IP/DNS name with port 8080 as below:
```
http://server-IP:8080
```
or
```
http://jenkins.ramesht.com.np:8080/
```
![6](https://user-images.githubusercontent.com/11027110/204765974-40fe2c48-3b9a-46ae-9f5c-5c76901980e5.jpg)

You will get  the page similar as shown above to provide the Administrator’s password. As per the instructions, the password is located in the file:
```
/var/lib/jenkins/secrets/initialAdminPassword
```
To view the password, run the following command:
```
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Copy the password and paste it in the text field as shown below and click the “Continue” button.
![7](https://user-images.githubusercontent.com/11027110/204768281-139cbc04-b44a-49ba-b044-c5d239fd1a6e.jpg)

In the next step, select ‘Install suggested plugin‘ for default installation.
![8](https://user-images.githubusercontent.com/11027110/204768601-18de1e62-8a79-41af-bf18-980cb0b5c3d4.jpg)

Thereafter, the installation of the necessary plugin required by Jenkins will start.
![9](https://user-images.githubusercontent.com/11027110/204768866-1db745c9-1ba9-4513-97e5-cc16b08924b3.jpg)

When the installation is complete, the installer will take you to the next section where you need to create an Admin user and click on the ‘Save and Continue’ button.
![10](https://user-images.githubusercontent.com/11027110/204769223-4bd0c23d-ca0d-4788-a894-25c6a64c672f.jpg)

The next step will populate the default URL for your Jenkins server. Just simply click ‘Save and Finish’.
![11](https://user-images.githubusercontent.com/11027110/204769560-3cc63d49-9606-42fa-8e26-693bb3f55743.jpg)

Finally, click on the ‘Start using Jenkins’ button to access the jenkins dashboard.
![12](https://user-images.githubusercontent.com/11027110/204769795-271e1d53-50f6-4293-810e-b910747cc2e6.jpg)

Then you will see Jenkins dashboard as shown below:
![13](https://user-images.githubusercontent.com/11027110/204770046-1afde179-c855-4a97-b0a1-544c25176157.jpg)

Finally, we have successfully installed jenkins on Ubuntu Server. 









