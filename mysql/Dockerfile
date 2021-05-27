FROM mysql:8

ARG ROOT_PASSWORD=""
ARG DATABASE=mattermost
ARG USER=mmuser
ARG PASSWORD=""

RUN apt-get -y update
RUN apt-get -y install vim wget curl git less procps net-tools sudo make cmake gcc g++ zip gzip unzip tar

ENV MYSQL_ROOT_PASSWORD=${ROOT_PASSWORD}
ENV MYSQL_DATABASE=${DATABASE}
ENV MYSQL_USER=${USER}
ENV MYSQL_PASSWORD=${PASSWORD}

EXPOSE 3306
VOLUME /var/lib/mysql

CMD ["mysqld", "-u", "mysql"]
