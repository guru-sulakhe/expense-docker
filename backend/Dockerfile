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
#allowing non-root access for the container and allowing only expense-user access for the non-root access in the dockerfile, from here normal user access the container
USER expense
#exposing port 8081
EXPOSE 8081
#Running index.js file while creating the container 
CMD [ "node","index.js" ]

#NOTE: 
#     while creating mysql container, create with mysql as container name which will helps building connection between backend and mysql.
#     mysql  container can't be connected from backend container and container will not be created, due to the default docker network
#     docker defaultly uses bridge network at which docker0(default bridge network ) acts as a bridge between two containers, which can't be useful for connection of containers.
#     docker uses host network, where the containers can able to connect to the direct HOST.
#     in the above code we are using ENV DB_HOST=mysql. which will be helpful for building connection between host network of mysql from backend.
#     create a host network through which backend can connect to mysql
#     $ docker network create expense
#     Now we need to allow mysql and backend containers to run into expense network
#     $ docker run -d -p 3306:3306 --name mysql --network expense mysql:v1.0
#     $ docker run -d -p 8080:8080 --name backend --network expense backend:v1.0

#     verifying whether mysql client is installed in backend or not
#     $ docker exec -it backend bash
#     # mysql
#     # cat /etc/*release --> to know the OS information
#     # apt update
#     # apt install -y deault-mysql-client
#     # mysql -h mysql -u root -pExpenseApp@1 ---> connecting to mysql from backend
#     TO troubleshoot 
#     $ docker exec -it backend sh
#       # curl http://localhost:8080/transaction -->if it is success you will see result{[]}