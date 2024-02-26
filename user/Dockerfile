# using nodejs version 18
FROM node:18.19.1-alpine3.19
#EXPOSE functions as a type of documentation between the person who builds the image and the person who runs the container
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# chaning current diretory to /opt/server
WORKDIR /opt/server
#ENV MONGO=true # in k8 we are giving this as configmap
RUN chown roboshop:roboshop /opt/server
USER roboshop
# copying package.json to /opt/server location
COPY package.json /opt/server
# copying server.js to /opt/server location
COPY server.js /opt/server
# installing dependencies
RUN npm install
RUN adduser cart
# keeping node and server.js active forever
CMD ["node", "server.js"]

# No need to give mongodb URL in user since server.js contains name "monogobd" with which user will connect and load into to monodb databse 

# docker build -t user:v1 <---to build image

# docker run -d --name user --network=roboshop user:v1 <--- to create and run container with name, in roboshop network

# docker ps <-- to see running container
# docker logs user <-- to see logs of user

FROM node:18.19.1-alpine3.19
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
ENV MONGO=true
RUN chown roboshop:roboshop /opt/server
USER roboshop
COPY package.json /opt/server/
COPY server.js /opt/server/
RUN npm install
RUN echo Hello World
RUN adduser cart
CMD ["node", "server.js"]