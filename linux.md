# Linux

Linux cheat sheet.


## Uncomplicated Firewall

```
ufw status               # firewall rules
ufw app list             # available apps
ufw allow <app-or-port>  # allow app or port
```


## Systemd

```
systemctl status <service>   # check service status
systemctl stop <service>     # stop
systemctl start <service>    # start
systemctl restart <service>  # restart
systemctl reload <service>   # reload without restarting
systemctl disable <service>  # disable start during boot
systemctl enable <service>   # enable start during boot
```

## Nginx

```
vim /etc/nginx/sites-available/<sitename> # server block config
```

## PM2

```
pm2 list             # list currently running processes
pm2 info <app>.      # show info about running app
pm2 start <file.js>  # start process
pm2 restart <app>    # restart process
pm2 save             # save current processes (start on boot)
pm2 monit            # monitor all processes
pm2 log <app>        # tails app log
systemctl status pm2-<username>  # show systemd process
```

## Ubuntu packages

```
apt update                  # update packages
apt install <package-name>  # install package
```
