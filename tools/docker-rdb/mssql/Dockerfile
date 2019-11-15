FROM microsoft/mssql-server-linux:latest

ENV SA_PASSWORD=1234
ENV ACCEPT_EULA=Y

RUN apt-get update && locale-gen en_US.UTF-8 && update-locale
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

EXPOSE 1433
