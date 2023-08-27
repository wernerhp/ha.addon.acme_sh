# Home Assistant Add-on: ACME.sh Certs

A Home Assistant add-on that uses ACME.sh to generate certificates.

ACME.sh uses ZeroSSL.com CA by default.  Set `account` to your email address to register a ZeroSSL.com account.
Specify the `dns.provider` from the supported list at https://github.com/acmesh-official/acme.sh/wiki/dnsapi
Add environment variables to the `dns.env` list.  No need to add `export`.  NB: Do not use quotes in environment variables.
The server can be one listed at https://github.com/acmesh-official/acme.sh/wiki/Server (default: `zerossl`)

## Troubleshooting
- Add `DEBUG=1` (or `2` or `3`) to `env` for debug output. 
Certificates will be installed to `/ssl/`

# Support 
If you find this addon useful, please consider supporting my work by [buying me a coffee](https://www.buymeacoffee.com/wernerhp) or making a donation in the form of Bitcoin.

### Bitcoin
`3EGnQKKbF6AijqW9unyBuW8YeEscY5wMSE`  
<img width="200" alt="Bitcoin address: 3EGnQKKbF6AijqW9unyBuW8YeEscY5wMSE" src="https://github.com/wernerhp/ha.addon.acme_sh/assets/2578772/9914c7d4-cd73-4d69-a2f0-2c9b1633dc8f">


### Buy me a coffee
<a href="https://www.buymeacoffee.com/wernerhp" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>

Sign-up for a free Luno wallet using [this invite link](http://www.luno.com/invite/X48WY) or enter the code **X48WY** in the **Rewards** section and we can both earn **R 25.00 free BTC** after investing our first R 500.


## Config
```
account: me@example.com
server: zerossl
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
    - DEBUG=1
```
## Automation 
Setup an automation to run 
```yaml
alias: Restart ACME.sh Addon
trigger:
  - platform: time
    at: "00:00"
action:
  - service: hassio.addon_restart
    data:
      addon: 5b07adba_acme_sh
initial_state: true
mode: single
description: Renew SSL Certificates using ZeroSSL
```
