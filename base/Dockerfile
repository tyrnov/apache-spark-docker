FROM java:8

MAINTAINER Artem Tyrnov <tyrnov@protonmail.com>

ENV ENABLE_INIT_DAEMON true
ENV INIT_DAEMON_BASE_URI http://identifier/init-daemon
ENV INIT_DAEMON_STEP spark_master_init

ENV SPARK_VERSION=2.2.0
ENV HADOOP_VERSION=2.7

COPY wait-for-step.sh /
COPY execute-step.sh /
COPY finish-step.sh /

ADD https://gist.githubusercontent.com/tyrnov/ab3d1b07c68945a884ea588701cff57a/raw/aed8dc273798acd3380fafae93326f3e9a4fe50e/apt-get-install /usr/bin/ 
RUN chmod +x /usr/bin/apt-get-install

RUN apt-get-install -y curl \
      && chmod +x *.sh \
      && wget http://d3kbcqa49mib13.cloudfront.net/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
      && tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
      && mv spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark \
      && rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
      && cd /

RUN apt-get-install -y python3 python3-setuptools python3-pip

ENV PYTHONHASHSEED 1
