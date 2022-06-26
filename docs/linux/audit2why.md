---
layout: default
title: "audit2why"
parent: Linux
nav_order: 1
published: true
---

# audit2why
{: .no_toc }
---
## Table Of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## Option

```
```

## Example
```
$ audit2why < /var/log/audit/audit.log

type=AVC msg=audit(1656270566.496:10570): avc:  denied  { name_connect } for  pid=43148 comm="nginx" dest=4000 scontext=system_u:system_r:httpd_t:s0 tcontext=system_u:object_r:http_port_t:s0 tclass=tcp_socket permissive=0

        Was caused by:
        One of the following booleans was set incorrectly.
        Description:
        Allow httpd to can network connect

        Allow access by executing:
        # setsebool -P httpd_can_network_connect 1
        Description:
        Allow httpd to graceful shutdown

        Allow access by executing:
        # setsebool -P httpd_graceful_shutdown 1
        Description:
        Allow httpd to can network relay

        Allow access by executing:
        # setsebool -P httpd_can_network_relay 1
        Description:
        Allow nis to enabled

        Allow access by executing:
        # setsebool -P nis_enabled 1
```
## Reference
```
https://www.geeksforgeeks.org/awk-command-unixlinux-examples/
https://stackoverflow.com/questions/44445852/difference-between-single-and-double-quotes-in-awk
```
---