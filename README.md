# Vaultwarden for self hosted password manager using docker-compose

If you are looking for a password manager where you control all of your data and no one else has access to your secrets, then self-hosting this is a great way to make sure of that. Vaultwarden is one of the best known self-hosted password managers out there and has gained a reputation as one that is secure and does the job.


## Step 1: Create ec2 – server – connect – install docker – check status – start docker  
```
yum install -y docker
docker --version
systemctl status docker
systemctl start docker
```
## Step 2: import docker-compose from official site, change mode and check the version.
```
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose version
```
## Step 3: create directory and create yaml file:
```
mkdir nginx
touch docker-compose.yml
vi docker-compose.yml
```

**Edit file and put below code:**

```
version: '3'

services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    volumes:
      - ./vw-data:/data
    ports:
      - "8080:80"
    restart: always
```

## Step 4: enter this cmd to run docker-compose, check images and logs: 
```
docker-compose up -d
docker images
docker-compose logs -f vaultwarden
```

## Step 5: Change inbound rules:
 - Security group >> inbound >> all traffic >> anywhere 0.0.0.0
 - Access : http://<your-ec2-public-ip:8080
   
   <img width="1148" height="591" alt="image" src="https://github.com/user-attachments/assets/8fb6a56e-b950-4d68-8266-3e72e4b6a719" />


 Project is successfully completed.
