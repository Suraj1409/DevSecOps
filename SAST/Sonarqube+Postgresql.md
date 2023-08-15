Increase the vm.max_map_count kernal ,file discriptor and ulimit for current session at runtime.

    sudo sysctl -w vm.max_map_count=262144
    sudo sysctl -w fs.file-max=65536
    ulimit -n 65536
    ulimit -u 4096

To Increase the vm.max_map_count kernal ,file discriptor and ulimit permanently . 
Open the below config file and Insert the below value as shown below,

    sudo nano /etc/security/limits.conf
    
    sonarqube   -   nofile   65536
    sonarqube   -   nproc    4096

Before installing, Lets update and upgrade System Packages

    sudo apt-get update
    sudo apt-get upgrade

Install wget and unzip package

    sudo apt-get install wget unzip -y

Step #1:Install OpenJDK 17 on Ubuntu 20.04 LTS
Install OpenJDK and JRE 11 using following command,

    sudo apt-get install openjdk-17-jdk -y
    sudo apt-get install openjdk-17-jre -y

SET Default JDK

To set default JDK or switch to OpenJDK enter below command,

    sudo update-alternatives --config java

You will see below choices for the alternative java (providing /usr/bin/java).
Type Index of version number to confirm

Check JAVA Version:

    java -version

Step #2: Install and Setup PostgreSQL 10 Database For SonarQube
Add and download the PostgreSQL Repo
    
    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'
    wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | sudo apt-key add -

Install the PostgreSQL database Server by using following command,

    sudo apt-get -y install postgresql postgresql-contrib

Start PostgreSQL Database server

    sudo systemctl start postgresql

Enable it to start automatically at boot time.
    
    sudo systemctl enable postgresql

Change the password for the default PostgreSQL user.
    
    sudo passwd postgres

Switch to the postgres user.

    su - postgres

Create a new user by typing:

    createuser sonar

Switch to the PostgreSQL shell.

    psql

Set a password for the newly created user for SonarQube database.

    ALTER USER sonar WITH ENCRYPTED password 'sonar';
    Create a new database for PostgreSQL database by running:
    CREATE DATABASE sonarqube OWNER sonar;
    grant all privileges to sonar user on sonarqube Database.
    grant all privileges on DATABASE sonarqube to sonar;
    \q

Switch back to the sudo user by running the exit command.

    exit
