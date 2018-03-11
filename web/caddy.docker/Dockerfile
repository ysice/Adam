FROM debian:stretch-slim

RUN apt-get update && apt-get install -y --no-install-recommends curl ca-certificates \
 && wget https://caddyserver.com/download/linux/amd64?plugins=dns,docker,dyndns,hook.service,http.authz,http.cache,http.cgi,http.cors,http.datadog,http.expires,http.filemanager,http.filter,http.forwardproxy,http.git,http.hugo,http.ipfilter,http.locale,http.login,http.mailout,http.minify,http.nobots,http.prometheus,http.proxyprotocol,http.ratelimit,http.realip,http.reauth,http.restic,http.upload,http.webdav,net&license=personal -O /usr/local/bin/caddy  \
 && rm -rf /var/lib/apt/lists/* 

RUN /usr/local/bin/caddy -version

RUN /usr/local/bin/caddy -plugins

EXPOSE 80 443

VOLUME /root/.caddy /proxy
WORKDIR /proxy

COPY index.html /proxy/index.html
COPY Caddyfile /etc/Caddyfile

ENV TZ=Asia/Shanghai

ENTRYPOINT [ "/usr/local/bin/caddy" ]
CMD [ "--conf", "/etc/Caddyfile", "--log", "stdout"]
