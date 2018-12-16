# Linux API Infrastructure

This describes steps necessary to set up API infrastructure on a Linux server, namely DigitalOcean's Ubuntu droplet.

## 1. Set up Ubuntu server

[Initial Server Setup with Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

1. Create user with sudo administrative priviledges.
2. Set up firewall to enable SSH access.
3. Set up public key authentication.
4. Disable password authentication.

## 2. Install MongoDB

[How to Install and Secure MongoDB on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-mongodb-on-ubuntu-16-04)

1. Install MongoDB.
2. Create administrative user.
4. Enable authentication.
5. Create database and it's users.

## 4. Install Nginx

[How To Install Nginx on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)

1. Install Ngingx.
2. Set up server block for the API subdomain.
3. [Enable CORS](https://enable-cors.org/server_nginx.html) for API consumers.
4. [Enable HTTPS, redirect from HTTP.](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04)

# 5. Install Node.js

[How To Set Up a Node.js Application for Production on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04)

1. Install Node.js.
2. Install PM2 for managing production node apps.
3. Configure Nginx as a reverse proxy for node app on localhost.

# 5. Set up git deployment

[How To Set Up Automatic Deployment with Git with a VPS](https://www.digitalocean.com/community/tutorials/how-to-set-up-automatic-deployment-with-git-with-a-vps)

1. Init bare repo in `/var/repo/<appname>.git`.
2. Create dir for node app distribution files (deployment dir) in `/opt/<appname>`.
3. Change user of both directories to non-sudo user.
4. [Create `post-receive` hook.](https://gist.github.com/nikdo/bbed8087f13d9c0f16888d1ba95bbb96)
5. Set `NODE_ENV` environment variable to `production` and other variables necessary for the app in `var/repo/<appname>.git/hooks/.env` file.