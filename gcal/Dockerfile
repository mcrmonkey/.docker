FROM alpine:latest
LABEL maintainer "ant <git@manchestermonkey.co.uk>"

ENV HOME /home/gcal

RUN apk --no-cache add \
	python \
	python-dev \
	py2-pip \
	build-base \
	&& adduser -S gcal \
	&& chown -R gcal $HOME \
	&& pip install vobject parsedatetime gcalcli

WORKDIR $HOME
USER gcal

ENTRYPOINT [ "gcalcli" ]
