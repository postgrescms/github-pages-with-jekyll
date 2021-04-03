---
title: "Start to Develop New CMS"
date: 2021-04-03
---

There are a lot of CMS in the world such as WordPress, Joomla, Drupal and the like.

They usually use MySQL database, sometimes talk about PostgreSQL database support. But in many cases, the database is just used as a database - tables and columns, and nothing else.

All business logic is implemented in PHP, Ruby or other languages. No database procedures and functions, no built-in database libraries are used. Is it correct? Is it effective? I have heard that some SMS will execute several hundred SQL queries to display one page ...

I got the idea to use all the capabilities of PostgreSQL to make the CMS efficient, simple and secure. Ideally: one page - one SQL query.

So far I don't know what will happen in the end, but I have to try.

Well, let's start.
