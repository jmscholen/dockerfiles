FROM centos:centos7

MAINTAINER Jeff Scholen <jmscholen@gmail.com>

ENV RUBY_MAJOR 2.2
ENV RUBY_VERSION 2.2.4

ENV JAVA_HOME=/usr/bin/java


RUN  yum update -y \
  && yum install -y gcc make \
  && yum clean all

RUN yum install -y mysql-devel \
  && yum clean all

# Build ruby
RUN yum install -y openssl-devel libyaml libyaml-devel libffi \
  libffi-devel readline-devel zlib zlib-devel gdbm gdbm-devel \
  ncurses ncurses-devel bzip2 automake autoconf \
  && mkdir -p /usr/src/ruby \
  && curl -SL "https://cache.ruby-lang.org/pub/ruby/$RUBY_MAJOR/ruby-$RUBY_VERSION.tar.gz" \
  | tar -xzC /usr/src/ruby --strip-components=1 \
  && cd /usr/src/ruby \
  && autoconf \
  && ./configure --disable-install-doc \
  && make -j"$(nproc)" \
  && make install \
  && (yum remove openssl-devel libyaml-devel libffi-devel readline-devel zlib-devel gdbm-devel ncurses-devel bzip2 automake autoconf || exit 0) \
  && yum clean all \
  && rm -r /usr/src/ruby 

RUN yum install -y \
    wget \
    ruby-devel \
    libxml2 \
    libxml2-devel \
    libxslt \ 
    libxslt-devel  \
    net-tools \
  && yum clean all

RUN yum install -y java-1.7.0-openjdk-devel \
    epel-release \
  && yum clean all

RUN yum install -y nodejs \
 && yum clean all

RUN yum groups mark install "Development Tools" \
    yum groups mark convert "Development Tools" \
    yum groupinstall "Development Tools" \
  && yum clean all

RUN yum install -y qt-devel \
  && yum clean all

RUN yum install -y git \
  && yum clean all

RUN yum upgrade -y \
  && yum install -y gcc-c++
