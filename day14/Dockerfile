FROM centos:latest

RUN cd /etc/yum.repos.d/  && yum install -y wget && wget http://mirrors.aliyun.com/repo/Centos-8.repo && \
    yum clean all && mv Centos-8.repo CentOS-Base.repo && yum makecache && yum update  -y

RUN yum install -y gcc && yum install -y gcc-c++
    

RUN yum install -y make && \
    wget https://download.redis.io/releases/redis-6.0.9.tar.gz && \
    mkdir -p /usr/src/redis && \
    tar -xzf redis-6.0.9.tar.gz -C /usr/src/redis --strip-components=1 

RUN cd /usr/src/redis && make && make PREFIX=/usr/src/bin install && \
    cp /usr/src/redis/redis.conf /usr/src/bin/redis.conf

CMD ["/bin/sh", "-c", "while true; do sleep 3600; done"]
