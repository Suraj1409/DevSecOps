## Install Docker on Ubuntu:

1. **Update Package Repository:**
   Update the package repository on your Ubuntu system.
   ```bash
   sudo apt update
   ```

2. **Install Required Packages:**
   Install the packages necessary to add repositories over HTTPS and to use Docker packages from them.
   ```bash
   sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Add Docker GPG Key:**
   Add Docker's GPG key to ensure the authenticity of the Docker packages.
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

4. **Add Docker Repository:**
   Add the Docker repository to your system's sources.
   ```bash
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

5. **Update Package Repository Again:**
   Update the package repository again to include the Docker repository.
   ```bash
   sudo apt update
   ```

6. **Install Docker:**
   Install the Docker package.
   ```bash
   sudo apt install -y docker-ce docker-ce-cli containerd.io
   ```

7. **Start and Enable Docker:**
   Start the Docker service and enable it to start on boot.
   ```bash
   sudo systemctl start docker
   sudo systemctl enable docker
   ```

8. **Verify Docker Installation:**
   Check that Docker is running by running a simple hello-world container.
   ```bash
   sudo docker run hello-world
   ```

   If everything is set up correctly, you should see a "Hello from Docker!" message.


# You can specify a different port for the WebGoat Docker container to run on. Here's how you can do it:

1. **Pull the WebGoat Docker Image:**
   If you haven't pulled the image already, use this command to pull the WebGoat Docker image:
   ```bash
   docker pull webgoat/webgoat
   ```

2. **Run the WebGoat Container with a Custom Port:**
   To run the WebGoat container on a different port, use the `-p` flag to map the container's port to a port on your host machine.
   Replace `YOUR_HOST_PORT` with the port number you want to use:
   
   ```bash
   docker run -p YOUR_HOST_PORT:8080 -t webgoat/webgoat
   ```
   For example, to run WebGoat on port 9000, use:
   ```bash
   docker run -p 9000:8080 -t webgoat/webgoat
   ```

4. **Access WebGoat:**
   Open a web browser and navigate to `http://localhost:YOUR_HOST_PORT/WebGoat/` to access the WebGoat interface.

By using the `-p` flag with the `docker run` command, you're specifying the port mapping between the container and your host machine. This allows you to access the application on the specified port of your choice.

Remember to replace `YOUR_HOST_PORT` with the actual port number you want to use on your host machine.
