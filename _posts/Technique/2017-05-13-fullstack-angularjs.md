---
layout:     post
title:      "Front-End Javascript Framework: AngularJS"
subtitle:   ""
date:       2017-05-13
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

# AngularJS Overview

![Angular Overview](/img/in-post/post-fullstack-angular.jpg)

## Javascript Frameworks
1. library: a collection of functions,  your code is in charge and it calls into the library when it sees fit
2. framework: a particular implementation of a web application where your code fills in the details, the framework is in charge and it calls into your code when it needs something app specific
3. javascript framework: single page application, MVC, test driven; scalable, reusable maintainable js code

## Introduction to AngularJS
1. AngularJS: solve impedance mismatch, design CRUD, declarative
2. terms: two-way binding, scope, directive, template, routing, testing, module, controller, filter, factory, service, provider
3. directives: ng-\* / data-ng-\*, e.g., ng-app, ng-init, ng-bind, ng-model, ng-repeat
4. ng-app: apply to \<html> with app's name, means entire page is under control of this Angular app
5. ng-init: evaluate an expression, initialize a javascript variable
6. ng-model: two-way binding, bind input value to a js variable within the scope
7. ng-repeat: loop over items in a collection, instantiate a template for each item

## MVC Framework
1. design pattern: well-document solution to a recurring problem
2. MVC: isolation of domain logic from user interface, permit independent development, testing and maintenance; separate concerns to models, views and controllers
3. model: manage behavior and data, response info about state to request (usually view), change state from instruction of commander (usually controller), notify observer (usually view) the change of info in event-driven system
4. view: render model into user interface for interaction, a viewport typically has a 1 to 1 corresponding display surface
5. controller: receive user input and initiate response by calling model, instruct model and viewport to perform actions based on user input
6. MVVM: descendent of MVC, ViewModel is abstraction of view that exposes public properties and commands

## Angular Modules and Controllers
1. angular module: collection of controller, directive, filter, service, other configuration info; `<html ngApp=“someApp”><body><script>var app=angular.module(’someApp’, []);</script></body></html>`
2. angular controller: js object containing attributes and functions exposed to expressions and directives, `<div ng-controller=“someController"></div><script>app.controller(‘someController', function() {});</script>`
3. angular filter: format value without modifying underlying data; used in view templates, controllers, services
4. built-in filters: uppercase/lowercase, currency, date, orderBy, json, limitTo, filter (based on criteria specifies and return a new array)

# Task Runners, Angular Scope and Form

## Task Runners: Grunt and Gulp
1. css tasks: compile sass or less into css, autoprefixer to add vendor prefix, minification to remove unnecessary characters, concatenation
2. js taskes: JSHint to check code errors and potential problems, contenation, uglification (minification+mangling), recheck errors
3. other tasks: reduce image size, watch changes and automatically rerun tasks, livereload, testing
4. task runner: configure tasks once and rerun automatically as needed; grunt configure over code, gulp code over congifure
5. gulp: using node.js streams to build pipelines, gulp.src()->pipe()->gulp.dest(), [gulpfile example](https://github.com/yogykwan/conFusion/blob/master/conFusion-Angular/gulpfile.js)

## Angular Scope
1. scope: object refers to app model, core of two-way data binding; controller set properties on scope for view to sync
2. nested scope: $rootScope: topmost scope created when app starts, new scope create when encountering some directives as a child of a parent scope, scope tress looks like DOM tree

## Angular Forms and Form Validation
1. Angular form: define js object on $scope `$scope.name={first:"",last:""};`, use ng-model on form field `<input class=“form-control” ng-model=“name.first”>`
2. binding select: define js list `var channels = [{value:"tel", label:"Tel."},{value:”email",label:"Email"}];`, bind with ng-option `<select class="form-control” ng-model=“mychannel” ng-options="channel.value as channel.label for channel in channels"><option value="">Tel. or Email?</option></select>`
3. form validation: use `novalidate` to turn off HTML5 form validation, let angular in charge of validation, give form a name, ng-submit specifies the function to call; angular validates form before copying value to $scope
4. filed properties: `formname.fieldname.[$pristine, $dirty, $valid, $invalid]`; bootstrap provides css classes to enable validation state and message like has-error, has-warning, has-success, help-block

# Single Page Applications

## Dependency Injection
1. dependency injection: implement inversion of control, pass a dependency to a dependent object that it can use it
2. angular components like services, directives, filters and animations can be injected into controllers, config and run methods
3. annotation: `module.controller('MenuController', ['$scope', 'menuFactory', function($scope, menuFactory){}]);`

## Angular Factory and Service
1. factory: substitute objects via DI, lazily instantiated, singleton
2. built-in services: $http , $scope, $rootScope, $location, $parse, $templateCache, $animate, $injector
3. services declare functions: service(), factory(), provider(), constant(), value()
4. angular factory: `.factory(’someFactory', function(){var fact; fact.fun=function(){}; return fact;});`
5. angular service: `.service(’someFactory', function(){this.fun=function(){};});`

## Angular Templates
1. angular template: written in HTML, contain angular specific elements and attributes (directive, markup, filter, form control), dynamic view = template + controller + model
2. ng-include directive: `<ng-include src=“’menu.html’”></ng-include>`

## Single Page Applications
1. SPA: redraw parts of page without requiring the entire page
2. challenges: search engine, partitioning responsibility between client and server, accelerate initial page load

## Angular ngRoute and SPAs
1. server serves up data using REST API, view is completely rendered on client-side with templating and routing
2. deep linking: specify a link to a searchable or indexed piece of web content, `http://localhost/#!/menu/0`
3. $location service: expose current URL, synchronize URL with browser; manipulate URL, path, search part, hash part
4. ngRoute module: manage the interaction between the $location service and the rendered view, `angular.module(‘someApp', ['ngRoute'])`
5. config $routeProvider: `.config(function($routeProvider) {$routeProvider.when(‘/about', {templateUrl : ‘about.html’, controller : ‘aboutController' }).otherwise(‘/');;});`
6. $routeParams: `.controller('DishDetailController', ['$scope', '$routeParams','menuFactory', function($scope, $routeParams, menuFactory) { var dish= menuFactory.getDish(parseInt($routeParams.id,10));$scope.dish = dish; }]);`
7. ng-view directive: work with $route service to include rendered template of current route into main layout, `<ng-view></ng-view>`

## Angular UI-Router and SPAs
1. Angular UI Router: view based on state of app, multiple and nested views, `angular.module(‘someApp', ['ui.router'])`
2. router as a state machine: `.config(function($stateProvider, $urlRouterProvider) { $stateProvider.state('app.about', {url:'about',views:{'content@':{template:’about.html',controller :'AboutController' } }});$urlRouterProvider.otherwise('/'); });`
3. ui-view directive: `<div ui-view="header"></div><div ui-view="content"></div>`
4. ui-sref: generate href of next state when clicked, `<a ui-sref=“app”></a><a ui-sref=“app.about”></a>`
5. $stateParams: `.controller('DishDetailController', ['$scope', '$stateParams','menuFactory', function($scope, $stateParams, menuFactory) { var dish= menuFactory.getDish(parseInt($stateParams.id,10)); $scope.dish = dish;}]);`

# Client-Server Communication and Angular Testing

## Networking Essentials
1. http: Hypertext Transfer Protocol; verbs are head, get, post ,put, delete ,trace, options, connect
2. http response codes: 200 ok, 301 moved, 304 not modified, 400 bad request, 401 unauthorized, 403 forbidden, 404 not found, 500 internal error
3. json: Javascript Object Notation, key-value pairs

## Angular $http
1. $http service: communicate with servers using http protocol via browsers XMLlHttpRequest or JSONP
2. promise: run functions asynchronously, call handler/callback (success/error) based on states (pending/fulfilled/rejected)
3. $http return promise: `$http({method: ‘GET’, url: ‘/dishes’})•.then( function() {success}, function() {error);`; shortcuts: $http.get(), $http.put(), $http.post(), $http.delete(), $http.jsonp(), $http.head(), etc.
4. http response components: data, status, headers, config, statusText
5.  ng-if directive: add or remove portion of DOM tree based on express

## REST
1. REST concepts: unconstrained resources, constrained verbs, constrained representations
2. resources: map to entities, represented with URI in http
3. verbs: actions performed on resources, corresponding to CRUD operations
4. representations: data represented or returned format, json and xml are two main formats
5. stateless server: server side shouldn’t track client state, client track its own state using cookies or local storage

## Angular $resource
1. $resource module: rovides a higher level abstraction than $http for interacting with a RESTful API server, `angular.module(’someApp’, [’ngResource'])`
2. $resource service: `$resource(url, [paramDefaults], [actions], options);`, e.g., `$resource(baseURL+"dishes/:id",null, {'update':{method:'PUT' }}).update({id:$scope.dish.id},$scope.dish).$promise.then(function(response){},function(response){});`
3. default actions: `{ 'get': {method:'GET'},'save': {method:'POST'},'query': {method:'GET', isArray:true}, 'remove': {method:'DELETE'}, 'delete': {method:'DELETE'} };`

## Angular Testing
1. unit testing: test individual unit of code restricted to verifying the correctness of logic, use dependency injection to test isolated unit, separate DOM and logic through the use of $scope
2. Jasmine: behavior driven development framework for JavaScript, `describe('Controller: MenuController', function () {it('should show menu', function(){ expect(scope.showMenu).toBeTruthy(); }); });`
3. Karma: js based command line tool, execute tests in browser
4. ngMock module: inject and mock angular services within unit tests, `beforeEach(module(‘confusionApp'));var MenuController, scope, $httpBackend; beforeEach(inject(function ($controller, _$httpBackend_, $rootScope, menuFactory) {$httpBackend = _$httpBackend_; $httpBackend.expectGET("http://localhost:3000/dishes").respond([]);scope = $rootScope.$new(); MenuController = $controller('MenuController', { $scope: scope, menuFactory: menuFactory });$httpBackend.flush(); }));`
5. testing strategies: unit (individual units, repeated), integration (interactions of modules), end-to-end (slowly test everything including user interaction)
6. protractor: node program enables E2E test, use WebDriver to control browsers to carry out test, use Jasmine for expressing the test syntax, [protractor config example](https://github.com/yogykwan/conFusion/blob/master/conFusion-Angular/test/protractor.conf.js) and [test example](https://github.com/yogykwan/conFusion/blob/master/conFusion-Angular/test/e2e/scenarios.js)
