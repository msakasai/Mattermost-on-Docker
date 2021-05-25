FROM mysql:8

RUN apt-get -y update
RUN apt-get -y install vim wget curl git less procps net-tools sudo make cmake gcc g++ zip gzip unzip tar

EXPOSE 3306
VOLUME /var/lib/mysql

CMD ["mysqld", "-u", "mysql"]
