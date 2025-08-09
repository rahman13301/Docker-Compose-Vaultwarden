# Vaultwarden for self hosted password manager using docker-compose

If you are looking for a password manager where you control all of your data and no one else has access to your secrets, then self-hosting this is a great way to make sure of that. Vaultwarden is one of the best known self-hosted password managers out there and has gained a reputation as one that is secure and does the job.


Step 1: Create ec2 – server – connect – install docker – check status – start docker  

yum install -y docker

docker --version

systemctl status docker

systemctl start docker

Step 2: 

sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64" -o /usr/local/bin/docker-compose

 sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

docker-compose version

step 3: create directory: ex - mkdir nginx

Step 4: create yaml file : ex - touch docker-compose.yml

Step 5: edit file and put below code : ex - vi docker-compose.yml

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


Step 6: enter this cmd to run docker compose: ex -  docker-compose up -d

Step 7: To check active images enter cmd: ex-  docker images 

Step 8: This cmd checks the logs for particular container : ex -  docker-compose logs -f vaultwarden  

step 9:  
 - security group >> inbound >> all traffic >> anywhere 0.0.0.0
 - Access : http://<your-ec2-public-ip:8080
   
   <img width="1148" height="591" alt="image" src="https://github.com/user-attachments/assets/8fb6a56e-b950-4d68-8266-3e72e4b6a719" />


 Project is successfully completed.
