FROM java:openjdk-8-jdk

ENV spark_ver 2.4.0
ENV hadoop_ver 2.7

# Kubernetes needs
RUN apt-get update; \
    apt-get install socat

# Get Spark from US Apache mirror.
RUN mkdir -p /opt && \
    cd /opt && \
    curl http://ftp.halifax.rwth-aachen.de/apache/spark/spark-${spark_ver}/spark-${spark_ver}-bin-hadoop${hadoop_ver}.tgz | \
        tar -zx && \
    ln -s spark-${spark_ver}-bin-hadoop${hadoop_ver} spark && \
    echo Spark ${spark_ver} installed in /opt


ADD start-common.sh start-worker.sh start-master.sh /
RUN chmod +x /start-common.sh /start-master.sh /start-worker.sh
ENV PATH $PATH:/opt/spark/bin

