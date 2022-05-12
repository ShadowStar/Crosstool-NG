FROM alpine:3.15
ARG CTNG_UID=1000
ARG CTNG_GID=1000
RUN addgroup -g $CTNG_GID ctng
RUN adduser -D -h /home/ctng -G ctng -u $CTNG_UID -s /bin/bash ctng
# Activate community and testing repositories
RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories
RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/community >> /etc/apk/repositories
RUN apk update
RUN apk add alpine-sdk wget xz git bash autoconf automake bison flex texinfo help2man gawk libtool ncurses-dev gettext-dev python3-dev rsync
RUN wget -O /sbin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.2.5/dumb-init_1.2.5_x86_64
RUN chmod a+x /sbin/dumb-init
RUN echo 'export PATH=/opt/ctng/bin:$PATH' >> /etc/profile
ENTRYPOINT [ "/sbin/dumb-init", "--" ]
