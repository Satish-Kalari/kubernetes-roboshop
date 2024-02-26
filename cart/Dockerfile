# using nodejs version 18
FROM node:18.19.1-alpine3.19
#EXPOSE functions as a type of documentation between the person who builds the image and the person who runs the container
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# chaning current diretory to /opt/server
WORKDIR /opt/server
#ENV MONGO=true
RUN chown roboshop:roboshop /opt/server
USER roboshop
# copying package.json to /opt/server location
COPY package.json /opt/server
# copying server.js to /opt/server location
COPY server.js /opt/server
# installing dependencies
RUN npm install
# keeping node and server.js active forever
CMD ["node", "server.js"]

# No need to give mongodb URL in cart since server.js contains name "monogobd" with which cart will connect and load into to monodb databse 

# docker build -t cart:v1 . <---to build image

# docker run -d --name cart --network=roboshop cart:v1 <--- to create and run container with name, in roboshop network

# docker ps <-- to see running container
# docker logs cart <-- to see logs of cart