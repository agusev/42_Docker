#!/bin/bash
FROM ruby:2.5.1

MAINTAINER agusev
# make db
#docker run -d -v /var/lib/postgresql/data -e MYSQL_ALLOW_EMPTY_PASSWORD=true --name db-data mysql:5.7
#build project
#docker build -t server (name) .
#run server
#docker run -it -p 3000:3000 --link db-data --name serv eee:2.5.1 bash

RUN apt-get update -y && apt-get install nodejs -y && \
	gem install rails && apt-get install mysql-server -y && \
	service mysql start

COPY app/ /opt
WORKDIR /opt/app

EXPOSE 3000:3000

RUN bundle install && rake db:migrate && rake db:setup && rake db:seed

CMD ["rails", "server"]

#docker run -it -p 3000:3000 --link db-data --name serv server
