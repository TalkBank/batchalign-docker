FROM mysql:8.0.34

# set root password
ENV MYSQL_ROOT_PASSWORD="batchalign"

ADD schema.sql /docker-entrypoint-initdb.d

EXPOSE 3306

