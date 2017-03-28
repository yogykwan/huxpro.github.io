---
layout:     post
title:      "Intro to Full Stack"
subtitle:   ""
date:       2017-03-28
author:     "Jennica"
header-img: "img/post-bg-geek.jpg"
catalog: true
tags:
    - 技术
    - Web
    - 后台
---


# Source
- [Full Stack Foundations](https://cn.udacity.com/course/full-stack-foundations--ud088)

# Project
- [item-catalog](https://github.com/yogykwan/item-catalog) - an application made up of categorized items and user system, where users can manage their own categories and items.

# SqlAlchemy

## Setup Database
```
Base = sqlalchemy.ext.declarative_base()
class ClassA(Base):
    __tablename__ = TABLENAME
    id = Column(sqlalchemy.Integer, sqlalchemy.orm.relationship(ClassB), primary_key=True, nullable=False)
engine = create_engine('sqlite:///some.db')
Base.metadata.create_all(engine)
```

## Bind & Session
```
engine = create_engine('sqlite:///restaurantMenu.db')
Base.metadata.bind = engine
DBSession = sessionmaker(bind = engine)
session = DBSession()
```

## CRUD
```
session.add(Class())
instance=session.query(Class).filter_by().one()
session.update(instance)
session.delete(instance)
```

# Python Web Server

## Handler
```
class webServerHandler(BaseHttpServer.BaseHTTPRequestHandler):
  def do_GET():
    if self.path.endswith(‘/'):
      self.send_response(200)
      self.send_header(‘Content-type’, ’text/html’)
      self.end_headers()
      self.wfile.write(HTML)
  def do_POST():
    if self.path.endswith("/edit"):
      ctype, pdict = cgi.parse_header(self.headers.getheader('content-type'))
      if ctype == 'multipart/form-data':
        fields = cgi.parse_multipart(self.rfile, pdict)
        value = fields.get(’name')
```

## Server
```
server = BaseHttpServer.HttpServer((‘’, 8080), webServerHandler)
server.serve_forever()
server.socket.close()
```

# Flask Framework

## Flask App
```
from flask import Flask, render_template, request, redirect, url_for, jsonify
app = Flask(__name__)
if __name__ == ‘__main__’:
  app.secret_key = ’SECRET KEY’ # session key for flashing
  app.debug = True
  app.run(host = ‘0.0.0.0’, port = 8080)
```

## Route
```
@app.route(‘path/<int:id>/path/‘, methods=[‘GET’, ‘POST'])
def MainPage(id):
  if request.method == ‘POST’: return redirect(url_for(function, params))
  return render_template(template, params)
```

## Flashing
- handler - `flask.flash(“Flash Message.”)`
- template - `with messages = get_flashed_messages()`


## Json
- declarative_base - `@property def serialize(self): return {’name’:’value',}`
- handler - `return jsonify(Items=[i.serialize for i in items])` 


# Iterative Development
- Mock-ups - sketch, page flow, service, url
- Routing - url, method, message
- Templates & Forms - html, fake test data
- CRUD Functionality - CRUD, redirect(url_for(FUNCTION))
- API Endpoints - json, jsonify(instance.serialize)
- Styles & Flashing - static(css, js, image), flash message
