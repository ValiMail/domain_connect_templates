# domain_connect_templates

Valimail templates for use in the Domain Connect Protocol

## Domain Connect Protocol

[Domain Connect](https://www.domainconnect.org/) is an open-source project
to allow easy and risk-free configuration of DNS between Service Providers (Valimail, Fraudmarc, Shopify, [more](https://www.domainconnect.org/service-providers/))
and DNS Providers (GoDaddy, Google Domains, [more](https://www.domainconnect.org/dns-providers/)).

References:

- https://github.com/Domain-Connect/spec
- https://github.com/Domain-Connect/Templates/

## Valimail DNS changes

For a given customer, Valimail prompts the customer to make DNS changes to support
our automated solutions for DMARC and anti-phishing.

For example, if our customer owned `example.com`, after making the requested changes the customer's DNS records would return:

```
> dig NS _dmarc.example.com +short
ns.vali.email.

> dig NS _domainkey.example.com +short
ns.vali.email.

> dig NS _bimi.example.com +short
ns.vali.email.

> dig TXT example.com +short
# Assuming that we pass in the following as the %spftxt% variable
...
"v=spf1 include:example.com._nspf.vali.email include:%{i}._ip.%{h}._ehlo.%{d}._spf.vali.email ~all"
...
```
