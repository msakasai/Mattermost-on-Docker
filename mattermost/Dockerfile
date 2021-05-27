FROM ubuntu:21.04

ARG MM_VER=5.35.1
ARG PUID=2000
ARG PGID=2000
ARG DB_HOST=127.0.0.1
ARG DB_PORT=3306

RUN apt-get -y update
RUN apt-get -y install vim
RUN apt-get -y install wget
RUN apt-get -y install curl
RUN apt-get -y install git
RUN apt-get -y install less
RUN apt-get -y install procps
RUN apt-get -y install net-tools
RUN apt-get -y install sudo
RUN apt-get -y install make
RUN apt-get -y install cmake
RUN apt-get -y install gcc
RUN apt-get -y install g++
RUN apt-get -y install zip
RUN apt-get -y install gzip
RUN apt-get -y install unzip
RUN apt-get -y install tar

WORKDIR /work

RUN echo $(pwd)
RUN wget https://releases.mattermost.com/${MM_VER}/mattermost-${MM_VER}-linux-amd64.tar.gz
RUN tar xfz mattermost-${MM_VER}-linux-amd64.tar.gz
RUN mv mattermost /opt/mattermost
RUN mkdir /opt/mattermost/data
RUN mkdir /opt/mattermost/plugins
RUN mkdir /opt/mattermost/client/plugins
RUN echo $(ls -l /opt/mattermost/)
RUN sed -i -e "s|\"DriverName\": \"postgres\"|\"DriverName\": \"mysql\"|" \
        -i -e "s|\"DataSource\":.*\"|\"DataSource\": \"mmuser:mmpass@tcp(${DB_HOST}:${DB_PORT})/mattermost?charset=utf8mb4,utf8\\u0026readTimeout=30s\\u0026writeTimeout=30s\"|" \
        -i -e "s|\"DefaultServerLocale\": \"en\"|\"DefaultServerLocale\": \"ja\"|" \
        -i -e "s|\"DefaultClientLocale\": \"en\"|\"DefaultClientLocale\": \"ja\"|" \
        -i -e "s|\"AvailableLocales\": \"\"|\"AvailableLocales\": \"ja,en\"|" \
        /opt/mattermost/config/config.json

RUN useradd --system --user-group mattermost
RUN chown -R mattermost:mattermost /opt/mattermost
RUN chmod -R g+w /opt/mattermost/

USER mattermost
WORKDIR /opt/mattermost

EXPOSE 8065 8067 8074 8075
VOLUME ["/opt/mattermost/data", "/opt/mattermost/logs", "/opt/mattermost/config", "/opt/mattermost/plugins", "/opt/mattermost/client/plugins"]

ENTRYPOINT ["/opt/mattermost/bin/mattermost"]
