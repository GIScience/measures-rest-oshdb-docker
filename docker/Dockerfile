FROM maven:alpine
MAINTAINER Sascha Fendrich <sascha.fendrich@uni-heidelberg.de>

WORKDIR /home

## link files
RUN mkdir -p src/main/java/org/giscience/measures && ln -s /data/user src/main/java/org/giscience/measures/repository
RUN ln -s /data/user/pom.xml pom.xml

## install
RUN if [ -d "/data/user/" ]; then mvn dependency:go-offline exec:help compile; fi

## run
RUN echo "#!/usr/bin/env bash" > /home/entrypoint.sh
RUN echo "chmod 755 /data/user/cleanup.sh" >> /home/entrypoint.sh
RUN echo "/data/user/cleanup.sh" >> /home/entrypoint.sh
RUN echo "mvn compile exec:java" >> /home/entrypoint.sh
RUN chmod 755 /home/entrypoint.sh
ENTRYPOINT ["/home/entrypoint.sh"]
