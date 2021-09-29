# Home Assistant Add-on: Let's Encrypt with ACME.sh

A Home Assistant add-on that uses ACME.sh to generate Let's Encrypt certificates.

Specify the `dns.provider` from the supported list at https://github.com/acmesh-official/acme.sh/wiki/dnsapi
Add environment variables to the `dns.env` list
Certificates will be installed to `/ssl/`

## Config
```
domains:
  - my.domain.tld
  - '*.my.domain.tld'
certfile: fullchain.pem
keyfile: privkey.pem
dns:
  provider: dns_freedns
  env: 
    - FREEDNS_User=my_username
    - FREEDNS_Password=my_password
```

<a href="https://www.buymeacoffee.com/wernerhp" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>
