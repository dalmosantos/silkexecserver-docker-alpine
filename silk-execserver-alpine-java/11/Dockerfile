#====================================
# Alpine Linux - OpenJDK11 Dockerfile
#====================================

FROM adoptopenjdk/openjdk11:jdk-11.0.14.1_1-alpine-slim

USER root

RUN (apk fix --no-cache || echo "cannot fix.") && \
    (apk upgrade --no-cache || echo "cannot upgrade.") && \
    (apk cache -v  clean || echo "cannot clean cache." ) && \
     apk add --no-cache --update --upgrade bash git openjdk8-jre tzdata jq openssl \
     unzip sudo shadow dbus-x11 dumb-init mesa-gl mesa-dri-swrast ttf-freefont curl xvfb libarchive-tools ttf-dejavu ncurses msttcorefonts-installer fontconfig && \
     update-ms-fonts && \
     fc-cache -f && \
     # Install maven
    mkdir -p /usr/share/maven /usr/share/maven/ref && \
    curl https://dlcdn.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.tar.gz -o /tmp/apache-maven.tar.gz && \
    tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 && \
    rm -f /tmp/apache-maven.tar.gz && \
    ln -s /usr/share/maven/bin/mvn /usr/bin/mvn && \
    rm -rf /tmp/* /var/log /*.log /var/cache/apk /var/lib/apk /etc/apk/cache
    #echo "securerandom.source=file:/dev/urandom" >> /usr/lib/jvm/default-jvm/jre/lib/security/java.security
ENV MVN_HOME=usr/share/maven

WORKDIR /tmp

CMD ["/bin/sh"]
