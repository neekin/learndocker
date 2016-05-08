FROM ubuntu:14.04
MAINTAINER NeeKin "njgzs360@gmail.com"
ENV REFRESHED_AT 2016-05-08
RUN apt-get -yqq update 
RUN apt-get -yqq install nodejs git-core curl zlib1g-dev build-essential 
RUN apt-get -yqq install  libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3
RUN apt-get -yqq install  libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common
RUN apt-get clean
RUN git clone git://github.com/sstephenson/rbenv.git /root/.rbenv
RUN git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build 
RUN /root/.rbenv/plugins/ruby-build/install.sh
ENV PATH /root/.rbenv/bin:$PATH
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh # or /etc/profile
RUN echo 'eval "$(rbenv init -)"' >> .bashrc
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc
ENV CONFIGURE_OPTS --disable-install-doc
ADD ./ruby-versions.txt  /root/ruby-versions.txt
RUN xargs -L 1 rbenv install  < /root/ruby-versions.txt
RUN bash -l -c 'for v in $(cat /root/ruby-versions.txt); do rbenv global $v;  gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/;gem install jekyll; done' 
VOLUME  /data
VOLUME /var/www/html
WORKDIR /data
ENTRYPOINT ["jekyll","build","--destination=/var/www/html"]
