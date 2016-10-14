FROM centos:centos7

MAINTAINER Jeff Scholen <jmscholen@gmail.com>

ARG JAVA_VERSION=7
ARG JAVA_RELEASE=JDK

ENV JAVA_HOME=/usr

RUN \
    yum update -y && \
    yum install -y \
    wget \
    gcc \
    ruby-devel \
    libxml2 \
    libxml2-devel \
    libxslt \ 
    libxslt-devel #\
    pkg="java-1.$JAVA_VERSION.0-openjdk"; \
    if [ "$JAVA_RELEASE" = "JDK" ]; then \
	pkg="$pkg-devel"; \
    else \
	pkg="$pkg-headless"; \
    fi; \

    yum install -y "$pkg" && \

    yum install epel-release \
    nodejs \
    yum groupinstall "C Development Tools and Libraries" \
    yum install mesa-libGL-devel \
    yum clean all

RUN yum install -y qt-devel
