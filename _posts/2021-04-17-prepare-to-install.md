---
title: "Prepare To Install"
date: 2021-04-17
---

We will store all source codes in separated files (one file for one database object). But to check our work we need to write a simple script to merge all files in one SQL.
```bash
cd db
cat \
	schema.sql \
	public/page.sql \
	content/article.sql \
	shop/product.sql \
	data.sql \
	> ../install.sql
cd ..
psql -U postgres -c "drop database if exists cms"
psql -U postgres -c "create database cms"
psql -U postgres -d "cms" < install.sql
rm install.sql
```

Of course it is SO simple and in future we will make it more complicated and useful, but now it is ok!
