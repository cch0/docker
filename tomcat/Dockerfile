FROM centos:centos6
MAINTAINER CCH

# ==================
# variables
# ==================
ENV TOMCAT_MAJOR_VERSION 7
ENV TOMCAT_VERSION 7.0.55

# ==================
# update centos
# ==================
RUN yum update -y; yum clean all

# ==================
# install wget
# ==================
RUN yum -y install wget tar

# ==================
# download oracle java
# ==================
RUN wget -q --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" -O /tmp/jdk-linux-x64.rpm "http://download.oracle.com/otn-pub/java/jdk/7u67-b01/jre-7u67-linux-x64.rpm"

# ==================
# install java
# ==================
RUN rpm -Uvh /tmp/jdk-linux-x64.rpm

# ==================
# install apache httpd
# ==================
RUN yum install -y httpd

# ==================
# download tomcat
# ==================
RUN wget -q https://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR_VERSION}/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz -O /tmp/tomcat.tar.gz

# ==================
# prepare tomcat directory
# ==================
RUN mkdir /opt/tomcat

# ==================
# install tomcat
# ==================
RUN cd /tmp && tar zxf tomcat.tar.gz && mv apache-tomcat-${TOMCAT_VERSION} /opt/tomcat/apache-tomcat-${TOMCAT_VERSION} &&  cd /opt/tomcat && ln -s apache-tomcat-${TOMCAT_VERSION} latest


# ==================
# tomcat run script
# ==================
ADD run.sh /run.sh
RUN chmod +x /run.sh

CMD ["/run.sh"]



