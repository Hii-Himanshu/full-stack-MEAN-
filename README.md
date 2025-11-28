#  Full-Stack MEAN Application — Dockerized & Deployed 


#   Deploy on Any Cloud VM (Using AWS EC2 Example)

### Step 0 — Allow Port 80 in EC2 Security Group
```
Before accessing the app, update your EC2 security group:

1. Go to AWS EC2 Console

2. Select your EC2 instance

3. Open Security → Security Groups

4. Click Edit Inbound Rules

5. Add a rule:

Type	Protocol	Port	Source
HTTP	 TCP	     80	    0.0.0.0/0

6. Save the rule.
```

### Step 1 — SSH into EC2
```
ssh -i your-key.pem ubuntu@EC2_PUBLIC_IP

```

### Step 2 — Install Docker & Docker Compose

#### Add Docker's official GPG key:
```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

#### Add the repository to Apt sources:
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

#### Install Docker:
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### Grant the permission 
```bash
sudo chmod 777 /var/run/docker.sock
```
#### Verify Docker Installation:

```bash
docker ps

```

### Step 3 — Clone Your Repository

```bash
git clone https://github.com/Hii-Himanshu/full-stack-MEAN-.git

# change directory to full-statck-MEAN- folder
cd full-stack-MEAN-
```

### Step 4 — Start Services

```bash
docker compose up -d

```


### Step 5 — Access App

```bash
http://EC2_PUBLIC_IP:80 (by default it will take 80)

```
