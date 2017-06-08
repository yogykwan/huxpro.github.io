---
layout:     post
title:      "Hybrid Mobile Development: Ionic"
subtitle:   ""
date:       2017-05-20
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

# Ionic Overview

## Hybrid Mobile App Development
1. app development approaches: native, html5, hybrid
2. hybrid WebView app: HTML, CSS and JavaScript code base runs in an internal browser (called WebView) that is wrapped in a native app. Some native APIs are exposed to JavaScript through this wrapper
3. advantages: one code base for multiple platforms, easily design for various form factors (including tablets) using responsive web design, have access to some device and os features
4. drawbacks: not all device and native features (fully) supported, risk of being rejected by Apple Store
5. best scenarios: content-driven apps like business, productivity, enterprise, media

## Introduction to Ionic
1. Ionic framework: HTML5 SDK to help build apps with native look and feel, use AngularJS, bring mobile-optimized HTML5 and CSS3 based UI elements
2. using Ionic: `npm install ionic cordova -g, ionic start someApp someTemplate, ionic cordova platform add ios/android, ionic serve`

## Ionic and AngularJS
1. all Angular features are accessible within Ionic, Ionic use Angular UI-Router for SPA, Ionic adds its own services like $loading and directives like <ion-view>
2. Ionic extends ui-router, navigation history is tracked, `<ion-view><ion-content><\ion-view><\ion-content>`
3. Ionic navigation: `<ion-side-menus> <ion-side-menu-content><ion-nav-bar><ion-nav-back-button></ion-nav-back-button></ion-nav-bar><ion-nav-view></ion-nav-view></ion-side-menu-content> <ion-side menu><ion-content>navigation list</ion-content><\ion-side-menu><\ion-side-menus>`

## Ionic CSS Components
1. Ionic introduces a number of CSS classes that enable creation of various UI components, independent of the Ionic Angular directives, use sass to define css classes
2. card class: `<div class=“card”><div class=“item item-divider”></div><div class=“item item-thumbnail-left item-text-wrap”></div></div>`
3. ion-list directive: providevarious interaction modes such as swipe to edit, drag to reorder, and deleting items, `<ion-list><ion-item></ion-item><ion-list>`
4. ionic basic tabs: `<div class="tabs-striped tabs-color-royal"><ul class="tabs"><li class="tab-item">Menu</li> <li class="tab-item">A</li></ul> </div>`
5. ionic grid: similar to Bootstrap grid system, but col sizes specified as percentage with col-\* classes, add responsive classes to row such as responsive-sm

# More Ionic Features

## Ionic Modals and Forms
1. Ionic form: input items forming items of the list, input item's label can be specified using placeholder, inline or stacked or floating labels
2. Ionic Modal: temporarily displayed over main view, controlled from controller in js, `<ion-modal-view><ion-header-bar>Login<div class="buttons"><button class="button button-clear” ng-click="closeLogin()">Close</button></div></ion-header-bar><ion-content><form ng-submit="doLogin()">...</form></ion-content></ion-modal-view>`
3. Ionic Modal JavaScript: `$ionicModal.fromTemplateUrl( 'templates/login.html', {scope: $scope }).then(function (modal) {$scope.modal = modal; }); $scope.closeLogin = function () {$scope.modal.hide();}; $scope.login = function () {$scope.modal.show();}; $scope.doLogin = function () {}; `

## Ionic Lists
1. Ionic provides enhanced lists with delete/reorder/option buttons, `<ion-list><ion-item ng-repeat=”"><ion-option-buttonclass="button-assertive icon ion-plus-circled” ng-click="addFavorite(dish.id)"></ion-option-button><ion-delete-button class="ion-minus-circled” ng-click="deleteFavorite(dish.id)"></ion-delete-button></ion-item></ion-list>`
2. collection-repeat: render DOM only as many items as are currently visible, replace ng-repeat
3. angular custom filter: a factory returning a filter function that takes input as the first argument, and additional filter arguments as additional arguments, `.filter(’someFilter’, function(){return function(input, arg){return newarray;}})`

## Popup, Popover, Action Sheet, Loading, Spinners ang Gestures
1. Popup, Popover, Action Sheet, Loading: overlay content on top of screen, for user interaction, maybe describe content as template, DI as a service like $ionicPopup
2. popup: `var confirmPopup = $ionicPopup.confirm({ title: ': ‘’, template: ‘’}); confirmPopup.then(function(res){});`
3. loading: `$ionicLoading.show({emplate: '<ion-spinner></ion-spinner> Loading…’}); $ionicLoading.hide();`
4. gestures: on-hold,on-tap,on-double-tap,on-touch,on-release, on-drag-up, on-drag right, on-swipe-left, on-swipe-right; give element gestures attribute to invoke a function, `<ion-item . . . on-swipe-left="deleteFavorite(dish.id)”>`

# Deploy Ionic App

## Angular ui-router and Resolve
1. resolve: each state in the ui-router can include a resolve object containing key-value pairs, resolution is done before the its injecting controller ’s instantiation

## Angular $scope and Events
1. publish–subscribe pattern: publisher not send messages directly to receiver but instead characterize published messages into classes without knowledge of which subscribers, subscriber express interest in classes and only receive interesting messages without knowledge of publisher
2. Angular event system: supported on $scope, $scope.$emit fire event up $scope, $scope.$broadcast fire event down $scope, $scope.$on listen for events
3. ui-router events: $stateChangeStart, $stateNotFound, $stateChangeSuccess, $stateChangeError
4. loading message: `$rootScope.$on('loading:show', function () { $ionicLoading.show({}) template: '<ion-spinner></ion-spinner> Loading ...’ }); $rootScope.$on('$stateChangeStart', function () { console.log('Loading ...');$rootScope.$broadcast('loading:show'); });` 

## Local Storage
1. html5 local storage: browsers support local storage using a simple key-value pair, only store string, `window.localStorage[‘key’] = ‘value’;`
2. $localStorage service: `.factory('$localStorage', ['$window', function($window) {return {store: function(key, value) {$window.localStorage[key] = value; },get: function(key, defaultValue) {return $window.localStorage[key] || defaultValue;},storeObject: function(key, value) {$window.localStorage[key] = JSON.stringify(value); },getObject: function(key,defaultValue) {return JSON.parse($window.localStorage[key] || defaultValue);} }}])`

## Install and Deploy
1. install sdk and platform: [Android Platform Guide](http://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html), [IOS Platform Guide](http://cordova.apache.org/docs/en/latest/guide/platforms/ios/index.html)
2. add platform: `ionic cordova platform add android/ios`
3. emulate: `cordova build android/ios, cordova emulate android/ios`
4. delpoy to android device: `cordova run android`

# Access Native Capabilities: Cordova and ngCordova

## Cordova and ngCordova
1. Cordova: Wrappers targeted to different platforms, Enables access to native device’s capabilities througha JavaScript API, Ionic apps are packaged using Cordova to enable access to the native device
2. ngCordova: a collection of 70+ AngularJS extensions on top of the Cordova API, cordova plugins works together with ngCordova wrapper, `module(‘someApp', ['ionic', 'ngCordova', . . . ])`

## Splash Screen
1. install cordova plugin: `cordova plugin add <details of plugin>`
2. ionic resources: automatically construct icon and splash screen resources for various screen sizes into resources folder
3. ngCordova wrapper for splash screen: `$ionicPlatform.ready(function() {$cordovaSplashscreen.hide(); });`

## Notify User
1. local notification: `$cordovaLocalNotification.schedule({id: 1,title: "",text: “"}).then(function () {}, function () {});`
2. toast message: `$cordovaToast .show('Added Favorite '+$scope.dishes[index].name, 'long', 'center').then(function (success) {}, function (error) {});`

## Access Camera
1. cordova-plugin-camera: `$cordovaCamera.getPicture(options) .then(function(imageData) {$scope.registration.imgSrc = "data:image/jpeg;base64," + imageData;}, function(err) {console.log(err); });`
2. camera data: string containing base64-encoded photo image and representing the image file location on local storage (default)
3. camera options: specified as a JS object; quality,destinationType,sourceType,encodingType, targetWidth, targetHeight, mediaType, saveToPhotoAlbum etc.

