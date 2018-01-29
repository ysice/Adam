FROM debian:stretch-slim

RUN apt-get update && apt-get install -y curl \
    && curl https://getcaddy.com | bash -s personal http.cache,http.proxyprotocol,http.expires,http.filter,http.forwardproxy,http.git,http.grpc,http.ipfilter,http.locale,http.nobots,http.prometheus,http.ratelimit,http.realip \
 && rm -rf /var/lib/apt/lists/* 

RUN /usr/local/bin/caddy -version

RUN /usr/local/bin/caddy -plugins

EXPOSE 80 443 2015

VOLUME /root/.caddy /proxy
WORKDIR /proxy

COPY index.html /proxy/index.html
COPY Caddyfile /etc/Caddyfile

ENV TZ=Asia/Shanghai

ENTRYPOINT [ "/usr/local/bin/caddy" ]
CMD [ "--conf", "/etc/Caddyfile", "--log", "stdout"]
