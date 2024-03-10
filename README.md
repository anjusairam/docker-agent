# used docker as agent in jenkins 

the installation of Jenkins on an EC2 instance, configuration of security groups, initial setup of Jenkins, installation of suggested plugins, creation of an admin user, and installation of the Docker Pipeline plugin.

Here's a breakdown of the steps provided:

1. **Installation on EC2 Instance:**
   - Launch an EC2 instance on AWS.
   - Install Java (JDK) and Jenkins on the EC2 instance.
   - Open port 8080 in the security group to allow access to Jenkins.
     Install Jenkins.

Pre-Requisites:

Java (JDK)
Run the below commands to install Java and Jenkins
Install Java

sudo apt update
sudo apt install openjdk-11-jre
Verify Java is Installed

java -version

2. **Login to Jenkins:**
   - Access Jenkins using the EC2 instance's public IP address and port 8080.
   - Retrieve the initial admin password from the EC2 instance.
   - Complete the Jenkins setup by creating an admin user or skipping the step.

     Now, you can proceed with installing Jenkins

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

3. **Install Docker Pipeline Plugin:**
   - Log in to Jenkins.
   - Navigate to Manage Jenkins > Manage Plugins.
   - Search for and install the Docker Pipeline plugin.
   - Restart Jenkins after plugin installation.

     Log in to Jenkins.
Go to Manage Jenkins > Manage Plugins.
In the Available tab, search for "Docker Pipeline".
Select the plugin and click the Install button.
Restart Jenkins after the plugin is installed.


4. **Docker Slave Configuration:**
   - Install Docker on the EC2 instance.
   - Grant Jenkins and Ubuntu users permission to access the Docker daemon.
   - Restart Docker and Jenkins to apply the changes.


     Run the below command to Install Docker

sudo apt update
sudo apt install docker.io
Grant Jenkins user and Ubuntu user permission to docker deamon.
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker
Once you are done with the above steps, it is better to restart Jenkins.

http://<ec2-instance-public-ip>:8080/restart
     

