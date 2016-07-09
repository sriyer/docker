FROM python:344 

ENTRYPOINT [ "/marathon-lb/run" ]
#CMD        [ "sse", "-m", "http://master.mesos:8080", "--health-check", "--group", "external" ]
EXPOSE     80 81 443 9090

ENV LB_HOME /marathon-lb
WORKDIR /tmp
RUN mkdir -p $LB_HOME && yum -y install git wget \
    && wget https://github.com/mesosphere/marathon-lb/archive/v1.2.2.tar.gz \
    && tar -zxvf v1.2.2.tar.gz \
    && cd marathon-lb* && cp -ar . $LB_HOME \
    && mv $LB_HOME/Dockerfile $LB_HOME/Dockerfile.repo

#COPY  . $LB_HOME

RUN yum -y update && yum -y groupinstall 'Development Tools' && yum -y install runit procps readline readline-devel \
    build-essential pcre pcre-devel python3-dateutil socat iptables \
    && pip3 install -r $LB_HOME/requirements.txt \
    && $LB_HOME/build-haproxy.sh \
#   && apt-get remove -yf wget libssl-dev build-essential libpcre3-dev libreadline-dev \
#    && apt-get autoremove -yf \
#     && apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /marathon-lb


