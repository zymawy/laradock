ARG MYSQL_VERSION
FROM mysql:${MYSQL_VERSION}
ENV MYSQL_ALLOW_EMPTY_PASSWORD yes

LABEL maintainer="Mahmoud Zalt <mahmoud@zalt.me>"

#####################################
# Set Timezone
#####################################

ARG TZ=UTC
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && chown -R mysql:root /var/lib/mysql/

COPY my.cnf /etc/mysql/conf.d/my.cnf

RUN chmod 0444 /etc/mysql/conf.d/my.cnf

RUN mkdir -p /var/lib/mysql && chown -R mysql:mysql /var/lib/mysql && \
    mysqld --initialize-insecure --user=mysql --datadir=/var/lib/mysql


RUN mysqld --initialize-insecure --user=mysql --datadir=/var/lib/mysql
# COPY setup.sh /mysql/setup.sh
# COPY schema.sql /mysql/schema.sql
# COPY test.sql /mysql/test.sql
# COPY mysql/master.cnf /etc/mysql/conf.d/
# COPY privileges.sql /mysql/privileges.sql
# COPY init-database.sql /mysql/init-database.sql
CMD ["mysqld"]

EXPOSE 3306
