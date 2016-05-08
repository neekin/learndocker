FROM ubuntu:14.04
MAINTAINER NeeKin "njgzs360@gmail.com"
ENV REFRESHED_AT 2016-05-07
RUN apt-get -yqq update && apt-get -yqq install ruby ruby-dev build-essential redis-tools
RUN gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/
RUN gem install --no-rdoc --no-ri sinatra json redis
RUN mkdir -p /opt/webapp
EXPOSE 4567

CMD   ["/opt/webapp/bin/webapp"]
