# To Install OWASP-ZAP (Zed Attack Proxy)

## Update and Upgrade:
Start by updating and upgrading package lists to ensure you have the latest package information.

    sudo apt update
    sudo apt upgrade -y


## Install Java:
OWASP ZAP requires Java to run. Install OpenJDK with the following command:

    sudo apt install openjdk-11-jre-headless -y


## Download and Install OWASP ZAP:
You can download and install OWASP ZAP using the following steps:
 - Download the latest OWASP ZAP package:

       wget https://github.com/zaproxy/zaproxy/releases/download/v2.13.0/ZAP_2.13.0_Linux.tar.gz

- Extract the downloaded package:

      tar -xzf ZAP_2.13.0_Linux.tar.gz

- Move the extracted directory to a suitable location (e.g., `/opt`):

      sudo mv ZAP_2.13.0 /opt/


## Create a Desktop Shortcut (Optional):
You can create a desktop shortcut for ZAP for easy access:

- Create a `.desktop` file:

      echo -e '[Desktop Entry]\nVersion=1.0\nName=OWASP ZAP\nExec=/opt/ZAP_2.13.0/zap.sh\nIcon=/opt/ZAP_2.13.0/zap.ico\nTerminal=false\nType=Application\nCategories=Utility;Application;' | sudo tee /usr/share/applications/zap.desktop

- Make the `.desktop` file executable:

      sudo chmod +x /usr/share/applications/zap.desktop
     
## Run OWASP ZAP:
You can now launch OWASP ZAP by searching for it in your applications menu or by using the terminal:

    /opt/ZAP_2.13.0/zap.sh

