## Connect to your EC2 Instance:

Replace your-instance-ip with the actual public IP address or DNS name of your EC2 instance, and use the appropriate path to your private key file (your-key.pem)

    ssh -i /path/to/your-key.pem ubuntu@your-instance-ip

## Update Packages:

Update the package list and upgrade the installed packages to their latest versions

    sudo apt update
    sudo apt upgrade

## Install Java:

Jenkins requires Java to run. Install OpenJDK 11

    sudo apt install openjdk-11-jdk

## Add Jenkins Repository:

Jenkins provides its own repository for easier installation and updates. Add the Jenkins repository and its GPG key

    wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
    sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

## Install Jenkins:

Update the package list again and install Jenkins

    sudo apt update
    sudo apt install jenkins

## Start Jenkins Service:

Start the Jenkins service
  
    sudo systemctl start jenkins

## Enable Jenkins to Start on Boot:

Enable the Jenkins service to start on system boot

    sudo systemctl enable jenkins

## Open Firewall Port:

Allow incoming traffic on port 8080 (default Jenkins port) through the firewall

    sudo ufw allow 8080
    
## Access Jenkins Web UI:

Open a web browser and navigate to http://your-instance-ip:8080. You should see the Jenkins setup wizard. Retrieve the initial admin password by running:

    sudo cat /var/lib/jenkins/secrets/initialAdminPassword
    
Copy the password and paste it into the Jenkins setup wizard to proceed.

## Install Recommended Plugins:

In the Jenkins setup, choose the option to install recommended plugins. This will install the necessary plugins for basic functionality.

Create Admin User:
Create an admin user account with your desired credentials.

Finish Setup:
Follow the remaining steps in the setup wizard to complete the installation.

Jenkins should now be installed and running on your AWS EC2 instance. You can configure Jenkins jobs and manage your CI/CD workflows through the Jenkins web interface.



