FROM coppit/filebot
COPY ./filebot.sh /files/filebot.sh
RUN chmod +x /files/filebot.sh

ARG OPENSUBTITLES_LOGIN
ARG OPENSUBTITLES_PASSWORD
ARG OPENSUBTITLES_LANG

RUN sed -i -e 's/OPENSUBTITLES_USER=""/OPENSUBTITLES_USER="'${OPENSUBTITLES_LOGIN}'"/' /files/filebot.conf && \
    sed -i -e 's/OPENSUBTITLES_PASSWORD=""/OPENSUBTITLES_PASSWORD="'${OPENSUBTITLES_PASSWORD}'"/' /files/filebot.conf && \
    sed -i -e 's/SUBTITLE_LANG=""/SUBTITLE_LANG="'${OPENSUBTITLES_LANG}'"/' /files/filebot.conf
