FROM centos:centos7

RUN yum -y update \
        && yum -y install gcc make openssl openssl-devel \
	        which wget curl

WORKDIR /

RUN wget https://www.python.org/ftp/python/3.4.4/Python-3.4.4.tgz \
        && tar -zxvf Python-3.4.4.tgz

RUN cd /Python-3* && ./configure --with-ensurepip=install && make install
