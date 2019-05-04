# DNS

*A* record points to IP address.

*CNAME* record points to another domain.

CNAME is preferred over A because hosting providers can scale it up using multiple servers on multiple IDs to serve requests. Most hosting providers do not offer fixed IP in a basic plan and it can be quite expensive.

## Naked domain

Naked domain cannot be pointed to CNAME. Some DNS providers have their DNS servers modified to allow that by faking A record. By setting an ALIAS or ANAME on naked domain, they inspect to what IP address(es) it resolves and serve them back as A record.

The other way is to use *subdomain redirection* to redirect naked domain to www. It is basically 301/302 redirect. The drawback is that it [does not work for HTTPS](https://devcenter.heroku.com/articles/apex-domains#ssl).

Resources:
- [Heroku: The Limitations of DNS A-Records](https://devcenter.heroku.com/articles/apex-domains)
- [freeCodeCamp: Why a domain’s root can’t be a CNAME](https://medium.freecodecamp.org/why-cant-a-domain-s-root-be-a-cname-8cbab38e5f5c)