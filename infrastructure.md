# Infrastructure

## NPM

*devDependencies* are [not installed in production](http://stackoverflow.com/a/22004559). That means most hosting providers (including OpenShift) won't install it during git push deployment.


## Running Express app publicly

Node app has to specify not only port, but also host. If it meant to be accessible on domain, the domain has to be specified in the app. The other alternative is a local reverse proxy server, that will proxy all calls to domain to localhost with specific port.