FROM maven:alpine
MAINTAINER Franz-Benjamin Mocnik <mocnik@uni-heidelberg.de>

WORKDIR /home

## copy files
COPY files .

## link files
RUN mkdir -p src/main/java/org/giscience/measures && ln -s /data/user src/main/java/org/giscience/measures/repository

## install
RUN mvn dependency:go-offline exec:help compile

## run
ENTRYPOINT ["mvn", "compile", "exec:java"]
