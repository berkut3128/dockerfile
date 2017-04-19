FROM debian:8.7

RUN apt-get update && apt-get install -y \
        git \
        wget \
        curl \
	software-properties-common \
	apt-transport-https \
	lsb-release \
	ca-certificates 
	
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E0C56BD4
RUN echo "deb http://repo.yandex.ru/clickhouse/trusty stable main" | tee /etc/apt/sources.list.d/clickhouse.list
RUN apt-get update && apt-get install -y \
	clickhouse-client \
	clickhouse-server-base \
	clickhouse-server-common && \
	rm -rf /var/lib/apt/lists/* /var/cache/debconf && \
	apt-get clean

RUN chown -R clickhouse /etc/clickhouse-server/


ENV CLICKHOUSE_CONFIG /etc/clickhouse-server/config.xml

ENTRYPOINT exec /usr/bin/clickhouse-server --config=${CLICKHOUSE_CONFIG}


