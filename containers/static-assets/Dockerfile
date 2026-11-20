FROM alpine:3.24

RUN apk update && apk upgrade
RUN apk add bash
COPY ./plugins /plugins
COPY ./themes /themes
COPY ./pkg-mgr /pkg-mgr
