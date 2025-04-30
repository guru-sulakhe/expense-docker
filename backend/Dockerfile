#Selecting Base OS
FROM node:20.15.0-alpine3.20
#Exposing port 8080
EXPOSE 8080
#Connecting to mysql server through backend by creating env variable DB_HOST, connects to mysql container 
ENV DB_HOST=mysql
#Creating expense group, expense user and adding  expense user to expense group, creating and allowing ownership access for /opt/server directory to expense user
RUN addgroup -S expense && adduser -S expense -G expense \
    && mkdir /opt/server \
    && chown expense:expense -R /opt/server
#changing to /opt/server directory
WORKDIR /opt/server
#copying package.json on /opt/server directory
COPY package.json .
#copying *.js on /opt/server directory
COPY *.js /opt/server/
#installing system dependencies
RUN npm install
#allowing non-root access for the container and allowing only expense-user access for the non-root access in the dockerfile
USER expense
#exposing port 8081
EXPOSE 8081
#Running index.js file while creating the container 
CMD [ "node","index.js" ]

#NOTE: while creating mysql container, create with mysql as container name which will helps building connection between backend and mysql