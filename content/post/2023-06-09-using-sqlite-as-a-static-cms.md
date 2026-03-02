---
title: Using SQLite as a Static CMS
date: 2023-06-09
postindex: 61
url: /post/61/using-sqlite-as-a-static-cms
---

SQLite is a database the operates out of a single file. The engine is embedded and does not require a separate process for management.

The application requires a Content Management System (CMS). I am using SQLite to store all of the data for that CMS. However, the application is constructed to only read from the database. The CMS is static.

My goal is to populate the database with the needed content during the build phase. Then publish the database file along with the application in a container image. The application and CMS versions would be in sync.

The CMS will be populated with a custom command line program. It uses YAML files to define the content. I chose this over creating another application for administration purposes. Normal database applications do not have a defined state. The contents of the database define the application state. The contents of the database are a point in time. I wanted a more definitive database state.

Running the CLI with a data file produces a very specific database state. It is not founded on activity performed on the data. You do not need to backup the data in order to test. The state of the database is very deterministic. The same data file will give you the same database every single time.

The CLI processes the YAML file. I did not want to run SQL files into the database. There would be a similar end state but I would need to think in terms of SQL and tables. With a custom CLI command I can think in terms of content.
