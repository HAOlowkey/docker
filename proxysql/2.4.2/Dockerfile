FROM amd64/centos:7.9.2009

ENV PROXYSQL_VERSION="2.4.2" \
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

CMD ["/bin/bash"]
