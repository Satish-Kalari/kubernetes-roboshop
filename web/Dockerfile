FROM nginx
# removing default index.html from /usr/share/nginx/html/ location
RUN rm -rf /usr/share/nginx/html/index.html
# removing default nginx.conf from /etc/nginx/ location
RUN rm -rf /etc/nginx/nginx.conf
# removing default.conf from /etc/nginx/conf.d/default.conf location
RUN rm -rf /etc/nginx/conf.d/default.conf
# copying our custom roboshop.conf local file to /etc/nginx/nginx.conf location
COPY roboshop.conf /etc/nginx/nginx.conf
# COPY and ADD are same, ADD has two extra function, copying from URL and untar
# Adding our custom html data from static local folder to /usr/share/nginx/html/ location
ADD static /usr/share/nginx/html/
# we donr need CMD here, this will atomatically run once we create container

# docker build -t web:v1 . <---to build image

# docker run -d -p 80:80 --name web --network=roboshop catalogue:v1 <--- to create and run container with name, in roboshop network with 80 prot

# docker ps <-- to see running container
# docker logs web <-- to see logs of web