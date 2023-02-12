FROM alpine:edge

RUN set -x &&\
  apk add --update --upgrade alpine-sdk doas && apk upgrade &&\
  echo 'https://dl-cdn.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories &&\
  adduser -D skilld &&\
  echo "permit nopass skilld" >> /etc/doas.d/skilld.conf &&\
  echo "permit nopass 0" >> /etc/doas.d/root.conf &&\
  ln -s doas /usr/bin/sudo &&\
  addgroup skilld abuild &&\
  mkdir -p /var/cache/distfiles &&\
  chmod a+w /var/cache/distfiles &&\
  chgrp abuild /var/cache/distfiles &&\
  chmod g+w /var/cache/distfiles &&\
  sudo -u skilld abuild-keygen -a -i -n &&\
  rm -fr /var/cache/apk/*

VOLUME /mnt
WORKDIR /mnt
USER skilld
CMD ["/bin/ash"]
