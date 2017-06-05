---
layout:     post
title:      "Intro to Javascript"
subtitle:   ""
date:       2017-04-28
author:     "Jennica"
header-img: "img/post-bg-geek.jpg"
catalog: true
tags:
    - 技术
    - Web
    - 前端
---


# Source
- [Javascript Design Patterns](https://cn.udacity.com/course/javascript-design-patterns--ud989)

# Project
- [neighborhood-map](https://github.com/yogykwan/neighborhood-map)

# MVO
- Model: store data, including both data from the server and user
- View: stuff user sees and interacts with, including DOM elements, input elements, buttons, images; giving application data and for reading data
- Octopus(Controller, ViewModel, Presenter, *): separate model and view, allow change one piece without upsetting the other

# Knockout JS

## Concepts
- ViewModel - similar to Octopus
- Declarative bindings - connect View and ViewModel
- Automatic UI refresh - update view whenever Model change, two-way binding
- Dependency tracking - some Model depend on other Model

## Terms
- observable - auto refresh, `ko.observable()`
- observable array - repeated observable, can call array methods like push() or pop() directly
- computed observable - return function based on observables, `ko.computed(function(){return o;}, this)`
- binding - tie observable* in View with Model via ViewModel, `data-bind=“”`, `ko.applyBindings(new ViewModel());`
- scope - `var self = this;`, `with: `, `$parent.`

# Learn New Codebase
- run application
- explore file structure
- look at what js files are loaded
- figure out what libraries do
- modify application
- add new feature