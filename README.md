# Docker-install-in-Ubuntu-24.04
To install Docker on Ubuntu 24.04 Desktop, follow these steps:

### Step 1: Update Your System
Start by updating the package index on your system to ensure you have the latest information on the available packages.

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Install Required Dependencies
Install the necessary packages that allow `apt` to work with repositories over HTTPS.

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

### Step 3: Add Docker’s Official GPG Key
Next, add Docker’s official GPG key to verify the packages you’re installing.

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Step 4: Set Up the Stable Docker Repository
Add the Docker repository to `apt` sources.

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Step 5: Install Docker Engine
Update the package index again to reflect the new repository and install Docker.

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

### Step 6: Start and Enable Docker Service
Start Docker and enable it to start automatically on boot.

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 7: Verify Docker Installation
To verify that Docker has been installed and is running, use the following command:

```bash
sudo docker --version
```

It should return the Docker version you installed, for example:

```
Docker version 20.10.8, build 3967b7d
```

### Step 8: Allow Running Docker as a Non-Root User (Optional)
By default, Docker requires root privileges. If you want to run Docker commands without `sudo`, you can add your user to the `docker` group.

```bash
sudo usermod -aG docker $USER
```

After running this, log out and log back in for the group change to take effect.

### Step 9: Test Docker with a Simple Command
To test if Docker is working correctly, run the following command to pull and run a test container:

```bash
docker run hello-world
```

If everything is set up correctly, you should see a message saying "Hello from Docker!"

---

That’s it! You should now have Docker installed and running on your Ubuntu 24.04 desktop. Let me know if you need any more help!
