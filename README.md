# exim-gmail-relay

A very basic image for relaying your mail via gmail SMTP servers using Exim4.

Launch the container with your gmail credentials by specifying `EXIM_GMAIL_LOGIN` 
and `EXIM_GMAIL_PASSWORD` environment variables:

```console
$ docker run --name exim-gmail-relay      \
    -e EXIM_GMAIL_LOGIN=example@gmail.com \
    -e EXIM_GMAIL_PASSWORD=qwerty         \
    -d selim13/exim-gmail-relay:latest
```

Or just mount `/etc/exim/conf.d/authenticators.conf` as a volume and put your
credentials there.

You can always put your additional  configuration 
either to `/etc/exim/exim.conf` or to the following included files:
* `/etc/exim/conf.d/main.conf`
* `/etc/exim/conf.d/acl.conf`
* `/etc/exim/conf.d/routers.conf`
* `/etc/exim/conf.d/transports.conf`
* `/etc/exim/conf.d/retry.conf`
* `/etc/exim/conf.d/rewrite.conf`
* `/etc/exim/conf.d/authenticators.conf`
* `/etc/exim/conf.d/local_scan.conf`

## Environment variables 

### EXIM_RELAY_FROM_HOSTS
Sets `relay_from_hosts` host list which is used in acl checks.

Default value: `10.0.0.0/8 : 172.16.0.0/12 : 192.168.0.0/16`

### EXIM_GMAIL_LOGIN
Login for you gmail account.

### EXIM_GMAIL_PASSWORD
Password for you gmail account.