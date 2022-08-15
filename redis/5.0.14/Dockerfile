FROM amd64/centos:7.9.2009

ENV REDIS_VERSION="5.0.14" \
    SUMMARY="Redis in-memory data structure store, used as database, cache and message broker" \
    DESCRIPTION="Redis $REDIS_VERSION available as container, is an advanced key-value store. \
It is often referred to as a data structure server since keys can contain strings, hashes, lists, \
sets and sorted sets. You can run atomic operations on these types, like appending to a string; \
incrementing the value in a hash; pushing to a list; computing set intersection, union and difference; \
or getting the member with highest ranking in a sorted set. In order to achieve its outstanding \
performance, Redis works with an in-memory dataset. Depending on your use case, you can persist \
it either by dumping the dataset to disk every once in a while, or by appending each command to a log."

# install Redis server
RUN groupadd -g 1001 redis \
 && useradd -u 1001 -r -g 1001 -s /sbin/nologin -c "Default Application User" redis \
 && yum install -y epel-release \
 && yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm \
 && yum-config-manager --enable remi \
 && rpmkeys --import /etc/pki/rpm-gpg/RPM-GPG-KEY-remi \
 && yum install -y \
     "redis-${REDIS_VERSION}" \
 && yum clean all

CMD ["/bin/bash"]
