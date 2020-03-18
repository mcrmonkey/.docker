# docker-files

Some docker files for things

Inspiration taken from @jessfraz's [Dockerfiles](https://www.github.com/jessfraz)


## Containers


### gcal

gcalcli in a container.

You'll need to pass the auth file through for this to work
Quick example:

    docker run --rm -it -v /etc/localtime:/etc/localtime:ro -v "${HOME}/.gcalcli:/home/gcal" mcrmonkey/gcalcli agenda


will return your agenda.

See https://github.com/insanum/gcalcli for more info and options


### mutt

The mutt mail program in a container

Its setup to talk to gmail. see readme within for whats needed

Run like this:

    docker run -it --rm -e GMAIL -e GMAIL_NAME -e GMAIL_PASS -e GMAIL_FROM -e GPG_ID -e IMAP_SERVER -e SMTP_SERVER \
    -v "${HOME}/.gnupg:/home/user/.gnupg:ro" -v /etc/localtime:/etc/localtime:ro mcrmonkey/mutt


### rainbowstream

TUI for twitter

This does some stuff with oauth tokens which it saves to disk. If you dont make
any allowances for it they will disappear when the container is rm'd


### vscode

A code editor

Map your `.config` dir to `/home/user/.config` to keep config across container
runs

### atom

The other code editor


### gopass

gopass in a container.
