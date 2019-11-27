FROM centos:centos7

ENV container docker

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
 && rpm -Uvh https://rpms.remirepo.net/enterprise/remi-release-7.rpm

# normal updates
RUN yum -y update

# # php && httpd
RUN yum -y install php72 php72-php php72-php-opcache php72-php-bcmath php72-php-cli php72-php-common php72-php-gd php72-php-intl php72-php-json php72-php-mbstring php72-php-pdo php72-php-pdo-dblib php72-php-pear php72-php-pecl-mcrypt php72-php-xmlrpc php72-php-xml php72-php-mysql php72-php-soap php72-php-pecl-zip php72-php-pecl-mongodb php72-php-pecl-xdebug php72-php-pecl-yaml
RUN yum -y install httpd mod_ssl

COPY v-host.conf /etc/httpd/conf.d/
# create webserver-default directory
RUN mkdir -p /var/www/dev.na
RUN mkdir -p /var/www/cert
COPY cert/server.crt /var/www/cert
COPY cert/server.key /var/www/cert

COPY cert/server.csr /var/www/cert


CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]
