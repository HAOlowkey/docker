FROM amd64/centos:7.9.2009

ENV MYSQL_VERSION="8.0.26" \
    SUMMARY="MySQL 8.0 SQL database server" \
    DESCRIPTION="MySQL is a multi-user, multi-threaded SQL database server. The container \
image provides a containerized packaging of the MySQL mysqld daemon and client application. \
The mysqld server daemon accepts connections from clients and provides access to content from \
MySQL databases on behalf of the clients."

# install mysql server
RUN groupadd -g 1001 mysql \
  && useradd -u 1001 -r -g 1001 -s /sbin/nologin -c "Default Application User" mysql \
  && yum install -y https://repo.mysql.com/mysql80-community-release-el7.rpm \
  && yum-config-manager --enable mysql80-server \
  && rpmkeys --import /etc/pki/rpm-gpg/RPM-GPG-KEY-mysql \
  && yum install -y \
      "mysql-community-server-${MYSQL_VERSION}" \
      "mysql-community-client-${MYSQL_VERSION}" \
      "mysql-community-client-plugins-${MYSQL_VERSION}" \
      "mysql-community-libs-${MYSQL_VERSION}" \
  && yum clean all

CMD ["/bin/bash"]
