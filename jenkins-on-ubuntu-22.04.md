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


