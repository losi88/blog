---
layout: default
title: "proxy-setting"
parent: nginx
nav_order: 1
published: true
---

# proxy-setting
{: .no_toc  }

## Table Of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## nginx.conf

```
location / {
    return 444;
}
location /moving-out-sale {
    rewrite ^([^/])$ $1 permanent; # Adding trailing slash.
    proxy_redirect off;
    proxy_set_header   X-Forwarded-Host   $host;
    proxy_set_header   X-Forwarded-Server $host;
    proxy_set_header   X-Forwarded-For    $proxy_add_x_forwarded_for;
    proxy_pass         http://127.0.0.1:4000/moving-out-sale; # Redirecting address
}

```

## SELinux
```
$ setsebool httpd_can_network_connect on # Enabling httpd_can_network_connect rule
$ getsebool -a | grep httpd # Checking the change
```
## Reference
```
```
---

