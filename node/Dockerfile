FROM phusion/baseimage:0.9.19

RUN apt-get update &&\
    apt-get install -y git &&\
    apt-get install -y npm &&\
    npm install -g n

ARG NODE_ENV=development
ARG NODE_VERSION=latest
ARG PROJECT_PATH=/opt/app/node-user-api
ARG YARN=false
ARG MYSQL_HOST=database
ARG MYSQL_DATABASE=userSignApi
ARG MYSQL_USER=root
ARG MYSQL_PASSWORD=apiUserNode
ARG MYSQL_PORT=3306
ARG SECRET=
ARG TOKEN_EXP_TIME=5m
ARG DB_DIALECT=mysql

ENV YARN=$YARN
ENV PROJECT_PATH=$PROJECT_PATH
ENV NODE_ENV=$NODE_ENV
ENV MYSQL_HOST=$MYSQL_HOST
ENV MYSQL_DATABASE=$MYSQL_DATABASE
ENV MYSQL_USER=$MYSQL_USER
ENV MYSQL_PASSWORD=$MYSQL_PASSWORD
ENV MYSQL_PORT=$MYSQL_PORT
ENV SECRET=$SECRET
ENV TOKEN_EXP_TIME=$TOKEN_EXP_TIME
ENV DB_DIALECT=$DB_DIALECT

# Add
RUN groupadd -r www-app &&\
    useradd -r -g www-app www-app

RUN mkdir -p /home/www-app &&\
    chmod 777 /home/www-app -R

# Install the specified NODE_VERSION or grab latest
RUN n "$NODE_VERSION"

COPY scripts/run-nodock.sh /usr/bin/run-nodock

RUN chmod 700 /usr/bin/run-nodock

WORKDIR /opt/app/node-user-api

EXPOSE 3000