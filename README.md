# Node.js To-Do List Application with Jenkins Integration

This project is a simple **To-Do List Application** built using **Node.js** and integrated with **Jenkins** to demonstrate Continuous Integration and Continuous Deployment (CI/CD) pipelines.

## Features

- **To-Do List Management**: Add, view, update, and delete tasks.
- **Jenkins Integration**:
  - Automates build, test, and deployment processes.
  - Demonstrates CI/CD pipeline for a Node.js application.
- **Modular Architecture**: Clean and scalable code structure.

## Tech Stack

- **Backend**: Node.js, Express.js
- **Build Automation**: Jenkins
- **Package Management**: npm
- **Version Control**: GitHub
- **Deployment**: Configurable for local or server-based environments.

## Prerequisites

Ensure you have the following installed:

1. [Node.js](https://nodejs.org/) (version 14+ recommended)
2. [npm](https://www.npmjs.com/)
3. [Jenkins](https://www.jenkins.io/)
4. Git

## Getting Started

### Create Ec2 instance 
* Create AWS EC2 instance
### Make changes for inbound traffic on Ec2
* Go to Ec2 instance and click on Security groups.
* Add inbound traffic as ALL traffic and save it.
* Add inbound traffic as ALL traffic for port 8000 and save it.
* Add inbound traffic as ALL traffic for port 8080 and save it.
### Install jenkins

```bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
```
```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
```bash
 sudo systemctl enable jenkins
 sudo systemctl start jenkins
 sudo systemctl status jenkins
```
* Initial password will store in this path.
```bash
 sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
* After setting up jenkins install Github integration plugin.
* Install the Github integration plugin in Jenkins:
* Log in to Jenkins.
* Go to Manage Jenkins > Manage Plugins.
* In the Available tab, search for "Github integration".
* Select the plugin and click the Install button.
* Restart Jenkins after the plugin is installed.
#### Integrating Jenkins with Github 
* Create new project in jenkins.
* Give the details of the github repository.
* Create a webhook in github so that github can communicate with jenkins.
* Add these commands in  Execute shell.
```bash
sudo apt install nodejs
sudo apt install npm
npm install
node app.js
```
#### Install docker 
```bash
sudo apt install docker.io
sudo usermod -a -G docker $USER
```
* Create a dockerfile
* Add this in Execute shell
```bash 
docker build . -t node-app-todo
docker run -d --name node-app-container -p 8000:8000 node-app-todo
```
* Now build the Jenkins project it should deploy the Todo-list application on
* http://[IPv4 address of Ec2 instance]:8000
