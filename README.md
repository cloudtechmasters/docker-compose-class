# docker-compose

# Pre-requisites:
  - Install Java
  - Install Maven
  - Install Docker
  - Install Docker-compose
 
# Clone Springboot-mongodb application:
    git clone https://github.com/Naresh240/docker.git
    cd docker/springboot-mongodb-dockercompose
# Build artifact
    mvn clean install -DskipTests=true
 
# Build Docker Image
    docker build -t naresh240/springboot-mongodb:latest .
# Docker login
    docker login -u naresh240 -p
# Push Docker image to Dockerhub
    docker push naresh240/springboot-mongodb:latest
    
# Deploy application with run command:
    docker run --name mymongodb -p 27017:27017 -d mongo
    docker run --name springboot-mongodb --link mymongodb:mymongodb -p 8080:8080 -d naresh240/springboot-mongodb:latest
# Use postman app and Add Employee data
Check API: /addEmployee

    http://<ip-address>:8080/addEmployee
  
In postman app keep Post method and give Json data by selecting Body --> raw (Json format)

    {"id": "1001", "name": "Naresh", "departement": "Engineer"}
    
Check API:- /findAllEmployees

Goto Web UI and check below link

    http://<ip-address>:8080/findAllEmployees
# CleanUP
    docker stop <container-name>
    docker rm <container-name>
    
# Deploy springboot-mongodb application using docker-compose
    docker-compose up -d
# Use postman app and Add Employee data

Check API: /addEmployee

    http://<ip-address>:8080/addEmployee
  
In postman app keep Post method and give Json data by selecting Body --> raw (Json format)

    {"id": "1001", "name": "Naresh", "departement": "Engineer"}
    
Check API:- /findAllEmployees

Goto Web UI and check below link

    http://<ip-address>:8080/findAllEmployees
    
# To down our springboot-mongodb application
    docker-compose down
