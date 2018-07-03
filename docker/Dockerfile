FROM maven:alpine
MAINTAINER Franz-Benjamin Mocnik <mocnik@uni-heidelberg.de>

WORKDIR /home

## link files
RUN mkdir -p src/main/java/org/giscience/measures && ln -s /data/user src/main/java/org/giscience/measures/repository
RUN ln -s /data/user/pom.xml pom.xml

## install
RUN if [ -d "/data/user/" ]; then mvn dependency:go-offline exec:help compile; fi

## run
ENTRYPOINT ["mvn", "compile", "exec:java"]
