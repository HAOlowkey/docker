FROM amd64/centos:7.9.2009

ENV PROXYSQL_VERSION="2.4.2" \
    MYSQL_VERSION="8.0.26" \
    PROXYSQL_INITIALIZER_VERSION="1.0.5" \
    SUMMARY="High-performance MySQL proxy" \
    DESCRIPTION="ProxySQL is a high performance, high availability, protocol aware proxy for MySQL \
    and forks (like Percona Server and MariaDB). All the while getting the unlimited \
    freedom that comes with a GPL license."

# install proxysql
RUN echo $'[proxysql_repo] \n\
name=ProxySQL YUM repository \n\
baseurl=https://repo.proxysql.com/ProxySQL/proxysql-2.4.x/centos/$releasever \n\
enabled=1 \n\
gpgcheck=1 \n\
gpgkey=https://repo.proxysql.com/ProxySQL/proxysql-2.4.x/repo_pub_key \n '\
 > /etc/yum.repos.d/proxysql.repo \
 && rpmkeys --import https://repo.proxysql.com/ProxySQL/repo_pub_key \
 && yum install -y "proxysql-${PROXYSQL_VERSION}" \
 && yum clean all \
 && rm -rf /var/cache/yum

# install mysql-client
RUN yum install -y https://repo.mysql.com/mysql80-community-release-el7.rpm \
  && yum-config-manager --enable mysql80-server \
  && rpmkeys --import /etc/pki/rpm-gpg/RPM-GPG-KEY-mysql \
  && yum install -y \
      "mysql-community-client-${MYSQL_VERSION}" \
      "mysql-community-client-plugins-${MYSQL_VERSION}" \
      "mysql-community-libs-${MYSQL_VERSION}" \
  && yum clean all

CMD ["/bin/bash"]
