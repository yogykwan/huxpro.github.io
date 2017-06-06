---
layout:     post
title:      "Front-End Web UI Framework: Bootstrap"
subtitle:   ""
date:       2017-05-05
author:     "Jennica"
header-img: "img/post-bg-fullstack.jpg"
catalog: true
tags:
    - 技术
    - Web
    - 前端
---

# Related

- [Project - conFusion](https://github.com/yogykwan/conFusion)
- [Course - Full Stack](https://www.coursera.org/specializations/full-stack)

# Bootstrap Overview

## Front-End Web UI Framework
1. collection of ready-to-use HTML, CSS and JavaScript templates for UI components:– Typography, Forms, BuPons, Tables, Naviga8ons, Dropdowns, Alerts, Modals, Tabs, Accordion, Carousel etc.
2. responsible web design, cross-browser compatibility, increased productivity, community support
3. Bootstrap is the most popular HTML, CSS, and JS framework for developing responsive, mobile first projects on the web

## Using Bootstrap
1. file structure: css, js, fonts. Include css in <head>, include js at the bottom of <body>
2. container class: fixed width, outermost div to wrap all the site content, container-fluid allows full width container
3. row class: divide page into multiple rows, horizontal grouping for columns, must be inside container
4. jumbotron class: component for showcasing key content like company name, can be used outside a container to span the entire screen width

## Responsive Design
1. for devices with different screen sized, adapt to user’s viewport, mobile first design
2. built-in features like grid system, fluid images, media queries
3. media query based on size of viewport: `@media screen and (min-width: 600px) {…}`

## Grid System
1. viewport meta tag: ensure screen width as same as device width, `<meta name="viewport" content="width=device-width, iniBal-scale=1”>`
2. each row divided into 12 columns, column classes (col-xs-\*, col-sm-\*, col-md-\*, col-lg-\*) for defining layouts for various screen sizes
3. column layout classes : col-sm-push-\*, col-sm-pull-\*, column-sm-offset-\*
4. nesting column: row can be nested in column div

## Navigation
1. navigation bar: use simple terms, standardize navigation, indicate current location, use standard web conventions like click logo for home page
2. breadcrumb: secondary navigation below primary one like bar and above content, indicate current page location within hierarchy
3. other navigations: tab, pill, pagination, dropdown, accordion, tags, scrollspy, affix

## Navbar
1. navbar classes: navigation header with responsive behavior, can start collapsed on xs screens and include toggle button to show/collapse items
2. outmost navbar class: `<nav class=“navbar” role=“navigation”>`, positioning with navbar-fixed-top, navbar-fixed-bottom, navbar-static-top, navbar-inverse
3. nav include include navbar-header and navbar-nav; bar-header include navbar-brand, navbar-nav used with navbar-right
4. navbar-toggle button: inside navbar-header, target to navbar-collapsed div, inside navbar-collpased are navbar-nav
5. dropdown class: `<a href="#" class="dropdown-toggle" data-toggle=“dropdown" role="button">Menu</a><ul class=“dropdown-menu”></ul>`

## Icon Fonts
1. bootstrap glyphicon: `<span class="glyphicon glyphicon-home”></span>`
2. font awesome: `<i class="fa fa-phone"></i>`
3. bootstrap-social: use glyphicon and font awesome icons to create buttons for social media links, `<a class="btn btn-social-icon btn-facebook" href="http:// www.facebook.com/profile.php?id="><i class="fa fa-facebook"></i></a>`

# Bootstrap CSS Components

## User Input
1. input tags: \<a>, \<button>, \<form>
2. button: simple interaction of click, specific role inside form and general purpose outside
3. form elements: \<textarea>, \<button>, \<select>, \<input type=“[text, password, submit, radio, checkbox, button, color, date, datetime, email, month, number, range, search, tel, Eme, url, week]”>

## Bootstrap Buttons
1. color classes: btn-[default, primary, success, info, warning, danger, link]
2. size classes: btn-[lg, sm, xs] indicate size, btn-block span full width of parent
3. button classes can be applied to \<a>, \<button> and \<input>, but only \<button> can be used in nav and navbar
4. btn-toolbar contain group classes: btn-group, btn-group-vertical, btn-group-justified, btn-group-[lg, sm, xs] 

## Bootstrap Forms
1. form classes: hoirzontal-form, inline-form
2. form-group class: composed of label and corresponding input div
3. input-group-addon class: add extra info to ends of input area

## Bootstrap Tables
1. table classes: table-striped, table-bordered, table-hover, table-condensed,, table-responsive
2. apply contextual color classes to <tr> or <td>: active, success, info, warning, danger

## Bootstrap Panels and Wells
1. panels and wells are used to highlight content on website
2. panel: outmost is panel class, inside are panel-heading, panel-body and panel-footer
3. well: `<div class=“well”><blockquote><p>ABC</p><footer><cite>by XX</cite></footer></blockquote></div>`

## Images and Media
1. image classes: img-responsive for responsive images, img-rounded, img-circle, img-thumbnail indicate shape
2. thumbnail class: `<div class=“thumbnail”><img src=“”, class=“”><div class=“caption”>ABC</div></div>`
3. media: outmost class is media; inside media-position class is media-object img, followed by media-body class; inside media-body is media-heading and context
4. media list: media-list applied to \<ul>, media classes applied to \<li>
5. responsive embed: apply embed-reponsive and embed-responsive-4by3 or embed-responsive-16by9 to \<div>, inside apply embed-responsive-item to \<embed>, \<iframe>, \<video>, \<object>

## Alerting Users
1. label class: label + label-\<color>
2. badge class: self-collpasing when empty
3. alert class: `<div class="alert alert-warning alert-dismissible" role="alert"><button type="button" class=“close" data-dismiss="alert"><span>&times;</span></button>ABC</div>`
4. progress bar: `<div class="progress"><div class="progress-bar progress-bar-danger progress-bar-striped"role="progressbar" style="width: 80%">80%</div></div>`

# Bootstrap Javascript Components

## Bootstrap Javascript
1. Bootstrap javascript components based on Jquery (javascript library)
2. include both bootstrap and jquery js files at bottom of body 
3. js components ca be used via js plugins and data-* attributes, without a single line of js

## Tabs, Pills and Tabbed Navigation
1. navigation elements for navigating content within a page that is organized into multiple panes
2. tabs and pills: `<ul class=“nav nav-tabs/nav-pills” role=“tablist”><li role=“presentation” class=“active"><a href="#peter” role="tab" data-toggle="tab">Peter</a></i></ul>`
3. content and panels: `<div class="tab-content"><div role="tabpanel" class="tab-pane fade in active" id="peter”>Peter</div></div>`

## Collapse
1. collapse: `<div class=“collapse in” id=“example”>...</div><div><a class=“btn” role=“button” data-toggle=“collapse” href=“#example"></a></div>`
2. accordion: `<div class="panel-group" id="accordion” role="tablist”><div class=“panel”><div class=“panel-heading”><a role=“button” data-toggle=“collapse” data-parent=“#accordion” href=“#peter"></a></div><div role=“tabpanel” class=“panel-collapse collapse in” id=“peter"></div></div>`

## Scrollspy and Affix
1. scrollspy: add data-\* attributes to body `<body data-spy="scroll" data-target="#myScrollspy" data-offset="200”>`; add nav element to page `<nav class="hidden-xs col-sm-2" id="myScrollspy"><ul class="nav nav-pills nav-stacked" data-offset-top="400"><li><a href="#history">Our History</a></li></ul></nav>`
2. affix: `<ul class="nav nav-pills nav-stacked" data-spy="affix" data-offset-top="400”>`

## Tooltips, Popovers and Modals
1. reveal content upon interacting with element on page and display as an overlay, flexibility increase from tooltip to popover to modal
2. tooltip: pop up when hover, 3 attributes `data-toggle=“tooltip” data-placement=“top|botoom|left|right” title=“message”`, js code included `$(document).ready(function() {$('[data-toggle="tooltip"]').tooltip();});`
3. popover: pop up when click, 4 attributes `data-toggle=“popover” data-placement=“top|botoom|left|right” title=“title” data-content=“message"`, js code include `$(document).ready(function() {$('[data-toggle=”popover"]').popover();});`
4. modal: modal contains modal-dialog and modal-content, modal-content includes header, body and footer; trigger a modal `<a data-toggle=“modal” data-target=“#modal"></a>`

## Carousel
1. carousel: `<div id="mycarousel" class="carousel slide" data-ride="carousel"></div>`
2. slides: `<div class="carousel-inner" role="listbox"><div class="item active"><img class="img-responsive” src=”..."> <div class="carousel-caption”>...</div></div></div>`
3. indicator controls: `<ol class="carousel-indicators"><li data-target="#mycarousel"data-slide-to="0" class="active"></li></ol>`
4. left/right controls: `<a class="left carousel-control" href="#mycarousel" role="button" data-slide="prev"><span class="glyphicon glyphicon-chevron-left"></span></a>`

# Web Tools

## JQuery
1. JQuery features: HTML/DOM manipulation, CSS manipulation, HTML Event methods, Effects and animations, AJAX
2. syntax: `$(selector).action()`, e.g., `$(“p”).hide(); $(“#mycarousel”).carousel(‘pause’);`
3. selector: tag, #id, .class, $(this), [attribute] like [data-toggle=“tooltip”]
4. event: user’s interaction cause DOM events via mouse, keyboard, form, document; event methods include ready(), click(), dblclick(), mousedown(), on(), etc.

## Node.js and NPM
1. node.js: javascript runtime built on chrome v8 javascript engine, use event-driven, non-blocking I/O model
2. NPM (node package manager):manage node modules/packages, contain js files and package.json

## CSS Preprocessors: Less and Sass
1. css preprocessor: all are compiled into css automatically, less and sass are popular
2. features: variable, nesting selector, mixin, function, expression, import
3. less nesting: `@indigo: #1a237e; .carousel{background:@indigo; .item{…}}`
4. less mixin: `.zero-margin (@pad-up: 0, @pad-left: 0) {} .row-header{.zero-margin(50px. 0)}`

## Web Tools
1. Bower: manage dependencies and fetch components like framework, libraries, assets, utilities etc.
2. Yeoman wokflow: Yo scaffold webapp -> Bower install dependecies -> Grunt/Gulp task automation


