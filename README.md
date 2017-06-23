# .docker

Some dockerfiles

Inspiration taken from @jessfraz's
[Dockerfiles](https://www.github.com/jessfraz)


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



