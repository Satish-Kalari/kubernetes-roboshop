#
# Build
#
FROM maven AS build

WORKDIR /opt/shipping

COPY pom.xml /opt/shipping/
RUN mvn dependency:resolve
COPY src /opt/shipping/src/
RUN mvn package

#
# Run
#
FROM openjdk:8-jre-alpine3.9

EXPOSE 8080

WORKDIR /opt/shipping

ENV CART_ENDPOINT=cart:8080
ENV DB_HOST=mysql

COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar" ]

#--->mutistage bulids<----docker best practice 

#For java projects uses maven and jdk (java development kit) and gives us jar file
#but when run no need of maven or jdk since image is already built, we need jre (java runtime environment)

#jdk = jre + development packages  

#while build image need jdk (heavy), while running container jre (light weight) is enough 

# docker build -t shipping:v1 . <---to build image