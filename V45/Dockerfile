FROM ubuntu:18.04

WORKDIR /root/

RUN apt-get update \
    && apt-get install -y dpkg curl gpg gcc-4.8 \
    && apt-get clean all \
    && echo 'deb http://download.opensuse.org/repositories/home:/knonomura/xUbuntu_18.04/ /' | tee /etc/apt/sources.list.d/home:knonomura.list \
    && curl -fsSL https://download.opensuse.org/repositories/home:knonomura/xUbuntu_18.04/Release.key | gpg --dearmor | tee /etc/apt/trusted.gpg.d/home:knonomura.gpg > /dev/null \
    && apt-get update \
    && apt-get install griddb-c-client

VOLUME /var/lib/gridstore
WORKDIR /var/lib/gridstore
COPY start-griddb.sh /
RUN chmod a+x /start-griddb.sh
CMD ["/bin/bash", "/start-griddb.sh"]
