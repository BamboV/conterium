FROM coppit/filebot

RUN mkdir -p /var/www/filebot

COPY ./index.php /var/www/filebot
COPY ./filebot.sh /files/filebot.sh
COPY ./start.sh /files/start.sh

RUN chmod +x /files/filebot.sh && chmod +x /files/start.sh

RUN apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -y \
        php7.0 \
        && \
    apt-get clean

ARG OPENSUBTITLES_LOGIN
ARG OPENSUBTITLES_PASSWORD
ARG OPENSUBTITLES_LANG

RUN sed -i -e 's/OPENSUBTITLES_USER=""/OPENSUBTITLES_USER="'${OPENSUBTITLES_LOGIN}'"/' /files/filebot.conf && \
    sed -i -e 's/OPENSUBTITLES_PASSWORD=""/OPENSUBTITLES_PASSWORD="'${OPENSUBTITLES_PASSWORD}'"/' /files/filebot.conf && \
    sed -i -e 's/SUBTITLE_LANG=""/SUBTITLE_LANG="'${OPENSUBTITLES_LANG}'"/' /files/filebot.conf
