Here's a concise and clear **introduction to Docker and containers**:

---

## 🔹 Introduction to Docker and Containers

### 🚢 What is Docker?

**Docker** is an open-source platform that enables developers to **build, ship, and run applications in containers**. It simplifies application deployment by packaging code and dependencies together into a single unit called a **container**.

---

### 📦 What is a Container?

A **container** is a lightweight, standalone, and executable software package that includes:

* Application code
* Runtime environment
* Libraries
* System tools and settings

Unlike virtual machines, containers **share the host operating system’s kernel**, making them faster and more resource-efficient.

---

### 🧱 Docker vs Virtual Machines

| Feature        | Containers (Docker)  | Virtual Machines (VMs) |
| -------------- | -------------------- | ---------------------- |
| Size           | Lightweight (MBs)    | Heavy (GBs)            |
| Boot Time      | Seconds              | Minutes                |
| OS             | Share host OS kernel | Full guest OS per VM   |
| Isolation      | Process-level        | Full system-level      |
| Resource Usage | Low                  | High                   |

---

### 🔧 Key Docker Concepts

| Term                 | Description                                                                   |
| -------------------- | ----------------------------------------------------------------------------- |
| **Docker Image**     | A blueprint or template used to create containers. Think of it as a snapshot. |
| **Docker Container** | A running instance of a Docker image.                                         |
| **Dockerfile**       | A script containing instructions to build a Docker image.                     |
| **Docker Hub**       | A cloud-based registry for sharing Docker images.                             |
| **Docker Engine**    | The core software that runs and manages containers.                           |

---

### ⚙️ Basic Docker Workflow

1. **Write a Dockerfile** – Define your app and environment.
2. **Build an image** using:

   ```bash
   docker build -t myapp .
   ```
3. **Run a container** using:

   ```bash
   docker run -d -p 8080:80 myapp
   ```
4. **Push to Docker Hub** (optional):

   ```bash
   docker push username/myapp
   ```

---

### ✅ Benefits of Using Docker

* Consistent development and production environments
* Fast and scalable deployments
* Works on any system: Linux, Windows, macOS
* Simplifies CI/CD pipelines

### 🔐 What Are GPG Keys?

**GPG (GNU Privacy Guard) keys** are cryptographic keys used for **secure communication**, **data encryption**, and **authentication**. GPG is an implementation of the **OpenPGP standard**, which provides **public-key encryption and digital signing**.

---

## 🔑 GPG Key Concepts

### 1. **Public Key**

* Shared with others.
* Used by others to **encrypt** messages for you.
* Also used to **verify** your digital signatures.

### 2. **Private Key**

* Kept secret.
* Used to **decrypt** messages sent to you.
* Also used to **sign** messages or files, proving your identity.

Together, these form a **key pair**.

---

## 🛠️ What Are GPG Keys Used For?

| Use Case               | Description                                                            |
| ---------------------- | ---------------------------------------------------------------------- |
| **Email encryption**   | Send confidential emails that only the recipient can decrypt.          |
| **Software signing**   | Verify that software or commits (e.g. Git) come from a trusted source. |
| **File encryption**    | Securely encrypt sensitive files.                                      |
| **Git commit signing** | Prove authorship and integrity of your Git commits.                    |

---

## 🔧 Example Usage

### 🔹 Generate GPG Key:

```bash
gpg --full-generate-key
```

### 🔹 List Your Keys:

```bash
gpg --list-keys
```

### 🔹 Export Public Key:

```bash
gpg --export -a "Your Name" > publickey.asc
```

### 🔹 Import Someone’s Public Key:

```bash
gpg --import theirkey.asc
```

---

## 🔐 How It Works (Simplified)

| Action             | Uses This Key | Result                              |
| ------------------ | ------------- | ----------------------------------- |
| Encrypt data       | Public key    | Only the private key can decrypt it |
| Decrypt data       | Private key   | Reveals original content            |
| Sign a file        | Private key   | Proves authenticity                 |
| Verify a signature | Public key    | Confirms the sender's identity      |

---

## ✅ Summary

* GPG keys enable **encryption**, **decryption**, **signing**, and **verification**.
* You share your **public key**, but keep your **private key** secret.
* GPG is widely used in **email**, **software development**, and **file security**.


### 🔗 How GPG Relates to Ubuntu

GPG (GNU Privacy Guard) is **built into Ubuntu** and used widely across the system for **security, software integrity, and authentication**. Here's how GPG is commonly used on Ubuntu:

---

## 🧩 1. **Software Package Verification (APT + GPG)**

Ubuntu uses **GPG signatures** to ensure that software packages and repositories come from trusted sources and haven’t been tampered with.

### 🔐 Use Case:

When you run:

```bash
sudo apt update
```

Ubuntu checks GPG **signatures** of repository metadata to make sure it hasn't been modified.

If the signature is invalid, you'll get an error like:

```bash
The following signatures couldn't be verified because the public key is not available
```

---

## 📥 2. **Adding GPG Keys for PPAs (Personal Package Archives)**

When you add third-party repositories (e.g., a PPA), you often need to add a GPG key so Ubuntu trusts the source.

### 🔧 Example:

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ABC12345
```

Or in newer Ubuntu versions (recommended):

```bash
curl -fsSL https://download.repo.com/key.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/repo.gpg
```

---

## 🧑‍💻 3. **GPG for Secure Communication and Git Signing**

You can generate a GPG key on Ubuntu and use it for:

* Encrypting files or emails
* Signing Git commits

### ✅ Example: Generate a GPG key

```bash
gpg --full-generate-key
```

### ✅ Example: Sign a Git commit

```bash
git commit -S -m "My secure commit"
```

---

## 🧰 4. **Command Line GPG Tools in Ubuntu**

Ubuntu ships with GPG tools:

* `gpg`: Manage keys, sign/encrypt/decrypt files
* `gpg-agent`: Caches credentials
* `seahorse`: GUI for managing GPG keys (if installed)

---

## 📦 5. **Ubuntu ISO Verification**

When downloading Ubuntu ISOs, the Ubuntu website provides a `.gpg` or `.sig` file to verify the image.

### Steps:

1. Download `.iso`, `.gpg`, and `.gpg.key` files
2. Import Ubuntu’s public key:

   ```bash
   gpg --keyserver keyserver.ubuntu.com --recv-keys F6ECB3762474EDA9
   ```
3. Verify the ISO:

   ```bash
   gpg --verify ubuntu.iso.gpg ubuntu.iso
   ```

---

## ✅ Summary: GPG in Ubuntu

| Area                  | GPG Role                                    |
| --------------------- | ------------------------------------------- |
| Package Manager (APT) | Verifies repo metadata and packages         |
| PPAs                  | Authenticates third-party software sources  |
| ISO Downloads         | Ensures downloaded images are genuine       |
| Git & Dev Workflow    | Signs commits/tags for secure dev pipelines |
| Personal Use          | Encrypts/decrypts/signs your own data       |



## Project on Docker
1. we first start by making sure our terminal is up to date by using ``sudo apt-get update`` 
![caption](/img/1.sudo-update.jpg)

2. using this command
```bash
sudo apt-get install ca-certificates curl gnupg
```
 This a Linux command that installs essential packages including certificate authorities, a data transfer tool (curl), and the GNU Privacy Guard for secure communication and package verification.
![caption](/img/2.work.jpg)

3. using this following command
 ```bash
sudo install -m 0755 -d /etc/apt/keyrings
```
**The command above creates a directory (/etc/apt/keyrings) with specific permissions (0755) for storing keyring files, which are used for docker's authentication**

 using this command
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
**This downloads the Docker GPG key using `curl`**

Using this command
```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

**Sets read permissions for all users on the Docker GPG key file within the APT keyring directory**



**This downloads the Docker GPG key using `curl`**

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

Sets read permissions for all users on the Docker GPG key file within the APT keyring directory

---

***we will add the repository to Apt sources***

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

The `echo` command creates a Docker APT repository configuration entry for the Ubuntu system, incorporating the system architecture and Docker GPG key, and then `sudo tee /etc/apt/sources.list.d/docker.list > /dev/null` writes this configuration to the `/etc/apt/sources.list.d/docker.list` file.


```bash
sudo apt-get update
```
![caption](/img/3.world-load.jpg)

4. *Install latest version of Docker*

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
![caption](/img/4.docker-install.jpg)

5. *Verify that Docker has been successfully installed*
```bash
sudo systemctl status docker
```
![caption](/img/5.check-docker-status.jpg)


6. Add username to the docker group
```
sudo usermod -aG docker ubuntu
``` 
ubuntu signifies the name of the user in my case my user is ibrahim so that's what i will use inplace of ubuntu
![caption](/img/6.add-username.jpg)

7. Running my docker with the title hello-world. This gives an error
```
docker run hello-world
```

docker: permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: connect: permission denied
```

### Explanation:

This happens because your user does **not have the required permission** to access the Docker daemon socket file:
`/var/run/docker.sock`

By default, only users in the **`docker` group** can run Docker commands **without `sudo`**.

---

### Solution:

#### ✅ Option 1: Use `sudo` (temporary workaround)

Run the Docker command with `sudo`:

```bash
sudo docker run hello-world
```

---

#### ✅ Option 2: Add your user to the `docker` group (recommended)

1. Add your user to the Docker group:

   ```bash
   sudo usermod -aG docker $USER
   ```

2. Then **log out and log back in** (or reboot) to apply the group change.

3. Verify by running:

   ```bash
   docker run hello-world
   ```

---

### Check if you’re in the docker group:

```bash
groups
```

You should see `docker` listed. If not, you haven’t successfully joined the group yet.


![caption](/img/7.run-docker.jpg)

8. using the command
```
groups ibrahim
nwgrp docker
docker run hello-world
```
![caption](/img/8.add-docker-group-run.jpg)


The commands and error in the image relate to Docker, a platform for developing, shipping, and running applications inside containers.

### Commands Explained:
1. **`$ groups ibrahim`**
   - This command lists the groups that the user `ibrahim` belongs to. The `docker` group, which is necessary to run Docker commands without `sudo`.

2. **`$ newgrp docker`**
   - This command switches the primary group of the current session to `docker`. This ensures that subsequent Docker commands run with the appropriate group permissions.

3. **`$ docker run hello-world`**
   - This command instructs Docker to run a container using the `hello-world` image. The `hello-world` image is a test image that prints a welcome message and some instructions when run, verifying that Docker is working correctly.
### Error Explained:
The error message indicates:
- **"Unable to find image 'hello-world:latest' locally"**
  - Docker couldn’t find the `hello-world` image on the local system, so it attempted to pull it from the default registry (`registry-1.docker.io`).
- **"dial tcp: lookup registry-1.docker.io on 127.0.0.53:53: read udp 127.0.0.1:60850->127.0.0.53:53: i/o timeout"**
  - This suggests a network issue. Docker tried to resolve the domain `registry-1.docker.io` (the Docker Hub registry) using the local DNS server at `127.0.0.53:53`, but the request timed out. This could be due to:
    - No internet connection.
    - DNS resolution failure (e.g., misconfigured `/etc/resolv.conf` or a blocked DNS server).
    - A firewall or network restriction preventing access to `registry-1.docker.io`.

### Possible Solutions:
- Check your internet connection.
- Verify DNS settings (e.g., ensure `/etc/resolv.conf` points to a valid DNS server like `8.8.8.8`).
- Test connectivity to `registry-1.docker.io` with `ping registry-1.docker.io` or `nslookup registry-1.docker.io`.
- Ensure the Docker daemon is running (`sudo systemctl status docker`).
- Retry the command after resolving the network issue.


9. usiing the command below we are going to enter the daemond.json file to configure our dns to global.

The daemon.json file is the configuration file for the Docker daemon (dockerd), which controls how Docker operates on your system. It is typically located at /etc/docker/daemon.json on Linux systems
```
sudo nano /etc/docker/daemon.json
```


![caption](/img/9.write-into-docker.jpg)

10. input google dns by writing this into daemond.json file
```
{
   "dns": ["8.8.8.8", "8.8.4.4"]
}
```
![caption](/img/10.dns-google.jpg)

11. Restart docker and Rerun the docker images
```
sudo systemctl restart docker
docker run hello-world
```
![caption](/img/11.restart-run.jpg)

12. to check the docker we just run
we will use the commond docker images to see our docker images

```
docker image
```
![caption](/img/12.docker-images.jpg)

13. After creating the image if you run it it will show its working by giving you the hello-world message
```
docker run hello-world
```

![caption](/img/13.docker-shows-image-exist.jpg)


14. To check for a running container
```
docker ps
```
![caption](/img/14.docker-ps.jpg)

15. Check the container that's not running 
```
docker ps -a
```
![caption](/img/15.docker-ps-a.jpg)

16. The docker pull ubuntu command is used to download a Docker image from a registry (by default, Docker Hub) to your local system.
```
docker pull ubuntu
```

![caption](/img/16.docker-pull-ubuntu.jpg)

17. To delete an image we specify the image id
```
docker rm $image-id
```
![caption](/img/23.docker-rmi.jpg)

18. Creating an nginx server to a port 80(http)
```
docker run -d -p 8080:80 nginx
```



![caption](/img/'25.run-ngnix-as-container.jpg)

The command and output in the image relate to running a Docker container with a custom port mapping. Here's a detailed explanation:

### Command Explained:
- **`$ docker run -d -p 8080:80 ibdevop/hello-world:latest`**
  - **`docker run`**: Initiates a new container from a specified image.
  - **`-d`**: Runs the container in detached mode, meaning it runs in the background and doesn’t block the terminal.
  - **`-p 8080:80`**: Maps port 8080 on the host machine to port 80 inside the container. This allows external access to the container’s service (e.g., a web server) on host port 8080.
  - **`ibdevop/hello-world:latest`**: Specifies the image to use, tagged as `ibdevop/hello-world:latest`. This is the custom-tagged image you created earlier from the `hello-world` base image.

  19. To access the nginx on webpage we will use
  ```
  http://localhost:8080
  ```
  ![caption](/img/26.ngnix-web.jpg)

  20. stopping a container
  ```
  docker stop $container-id
  ```
  ![caption](/img/28.docker-stop.jpg)

21. deleting container 
```
docker rm $container-id
```
we can supply multiple id's to delete
 ![caption](/img/29.delete-container.jpg)

 ## To push into docker hub

 22. Firstly we log in from terminal using the command

 ```
 docker login
 ```
 This will give us a code and also a url to log in to authenticate log in
 ![caption](/img/20.login-code.jpg)

 23. After pasting the code giving the the browser you will get a congrats message ![caption](/img/21.paste-your-code-get-congrats.jpg)

 24. We can push our images into our docker hub
 ```
 docker push $repository
 ```
 To be able to push nginx image i have to use a tag and duplicate it to have another name. using ibdevop/nginx. then i can push the later nginx

 ![caption](/img/30.push-docker-hub.jpg)

 25. login to my docker hub i can see the image i pushed

 ![caption](/img/31.docker-hub-image.jpg)