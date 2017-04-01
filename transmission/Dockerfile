FROM linuxserver/transmission

RUN mkdir -p /data/Media/Downloads && mkdir /data/Media/Torrents
RUN mkdir -p /opt/mediacenter/transmission-config
COPY ./filebot.sh /config/filebot.sh
RUN chmod +x /config/filebot.sh
COPY ./settings.json /config/settings.json