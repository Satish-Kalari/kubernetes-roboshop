#using mongo version 5
FROM mongo:5
# (1) Dockerfile to copy all files with the extension ".js" to the "/docker-entrypoint-initdb.d/" directory inside the Docker container
# (2) This command is typically used to initialize a database inside a Docker container by copying the necessary scripts or data files to the container's file system. 
# (3) The asterisk () is a wildcard character that matches any file name with the ".js" extension in the current directory
COPY *.js /docker-entrypoint-initdb.d/

# docker build -t mongodb:v1 . <---to build image

# *** docker network create roboshop <--- creating roboshop network ***

# docker run -d --name mongodb --network=roboshop mongodb:v1 <--- to create and run container with name, in roboshop network

# docker ps <-- to see running container
# docker logs mongodb <-- to see logs of mongodb