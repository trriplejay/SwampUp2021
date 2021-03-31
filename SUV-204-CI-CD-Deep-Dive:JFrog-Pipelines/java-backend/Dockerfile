#Download image from artifactory
ARG REGISTRY
FROM openjdk:11-jdk
#FROM $REGISTRY/openjdk:11-jdk

WORKDIR /app

#Define ARG Again -ARG variables declared before the first FROM need to be declered again
ARG REGISTRY
MAINTAINER Colathur Vijayan

# Add downloaded artifacts from jfrog cli to the image
RUN ls -lR
ADD ./client.tgz .
ADD ./server.jar .


# Set JAVA OPTS + Static file location
ENV STATIC_FILE_LOCATION="/app/package/target/dist/"
# ENV GO_SERVICE="127.0.0.1"
ENV JAVA_OPTS=""

# Fire up our Spring Boot app
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Dspring.profiles.active=remote -Djava.security.egd=file:/dev/./urandom -jar /app/server.jar" ]
