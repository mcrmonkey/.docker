FROM alpine:latest as builder

ENV GPVER 1.8.6
ENV GPPLAT linux
env GPARCH amd64

ADD https://github.com/gopasspw/gopass/releases/download/v${GPVER}/gopass-${GPVER}-${GPPLAT}-${GPARCH}.tar.gz /tmp/
RUN tar -zxf /tmp/gopass-${GPVER}-${GPPLAT}-${GPARCH}.tar.gz
RUN mv /gopass-${GPVER}-${GPPLAT}-${GPARCH} gopass

FROM alpine:latest
LABEL maintainer "ant <git@manchestermonkey.co.uk>"

COPY --from=BUILDER /gopass/gopass /usr/bin/gopass

RUN apk add --no-cache gnupg bash xclip

ENTRYPOINT ["/usr/bin/gopass"]

