---
layout: default
title: "https-setting"
parent: nginx
nav_order: 1
published: true
---

# https-setting
{: .no_toc  }

## Table Of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## Install certbot

```
$ sudo dnf install -y epel-release
$ sudo dnf install certbot python3-certbot-nginx

```

## Install SSL/TLS certificate
```
$ sudo certbot --nginx

Saving debug log to /var/log/letsencrypt/letsencrypt.log
Enter email address (used for urgent renewal and security notices)
 (Enter 'c' to cancel): nerostar88@gmail.com

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.2-November-15-2017.pdf. You must
agree in order to register with the ACME server. Do you agree?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: Y

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing, once your first certificate is successfully issued, to
share your email address with the Electronic Frontier Foundation, a founding
partner of the Let's Encrypt project and the non-profit organization that
develops Certbot? We'd like to send you email about our work encrypting the web,
EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: Y
Account registered.

Which names would you like to activate HTTPS for?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: pentabong.com
2: www.pentabong.com
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel):
Requesting a certificate for pentabong.com and www.pentabong.com

Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/pentabong.com/fullchain.pem
Key is saved at:         /etc/letsencrypt/live/pentabong.com/privkey.pem
This certificate expires on 2022-09-24.
These files will be updated when the certificate renews.
Certbot has set up a scheduled task to automatically renew this certificate in the background.

Deploying certificate
Successfully deployed certificate for pentabong.com to /etc/nginx/nginx.conf
Successfully deployed certificate for www.pentabong.com to /etc/nginx/nginx.conf
Congratulations! You have successfully enabled HTTPS on https://pentabong.com and https://www.pentabong.com

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
If you like Certbot, please consider supporting our work by:
 * Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
 * Donating to EFF:                    https://eff.org/donate-le
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

## Settng nginx.conf
```
server {
    listen [::]:443 ssl ipv6only=on; # managed by Certbot
    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/pentabong.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/pentabong.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
}

```

## Managing the SSL certificate renewal
```
$ sudo certbot renew
$ crontab -e
0 0 * * * /usr/bin/certbot renew > /dev/null 2>&1
```

## Reference
```
https://www.linuxtechi.com/install-lets-encrypt-ssl-nginx-rocky-linux/
```
---