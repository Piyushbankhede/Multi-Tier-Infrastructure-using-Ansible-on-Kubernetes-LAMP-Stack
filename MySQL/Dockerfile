FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y mysql-server && \
    apt clean && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/run/mysqld /var/lib/mysql && \
    chown -R mysql:mysql /var/run/mysqld /var/lib/mysql

COPY mysqld.cnf /etc/mysql/mysql.conf.d/mysqld.cnf

EXPOSE 3306

USER mysql

# ✅ Conditional initialization before MySQL starts
CMD ["/bin/bash", "-c", "[ -d /var/lib/mysql/mysql ] || mysqld --initialize-insecure && exec mysqld"]