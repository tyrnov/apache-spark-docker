FROM tyrnov/spark-base:2.2.0-hadoop2.7

MAINTAINER Artem Tyrnov <tyrnov@protonmail.com>

COPY master.sh /

ENV SPARK_MASTER_PORT 7077
ENV SPARK_MASTER_WEBUI_PORT 8080
ENV SPARK_MASTER_LOG /spark/logs

EXPOSE 8080 7077 6066

CMD ["/bin/bash", "/master.sh"]
