FROM centos:centos7

RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all
RUN yum -y install redis; yum clean all

RUN mkdir -p /redis
COPY ./redis.conf .
COPY ./slave.conf .
COPY ./sentinel.conf .

# Start Master
RUN [ "redis-server", "/redis.conf" ]
# Start Slave
RUN [ "redis-server", "/slave.conf" ]
EXPOSE 6379
CMD [ "redis-server", "/sentinel.conf", "--sentinel"]
