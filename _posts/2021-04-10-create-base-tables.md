---
title: "Create Base Tables"
date: 2021-04-10
---

First we create base table that should contain fields common to all pages of the site. We put it in `public` schema.
```sql
CREATE TABLE public.page
(
    page_id bigserial PRIMARY KEY,
    alias text
);
```
All tables that represent data for any page in all site components should inherit this base page. We create two example component:
* `content` - to display content of the site
* `shop` - a draft for e-commerce solution

```sql
CREATE SCHEMA content;
CREATE SCHEMA shop;
```
In `content` schema we create simple `article` table^
```sql
CREATE TABLE content.article
(
    content text,
    CONSTRAINT article_pkey PRIMARY KEY (page_id)
)
INHERITS (public.page)
```

In `shop` we create simple table for products:
```sql
CREATE TABLE shop.product
(
    name text,
    price numeric,
    CONSTRAINT product_pkey PRIMARY KEY (page_id)
)
INHERITS (public.page)
```

And fill it with sample data:
```sql
INSERT INTO content.article (page_id, alias, content) VALUES (1, 'contacts', '250  Stratford Drive, Waipahu, 96797, 808-268-2423');

INSERT INTO shop.product (page_id, alias, name, price) VALUES (2, 'xiaomi-redmi-note-8t', 'Xiaomi Redmi Note 8T', 13999);
INSERT INTO shop.product (page_id, alias, name, price) VALUES (3, 'xiaomi-redmi-note-9-pro', 'Xiaomi Redmi Note 9 Pro', 20999);

SELECT pg_catalog.setval('public.page_page_id_seq', 3, true);
```
