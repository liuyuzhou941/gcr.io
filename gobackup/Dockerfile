FROM alpine
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories


RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub
RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.35-r0/glibc-2.35-r0.apk
RUN apk add glibc-2.35-r0.apk
RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.35-r0/glibc-bin-2.35-r0.apk
RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.35-r0/glibc-i18n-2.35-r0.apk
RUN apk add glibc-bin-2.35-r0.apk glibc-i18n-2.35-r0.apk
RUN /usr/glibc-compat/bin/localedef -i en_US -f UTF-8 en_US.UTF-8


ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8

ADD gobackup.tar.gz /usr/local/
RUN ln -s /usr/local/gobackup  /usr/bin
RUN  gobackup -v
RUN apk add --no-cache  mysql-client
RUN  mysqldump --help
RUN apk add  --no-cache  postgresql-client
RUN pg_dump --help
