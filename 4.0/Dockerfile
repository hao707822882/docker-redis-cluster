FROM redis:4.0

MAINTAINER Tommy Chen <tommy351@gmail.com>

RUN apt-get -y update && \
  apt-get install -y --no-install-recommends --no-install-suggests ruby supervisor rubygems wget && \
  rm -rf /var/lib/apt/lists/* && \
  gem install redis

RUN wget https://raw.githubusercontent.com/antirez/redis/4.0/src/redis-trib.rb -O /redis-trib.rb && \
  chmod +x /redis-trib.rb

COPY start.sh /
VOLUME /data
WORKDIR /

ENV CLUSTER_ANNOUNCE_IP 127.0.0.1

EXPOSE 7000 7001 7002 7003 7004 7005

CMD ["/start.sh"]