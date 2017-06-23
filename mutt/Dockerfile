FROM alpine:edge
LABEL maintainer "ant <git@manchestermonkey.co.uk>"

RUN addgroup -g 1000 user \
	&& adduser -D -h /home/user -G user -u 1000 user

RUN apk --no-cache add \
	ca-certificates \
	elinks \
	git \
	gnupg1 \
	lynx \
	mutt \
	mutt-doc \
	vim

# a browser for html readings
ENV BROWSER lynx

USER user
ENV HOME /home/user
ENV TERM xterm-256color
RUN mkdir -p $HOME/.mutt/cache/headers $HOME/.mutt/cache/bodies \
	&& touch $HOME/.mutt/certificates

# vim settings
RUN git clone --depth 1 https://github.com/mcrmonkey/.vim.git $HOME/.vim \
	&& git clone --depth 1 https://github.com/altercation/vim-colors-solarized $HOME/.vim/bundle/vim-colors-solarized \
	&& cp $HOME/.vim/vimrc $HOME/.vimrc

ENV LANG C.UTF-8

ADD entrypoint.sh /entrypoint.sh
ADD .mutt $HOME/.mutt

ENTRYPOINT ["/entrypoint.sh"]

CMD ["mutt", "-F", "~/.mutt/muttrc"]
