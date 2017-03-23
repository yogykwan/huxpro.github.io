---
layout:     post
title:      "Intro to Python"
subtitle:   ""
date:       2017-02-25
author:     "Jennica"
header-img: "img/post-bg-geek.jpg"
catalog: true
tags:
    - 技术
    - Web
    - Python
---

# Source

- [Programming Foundations with Python](https://cn.udacity.com/course/programming-foundations-with-python--ud036)

# Project

- [movie-trailer-website](https://github.com/yogykwan/movie-trailer-website) : a static web page allowing visitors to browse movies and watch trailers.

# Function

- create python file `some_module.py`
- make function inside this file, define function via `def do_this(params): do something`
- use function anywhere, firstly import module via import `some_module`, then call function via `some_module.do_this(some_params)`

# Class

- make class inside python module file, define function via `Class some_class(parent_class):`
- make constructor of the class inside it via `def __init__(self, class_params): construct some_class`
- make function member of the class inside it via `def do_this(self, params): initialize data members and do something`
- use class anywhere firstly import module via `import some_module`, create instance of the class via `some_instance=some_module.some_class(some_params)`
- call members of the class by its instance via `some_instance.do_this(some_params)` or `some_instance.data_member`

# Structure

- built-in functions like `open()` or `max()`
- built-in modules like `urllib` or `os`
- third-party modules like `twilio`or `numpy`
- self-built modules like `fresh-tomatoes`
- function and data members in modules like `show_something()` or `some_data`

