# DOCKER-MINIKUBE

## Steps for Ec2 server Deployment

Quick Deployment Steps
1. Log in to AWS Console: Go to the AWS Management Console and sign in.
2. Navigate to EC2: Search for and select EC2 from the services list.
3. Launch Instance: Click the Launch Instance button.
4. Choose AMI & Type: Select your desired AMI (e.g., Ubuntu, Amazon Linux) and an Instance Type (e.g., t2.micro).
5. Configure: Leave most settings as default, but ensure Auto-assign Public IP is enabled if needed.
6. Add Storage & Tags: Adjust the storage size and add a Name tag to identify your instance.
7. Configure Security Group: Set up firewall rules to allow traffic on specific ports like SSH (22) and HTTP (80).
8. Review & Launch: Confirm your settings, then click Launch.
9. Select Key Pair: Choose an existing key pair or create a new one to securely connect to your instance.
10. <img width="1919" height="881" alt="Screenshot 2025-11-04 152255" src="https://github.com/user-attachments/assets/be2dc91f-f61b-436c-a292-0bab22e0d700" />


# DOCKER.md
# docker-install


### Quick Install
```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
---

install packages:
```bash
sudo apt update
sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    jq
```

Add Docker’s official GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

setup repository:
```bash
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine:
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

Add your user to the docker group:
```bash
sudo usermod -aG docker $USER
```

### Docker Compose

download the current stable release of Docker Compose:
```bash
COMPOSE_VERSION=$(curl -s "https://api.github.com/repos/docker/compose/tags" | jq -r '.[0].name')
sudo curl -L "https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose
```

Apply executable permissions to the binary:
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
# PULL IMAGES 
```bash
 docker pull hello-world
```
```bash
 docker pull nginx
```
```bash
docker pull ubuntu/apache2
```
# SEE IMGAGES/INSPECT
```bash
 docker images
```
```bash
 docker inspect
```
```bash
  docker ps
```
# PORT FORWADING 
```bash
docker run --name mynginxl -p 80:80 -d nginx
```
```bash
docker run --name myapache -p 80:80 -d ubuntu/apache2
```
# KILLING IMAGE
```bash
docker kill mynginxl
```
<img width="1919" height="1074" alt="Screenshot 2025-11-04 143721" src="https://github.com/user-attachments/assets/084bd53e-d455-42b0-b3a7-b08674677cf2" />



# To install the latest minikube stable release on x86-64 Linux using binary download:

``curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64``



# 2.Start your cluster
From a terminal with administrator access (but not logged in as root), run:
```minikube start```
# Interact with your cluster
If you already have kubectl installed (see documentation), you can now use it to access your shiny new cluster:

```kubectl get po -A```
Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

```minikube kubectl -- get po -A```
You can also make your life easier by adding the following to your shell config: (for more details see: kubectl)

```alias kubectl="minikube kubectl --"```
Initially, some services such as the storage-provisioner, may not yet be in a Running state. This is a normal condition during cluster bring-up, and will resolve itself momentarily. For additional insight into your cluster state, minikube bundles the Kubernetes Dashboard, allowing you to get easily acclimated to your new environment:

```minikube dashboard```
<img width="990" height="356" alt="Screenshot 2025-11-04 151226" src="https://github.com/user-attachments/assets/79d48a66-86d0-4155-b00d-b1745a67bed3" />




<img width="1001" height="278" alt="Screenshot 2025-11-04 151159" src="https://github.com/user-attachments/assets/4e13c42a-21fd-4064-a558-b71ca1430312" />

# Install Kubernetes (kubectl)
Step 1: Download kubectl
``` bash
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
```

Step 2: Make it executable & move
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

Step 3: Test it
kubectl version --client
kubectl get nodes


You should see:

NAME       STATUS   ROLES    AGE   VERSION
minikube   Ready    master   Xs    v1.xx.x

🚀 4. Verify Everything
# Docker
docker ps

# Minikube
minikube status

# Kubernetes
kubectl get pods -A
