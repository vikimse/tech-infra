# tech-infra

Step-by-Step Guide to Set Up Jenkins on Ubuntu in VirtualBox

1. Download and Install VirtualBox
Visit the official VirtualBox website to download and install it on your host machine
https://www.virtualbox.org/wiki/Downloads

2. Download Ubuntu ISO 
Get the latest Ubuntu ISO file https://ubuntu.com/download/alternative-downloads or
Download Ubuntu 22.04.5 Desktop (64-bit)

3. Install Ubuntu in VM
Use the default VirtualBox user (vboxuser) and default password

4. Switch to root user and update system packages
su - 
sudo apt update  

5. Java is required for Jenkins
# Install the Java Runtime Environment (JRE)
sudo apt install default-jre
# Verify the Java version
java -version  
# Install the Java Development Kit (JDK)
sudo apt install default-jdk 
# Verify the JDK version
javac -version  

6. Install Jenkins
Run the following commands to add the Jenkins key and repository
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

# Update your package list
sudo apt update 
# Install Jenkins
sudo apt install jenkins -y  
# Enable Jenkins to start on boot
sudo systemctl enable jenkins
# Start Jenkins service
sudo systemctl start jenkins 
# Check Jenkins service status 
sudo systemctl status jenkins 

7. To access Jenkins from your host machine, you'll need to set up port forwarding in VirtualBox

8. To get the initial Jenkins admin password, use the following command
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

9. Access jenkins http://127.0.0.1:8080