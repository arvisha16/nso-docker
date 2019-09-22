FROM debian:buster

ARG NSO_INSTALL_FILE

COPY $NSO_INSTALL_FILE /tmp/nso
RUN apt-get update \
  && apt-get install -qy \
     default-jre-headless \
     iputils-ping \
     iputils-tracepath \
     less \
     liblog4cplus-1.1-9 \
     libuv1 \
     libxml2-utils \
     logrotate \
     openssh-client \
     openssl \
     python3.7 \
     snmp \
     tcpdump \
     telnet \
     vim-tiny \
  && update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 3 \
  && sh /tmp/nso --system-install --non-interactive --run-dir /ncs --log-dir /log \
  && apt-get -qy autoremove \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /root/.cache \