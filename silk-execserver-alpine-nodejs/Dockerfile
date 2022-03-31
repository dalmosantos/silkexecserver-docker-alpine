#====================================
# Alpine Linux - NodeJS Dockerfile
#====================================

FROM adoptopenjdk/openjdk8:alpine-jre

USER root

RUN (apk fix --no-cache || echo "cannot fix.") && \
    (apk upgrade --no-cache || echo "cannot upgrade.") && \
    (apk cache -v  clean || echo "cannot clean cache." ) && \
     apk add --no-cache --update --upgrade bash git tzdata jq openssl \
     unzip sudo shadow dbus-x11 dumb-init mesa-gl mesa-dri-swrast ttf-freefont curl xvfb \
     nodejs npm libarchive-tools ttf-dejavu ncurses msttcorefonts-installer fontconfig && \
     rm -rf /tmp/* /var/cache/apk /var/lib/apk /etc/apk/cache && \
     update-ms-fonts && \
     fc-cache -f && \
     npm install -g --cache /tmp newman jest jasmine ava mocha chai  && \
     rm -rf /tmp/* /var/log /*.log /var/cache/apk /var/lib/apk /etc/apk/cache

WORKDIR /tmp

CMD ["/bin/sh"]
