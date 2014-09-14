FROM centos:centos6
MAINTAINER CCH

# ==================
# variables
# ==================
ENV MONGODB_VERSION 2.6.4-1

# ==================
# update centos
# ==================
RUN yum update -y; yum clean all

# ==================
# install wget
# ==================
RUN yum -y install wget

# ==================
# install sudo
# ==================
RUN yum install sudo -y

# ==================
# prepare mongodb installation
# ==================
ADD mongodb.repo /etc/yum.repos.d/mongodb.repo

# ==================
# install mongo db
# ==================
#
# known issue
#
#/etc/init.d/mongod: line 54: ulimit: open files: cannot modify limit: Operation not permitted
#/etc/init.d/mongod: line 56: ulimit: max user processes: cannot modify limit: Operation not permitted
RUN yum -y install mongodb-org-${MONGODB_VERSION}

# ==================
# Define mountable directories
# ==================
VOLUME ["/data/db"]

# ==================
# start mongodb
# ==================
CMD ["/usr/bin/mongod"]
















