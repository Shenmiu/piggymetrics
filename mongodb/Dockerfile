FROM mongo:3.7

ADD init.sh /init.sh
ADD ./dump /

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
     && echo "Asia/Shanghai" > /etc/timezone

RUN \
 chmod +x /init.sh && \
 apt-get update && apt-get dist-upgrade -y --force-yes && apt-get install dos2unix && \
 apt-get install psmisc -y -q && \
 apt-get autoremove -y && apt-get clean && \
 rm -rf /var/cache/* && rm -rf /var/lib/apt/lists/* && \
 dos2unix -n /init.sh /initx.sh && chmod +x /initx.sh

ENTRYPOINT ["/initx.sh"]