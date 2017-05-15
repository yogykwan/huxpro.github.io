---
layout:     post
title:      "Intro to Ajax"
subtitle:   ""
date:       2017-04-18
author:     "Jennica"
header-img: "img/post-bg-geek.jpg"
catalog: true
tags:
    - 技术
    - Web
    - 前端
---


# Source
- [Intro to Ajax](https://cn.udacity.com/course/intro-to-ajax--ud110)

# Project
- [neighborhood-map](https://github.com/yogykwan/neighborhood-map)

# Ajax

## Ajax
- Asynchronous Javascript And XML
- response data: xml, json, html

## Load Page
- request generic html
- request unique html
- render generic html
- render unique html

## Manage HTML Elements

```javascript
var $element = $('#element_id');
$element.append(HTML_CODE);
```

# jQuery

## jQuery.getJSON()

```javascript
$.getJSON(URL, function(data) {...})
.error(function(e) {...});
```

## jQuery.ajax()

```javascript
var timeout = setTimeout(function() {...}, TIMEOUT_PERIOD);
$.ajax({
  url: URL,
  dataType: 'jsonp',
  // jsonp: ‘callback’,
  success: function(data) {
    ...
    clearTimeout(timeout);
  }
});
```