FROM debian:8.7

RUN apt-get update && apt-get install -y \
        git \
	wget

RUN echo "deb http://ftp.ua.debian.org/debian jessie-backports main" >> /etc/apt/sources.list

RUN apt-get update && apt-get install -t jessie-backports -y \
        openjdk-8-jre-headless \
        ca-certificates-java \
	openjdk-8-jre && \
	rm -rf /var/lib/apt/lists/* /var/cache/debconf && \
	apt-get clean

 
RUN wget http://apache.mirror1.spango.com/zookeeper/zookeeper-3.4.9/zookeeper-3.4.9.tar.gz -O /usr/src/zookeeper-3.4.9.tar.gz
RUN tar -xzf /usr/src/zookeeper-3.4.9.tar.gz -C /usr/src/ && mkdir /usr/src/zookeeper-3.4.9/data
 

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64
ENV JRE_HOME /usr/lib/jvm/java-8-openjdk-amd64/jre


ENTRYPOINT ["/usr/src/zookeeper-3.4.9/bin/zkServer.sh"]
CMD ["start-foreground"]


