FROM mysql:8.0
# not for human, only for system
RUN adduser -r expense
#copying *.sql code to docker-entrypoint-initdb.d which will helps in loading schema.sql to the database
COPY scripts/*.sql /docker-entrypoint-initdb.d/
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld /usr/sbin/mysqld
USER expense

#if you have any doubts of adding new instructions related to mysql 
#visit to docker hub and search for mysql, there you can find the instructions related to mysql