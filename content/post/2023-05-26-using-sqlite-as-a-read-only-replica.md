---
title: Using SQLite as a Read-Only Replica
date: 2023-05-26
postindex: 47
url: /post/47/using-sqlite-as-a-read-only-replica
---

I am looking into using [SQLite](https://sqlite.org/index.html) as a read-only database.

Why?

The application requires a database but only to read content metadata. Because this is an MVP it does not require the ability to write to the database. My idea is to pre-build the database and have the application use it like it was read replica.

Using a read-only database sounded appealing to me because I am cheap. Standing up [MySQL](https://www.mysql.com/) or [PostgreSQL](https://www.postgresql.org/) sounded a bit excessive to me. Why pay for, or pay for access to, only half of the intended functionality of the product. [SQLite](https://sqlite.org/index.html) is just a file. Files live perfectly happy in a container. My application is a web app. It lives in a container. Win-Win!

I entertained the idea of creating a management application that would allow me interact with the database. In it's current form the product only needs to read information at runtime. The setup and maintenance of the database would be handled elsewhere.

Part of the product's build process will be to create a new [SQLite](https://sqlite.org/index.html) database file. The data could be versioned alongside the application. The application gets the benefit of using SQL to access content metadata. I get the benefit of using the Entity Framework instead of parsing and reading from JSON files.

Initially I was afraid of incorporating a database because I did not want to support a full database installation: backups, etc. Now I can have access to a database with the additional burden of supporting one.
