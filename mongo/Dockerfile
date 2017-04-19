FROM debian:8.7

RUN apt-get update && apt-get install -y \
        git \
        wget \
        curl \
	software-properties-common \
	apt-transport-https \
	lsb-release \
	ca-certificates 
	
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
RUN echo "deb http://repo.mongodb.org/apt/debian jessie/mongodb-org/3.4 main" | tee /etc/apt/sources.list.d/mongodb-org-3.4.list
RUN apt-get update && apt-get install -y mongodb-org && \
	rm -rf /var/lib/apt/lists/* /var/cache/debconf && \
	apt-get clean

EXPOSE 27017
ENTRYPOINT exec /usr/bin/mongod --config /etc/mongod.conf

