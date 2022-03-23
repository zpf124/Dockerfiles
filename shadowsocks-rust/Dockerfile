FROM ghcr.io/shadowsocks/ssserver-rust:latest

USER root

RUN cd /tmp && \
  TAG=$(wget -qO- https://api.github.com/repos/teddysun/xray-plugin/releases/latest | grep tag_name | cut -d '"' -f4) && \
  wget https://github.com/teddysun/xray-plugin/releases/download/$TAG/xray-plugin-linux-amd64-$TAG.tar.gz && \
  tar -xf *.gz && \
  rm *.gz && \
  mv xray-plugin* /usr/bin/xray-plugin && \
  chmod +x /usr/bin/xray-plugin

USER nobody

ENTRYPOINT [ "ssserver", "--log-without-time" ]
CMD [ "-c", "/etc/shadowsocks-rust/config.json" ]
