---
layout: default
title: "mysqldump"
parent: linux
nav_order: 1
published: true
---
# mysqldump
{: .no_toc  }

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
mysqldump --single-transaction --add-drop-table -u <id> -p <DB> <table> > <table>.sql
mysqldump --single-transaction --add-drop-table -u <id> -p <DB> <table> | gzip > <table>.sql.gz
```
## Reference
```
```
---