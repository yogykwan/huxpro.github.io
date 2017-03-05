---
layout:     post
title:      "Intro to Backend"
subtitle:   ""
date:       2017-03-05
author:     "Jennica"
header-img: "img/post-bg-geek.jpg"
catalog: true
tags:
    - 技术
    - Web
    - 后台
---

# Source
- [Intro to Backend](https://cn.udacity.com/course/intro-to-backend--ud171)

# Project
- [multi-user-blog](https://github.com/yogykwan/multi-user-blog) - a multi user blog website allowing users to post, edit, delete, like posts after signup and login.

# Form and Input

## Google App Engine

- [install google app engine](https://drive.google.com/open?id=0Byu3UemwRffDc21qd3duLW9LMm8)
- create app in [Developer Console](https://console.developers.google.com/)
- run locally `dev_appserver.py .`
- browse locally via [http://localhost:8080](http://localhost:8080)
- deploy app `gcloud app deploy`
- browse app `gcloud app browse`

## Input Form

- form action - jump url
- form method - get(append ur, length limit, can cache), post(append body, no cache, update server)
- input type - submit, password(*), checkbox, radio, select option and textarea(value could inside option tag)
- input label - outside every input, start with label content

# Template

## Jinja

- set jinja template env - `jinja_env = jinja2.Environment(loader=jinja2.FileSytemLoader(template_dirname))`
- get template - `template = jinja_env.get_template(template_name)`
- render html - `template.render(params)`

## Escape

- set env - `autoescape=True`
- ignore escape in template - `{\{ some_item | safe}\}`  (\\{ means {)

## Template

- statement syntax - `{\% statement \%} {{some_item}} {\% endstatement \%}`
- inheritance - `{\% extends “base.html" \%} {\% block content \%} … {\% endblock \%}` (\% means %)

# Database

## ACID

- atomicity - steps in one transaction all fail or all succeed
- consistency - key constraint
- isolation - no parallel, only serial
- durability - what done remains there

## Google Datastore Entity

- create table - `class SomeTable(db.model): some_col = db.StringProperty()`
- create instance - `m = SomeTable()`
- insert into db- `m.put()`
- query from db - `db.GqlQuery(some_sql)`

# Account Security

## Cookie Hashing

- hash cookie - `h = hmax.new(SECRET, id).hexdigest()`
- set cookie - `Set-Cookie: user_id=id|h`
- get cookie - `Cookie: user_id=_id|_h`
- check cookie - `_h == hmax.new(SECRET, _id).hexdigest()`

## Password Hashing

- hash password (bcrypt is best) - `h = hashlib.sha256(name+password+some_salt)`
- store into database - `password=h|some_salt` 
- transmit login info (HTTPS=HTTP+SSL) - `_name, _password`
- check password - `h == hashlib.sha256(_name+_password+some_salt)`
