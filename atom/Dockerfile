#USAGE:
#	docker run -v /tmp/.X11-unix:/tmp/.X11-unix \
#		-e DISPLAY=unix$DISPLAY atom
#
# Original by Jessfraz

# Base docker image
FROM debian:buster
LABEL maintainer "ant <git@manchestermonkey.co.uk>"

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -qq && apt-get install -qq apt-transport-https ca-certificates gnupg wget --no-install-recommends

# Add the atom debian repo
RUN wget -qO- https://packagecloud.io/AtomEditor/atom/gpgkey | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'

# Install dependencies
RUN apt-get update -qq  && apt-get install -qq \
	atom \
	git \
	gconf2 \
	gconf-service \
	gvfs-bin \
	libasound2 \
	libcap2 \
	libgconf-2-4 \
	libgtk2.0-0 \
	libnotify4 \
	libnss3 \
	libxkbfile1 \
	libxss1 \
	libxtst6 \
	libx11-xcb-dev \
	xdg-utils \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/* && mkdir -p /root/.atom

ADD config.cson /root/.atom/config.cson

# Autorun atom
ENTRYPOINT [ "atom", "--foreground" ]
