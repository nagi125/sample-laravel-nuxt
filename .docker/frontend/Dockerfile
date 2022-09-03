FROM node:18.8-alpine

ENV LANG ja_JP.UTF-8
ENV TZ Asia/Tokyo

RUN apk update && \
    apk add git python3 python3-dev make g++

ENV TZ Asia/Tokyo

WORKDIR /app

CMD ["/bin/ash"]
