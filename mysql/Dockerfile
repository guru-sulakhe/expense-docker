FROM mysql:8.0
# creating user for non-root access in debian OS
# this is system user,Not a human, only for system
RUN adduser -r expense
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
    MYSQL_USER=expense \
    MYSQL_PASSWORD=ExpenseApp@1 \
    MYSQL_DATABASE=transactions
#copying *.sql code to docker-entrypoint-initdb.d which will helps in loading schema.sql to the database
COPY scripts/*.sql /docker-entrypoint-initdb.d/
# allowing access of /var/lib/mysql /var/run/mysqld /usr/sbin/mysqld for only expense user
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld /usr/sbin/mysqld
USER expense

#if you have any doubts of adding new instructions related to mysql 
#visit to docker hub and search for mysql, there you can find the instructions related to mysql