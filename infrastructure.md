# Infrastructure

## NPM

*devDependencies* are [not installed in production](http://stackoverflow.com/a/22004559). That means most hosting providers (including OpenShift) won't install it during git push deployment.