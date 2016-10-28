FROM phusion/baseimage:0.9.17
MAINTAINER El-ad Blech <elie@theinfamousblix.com.com>

ENV DATA_DIR=/data \
    BIND_USER=bind

RUN apt-get -qq update && apt-key update && apt-get -y install python-software-properties bind9 bind9utils

COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod 755 /sbin/entrypoint.sh

# Final cleanup
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 53/udp 53/tcp
VOLUME /data

# Use baseimage-docker's init system.
#CMD ["/sbin/my_init"]

ENTRYPOINT ["/sbin/entrypoint.sh"]
CMD ["/usr/sbin/named"]
