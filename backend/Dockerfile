FROM node:20.18.1-alpine3.19
EXPOSE 8080
# connecting to mysql db server from backend
ENV DB_HOST=mysql
# adding user expense in alpine OS version
RUN addgroup -S expense && adduser -S expense -G expense 
RUN mkdir /opt/server
RUN chown expense:expense -R /opt/server
# changing directory to /opt/server
WORKDIR /opt/server
COPY package.json /opt/server
COPY *.js /opt/server
# installing nodejs modules
RUN npm install
USER expense
CMD ["node","index.js"]