# DO NOT ALTER OR REMOVE COPYRIGHT NOTICES OR THIS HEADER.
# 
# Copyright (c) 2015 Oracle and/or its affiliates. All rights reserved.
# 
FROM oracle/openjdk:latest

MAINTAINER Bruno Borges <bruno.borges@oracle.com>

ENV VERSION "3.5.2"
ENV PACKAGE "kv-ce"
ENV EXTENSION "zip"
ENV BASE_URL "http://download.oracle.com/otn-pub/otn_software/nosql-database/"
ENV KVHOME /kv-3.5.2
ENV KVROOT /var/kvroot
ENV _JAVA_OPTIONS -XX:+PrintCommandLineFlags -Djava.security.egd=file:/dev/./urandom
 
RUN yum -y install unzip && \
    mkdir "${KVROOT}" && \
    curl -OLs "${BASE_URL}/${PACKAGE}-${VERSION}.${EXTENSION}" && \
    unzip "${PACKAGE}-${VERSION}.${EXTENSION}" && \
    rm "${PACKAGE}-${VERSION}.${EXTENSION}" && \
    yum -y remove unzip && yum -y clean all && rm -rf /var/cache/yum/*
 
WORKDIR "/kv-${VERSION}"
 
EXPOSE 5000 5001 5010-5020

CMD ["java", "-jar", "lib/kvstore.jar", "kvlite"]
