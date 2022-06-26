---
layout: default
title: "watch"
parent: linux
nav_order: 1
published: true
---
# watch
{: .no_toc  }

## Table Of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## Option

```
watch -d -n 2 "cat logs.txt | grep -i '7/6 10:.*test message' | awk '{print \$3}' | awk '{arr[\$1]+=1}END{for(i in arr){print i \"\t\"\":\"arr[i]}}' | sort -t: -k3 -n -r | head -10"
```

## Example
```
megacli -pdrbld -showprog -physdrv\[32:0\] -aALL
```
## Reference
```
```
---