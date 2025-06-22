<h1>🐳 Docker & Containerization </h1> 

🔄 A platform to develop, ship, and run applications in containers, making them portable and consistent across environments. <br>
🔄 Containers: Running instances of Docker images. Think of them as lightweight, isolated environments. <br>
🔄 Dockerfile: A script with instructions to build Docker images (e.g., from Ubuntu, install packages, copy code, etc.). <br>
🔄 Docker Compose: A tool to define and manage multi-container apps using docker-compose.yml. <br>
🔄 Networking: Docker provides isolated virtual networks; containers can communicate using service names. <br>
<hr>

![docker](https://github.com/user-attachments/assets/c9f7861a-57f5-4362-ae75-9ce1908e100e)


✅ Common Docker Commands
```
# Run a container
docker run -d -p 8080:80 nginx

# Build image from Dockerfile
docker build -t myapp .

# List running containers
docker ps

# Start/stop containers
docker start <id> && docker stop <id>

# Remove container/image
docker rm <id> && docker rmi <image>
```
<h1>🐳 NextCloud powered by Docker </h1> 

1. Install Server - I am using Hyper-V and Ubuntu Server LTS <br>
2. Install updates <br>
3. Install Docker and set running docker without sudo (avoiding using sudo with every docker command) <br>
sudo usermod -aG docker $USER <br>
The docker group is created automatically during the Docker installation. <br>
4. Install Docker Compose sudo apt install -y docker-compose <br>
5. mkdir nextcloud-docker <br>
6. cd nextcloud-docker <br>
7. Create a docker-compose.yml file:

```
version: '3'

services:
  db:
    image: mariadb:10.6
    restart: always
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW
    volumes:
      - db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=secret
      - MYSQL_PASSWORD=nextcloudpass
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser

  app:
    image: nextcloud
    ports:
      - 8080:80
    links:
      - db
    volumes:
      - nextcloud:/var/www/html
    restart: always
    environment:
      - MYSQL_PASSWORD=nextcloudpass
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser
      - MYSQL_HOST=db

volumes:
  db:
  nextcloud:
```
8. docker-compose up -d <br>
9. http://your-server-ip:8080

<h1>🐳 Flask powered by Docker </h1> 

🔄 Flask is a popular micro web framework written in Python. <br>
🔄 Simplicity and Ease of Use: It has a gentle learning curve and is quick to get started with, even for beginners. <br>
🔄 Great for APIs and Microservices <br>
🔄 Flexibility & Lightweight <br>

![flask](https://github.com/user-attachments/assets/00a348a0-a78e-4661-96f9-596fcea6ad5c)


