---
layout: post
title:  "Docker安装couchdb(使用docker pull方法)"
date:   2021-10-08 17:11:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

用过一段时间的`CouchDB`，当时的需求是离线时数据也能用，在线时能同步。顺着这个思路找到了`CouchDB`。用了有半年左右，就又不用了。还是换成传统的`HTTP接口+ＭySQL`方式。但是之前记录的安装过程，这里记录一下，方便Ｎ年后再次使用。

# 普通安装

Docker安装


# 新建目录

```
mkdir mycouchdb && cd mycouchdb
```


# 搜索

```
docker search couchdb
```


# 安装
```
docker pull apache/couchdb:3
```

# 运行
```
docker run --name couchdb-cok -p 5986:5984 -d -v /opt/couchdb/data/couchdb-cok:/opt/couchdb/data -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=kichina20202044 apache/couchdb:3
```

# 测试
```
http://localhost:5985/_utils
```

# 恢复数据
```

```

第一次init慢的原因
https://github.com/apache/couchdb-docker/pull/132
```

```
