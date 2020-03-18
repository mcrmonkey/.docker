FROM alpine:latest
LABEL maintainer "ant <git@manchestermonkey.co.uk>"

RUN apk --no-cache add \
	build-base ca-certificates \
	freetype freetype-dev \
	openjpeg-dev zlib-dev \
	python3 py3-pillow && \
	pip3 install --upgrade pip && \
	pip3 install rainbowstream


ENTRYPOINT [ "rainbowstream" ]
