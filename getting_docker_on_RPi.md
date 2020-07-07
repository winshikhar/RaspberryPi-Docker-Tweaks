# Docker
Firstly, we need to install certain dependencies.
```
sudo apt-get install apt-transport-https ca-certificates software-properties-common -y
```

### Now, download and install Docker
```
curl -fsSL get.docker.com -o get-docker.sh && sh get-docker.sh
```

Give the {USER} `pi` the ability to run Docker [i.e. add the non-root user to the Docker group]:
> **Note:** You may have different username, so change the field accordingly.
```
sudo usermod -aG docker pi
```

Now, import the Docker GPG key (for authentication purpose):
```
sudo curl https://download.docker.com/linux/raspbian/gpg
```

### Now, setup the Docker Repo
> This step is required so that you can upgrade to the latest version of docker available for the RPi.

For this, you'll need to check the **distribution** and the **version of distribution** running on your RPi.
At the time of making this guide, the latest version of `Raspberry Pi OS` (formely Raspbian) is `buster`.

Run the command:
```
sudo nano /etc/apt/sources.list
```
Navigate to the end of file and add the following line:
```
deb https://download.docker.com/linux/raspbian/ buster stable
```
From here, patch and upgrade your RPi:
```
sudo apt update && sudo apt upgrade -y
```

### Now, we have two optons to reflect the changes to the system
1. Reboot your system (recommended)
```
sudo reboot now
```
OR

2. Run the following command (if you don't want to reboot):
``` 
newgrp docker
```

### Now, start the Docker service
```
sudo systemctl start docker.service
```
To verify that the service is running successfully, run:
``` 
docker info 
```

### Test the installation
YES! We need to check whether everything got integrted and works perfectly.
For this, run:
```
docker run hello-world
```
> If you get **permission denied** error, append `sudo`.
> ```
> sudo docker run hello-world
> ```

This step will download the `hello-world` demo image for Docker and run it to give you an idea of, **how the Docker data flow behaved**.
When executing it for the first time, you should get an output like:
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
{some alpha-numeric id}: Already exists
Digest: sha256:{some long long long value}
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm32v7)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```