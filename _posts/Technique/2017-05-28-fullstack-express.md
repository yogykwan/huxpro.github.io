---
layout:     post
title:      "Server-side Development with NodeJS: Express"
subtitle:   ""
date:       2017-05-28
author:     "Jennica"
header-img: "img/post-bg-fullstack.jpg"
catalog: true
tags:
    - 技术
    - Web
    - 后台
---

# Related

- [Project - conFusion](https://github.com/yogykwan/conFusion)
- [Course - Full Stack](https://www.coursera.org/specializations/full-stack)

# Server-side Development

## Node Modules
1. node module: each file in Node is its own module, module.exports variable determines the export from the current module, require function is used to import a module
2. callback and error handling: `module.exports = function(x,y,callback) {try {if (x < 0 || y < 0) {throw new Error(“error"); }else callback(null, {perimeter: function () { return (2*(x+y)); },area:function () { return (x*y); } });}catch(error){callback(error,null); } }; rect(l,b, function(err,rectangle) {if (err) { console.log(err);} else {}});`
3. node http module: `var http = require('http’); var server = http.createServer(function(req, res){}); server.listen(port, );`
4. node path module: `var path = require('path’); path.resolve('./public'+fileUrl); path.extname(filePath);`
5. node fs module: `var fs = require(‘fs’); fs.exists(filePath, function(exists) {}); fs.createReadStream(filePath).pipe(res);`

## Introduction to Express
1. express: fast, unopinionated, minimalist web framework for node.js, many third-party middleware to extend functionality, `var express = require('express’); var app = express(); var server = http.createServer(app);`
2. express middleware: `var morgan = require(‘morgan’); app.use(morgan(‘dev’));`
3. express generator: app.js, package.json, public, routes, views; `express someApp`

## Express Router
1. express app routes: apply REST verb to app with URI, `app.get('/dishes/:dishId', function(req,res,next){res.end('')});`
2. body parser: parses body of the message and populates the req.body property, `var bodyParser = require('body-parser'); app.use(bodyParser.json());`
3. express router: `var dishRouter = express.Router(); dishRouter.use(bodyParser.json());dishRouter.route('/') .all(. . .);.get(. . .);`

# MongoDB and Mongoose

## Introduction to MongoDB
1. NoSQL: scalability, availability, consistency, partition tolerance, no object-relation mapping required
2. NoSQL categories: document databases (MongoDB), key-value databases (Redis), column-family databases (Cassandra), graph databases (Neo4J)
3. mongodb: store documents in BSON (Binary JSON) format, supports length prefix on each value
4. objectId: every document in Mongo must have an “_id” field that is unique, default created by mongo when inserting a document, 12 byte field (timestamp+machine id+proc. id+increment)

## Node and MongoDB
1. node mongodb driver: provide node app with apis to connect mongodb, crud methods, callback based and promise based interactions

## Mongoose
1. Mongoose ODM: Object Data Model, Object Document Mapping, Object relational mapping (ORM); add structure to mongodb documents through schema
2. connect to mongodb: `var mongoose = require('mongoose’);mongoose.connect(url);var db = mongoose.connection; db.on('error', console.error.bind(console, ‘error')); db.once('open', function () {});`
3. mongoose schema: structure of stored data, used to create model function, `var mongoose = require('mongoose'); var Schema = mongoose.Schema;var someSchema = new Schema({}); var someModel = mongoose.model(’Some’, someSchema);`
4. schema type: String, Number, Date, Buffer, Boolean,Mixed, ObjectId, Array; can do validation
5. REST with mongoose: translate request to an equivalent database operation, `someModel.create({}, )` = `Router().post()`
6. mongoose population: automatically replace specified paths within a document with document from another collection, `someModel.find({}).populate(‘postedBy’).exec();`

# Authentication and Security

## Basic Authentication
1. http basic access authentication: HTTP user agent provide username and password with a request
2. server send client WWW-Authenticate header with Basic, client send authorization header back to server
3. authorization header: begin with authorization method, then encode “username:password” using Base64,  `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`

## Cookies and Sessions
1. http cookie: client can set cookie and store on client, each subsequent request from client will include cookie in header
2. express and cookies: set cookie `res.cookie(name,value,options)`, parse cookie `var cookieParser = require(‘cookie-parser’); app.use(cookieParser());`, attach cookie after parsed `req.cookies.name`
3. express and signed cookies: signed with a secret key on the server side, `var cookieParser = require(‘cookie-parser’); app.use(cookieParser(’secret key’)); req.signedCookies.name`
4. express session: store info on server by default in-memory, set a cookie of  session id to client, then server can track user states, `var session = require('express-session');var FileStore = require('session-file-store')(session); app.use(session()); req.session.property`

## Token-based Authentication
1. shortages of cookie+session authentication: Session authentication becomes a problem when we need stateless servers and scalability, Mobile application platforms have a hard time handling cookies/sessions, sharing authentication isn’t feasible, CORS, CSRF
2. token-based authentication: after validates client’s credential, server create signed token and send it back to client, subsequent requests from client will include token for server to validate and authenticate user
3. jsonwebtoken node module: sign() for signing and issuing token, verify() for verifying and decoding token and making it available on the request property in Express

## Passport
1. passport strategies: Local Strategy, OpenId, Oauth (Facebook, Twitter, G+ etc.) single sign-on
2. invoke authentication: `app.get('/login', function(req, res, next) { passport.authenticate('local', function(err, user, info) {req.logIn(user, function(err) {})(req, res, next);});`
3. passport-local: `passport.use(new LocalStrategy( function(username, password, done) { User.findOne({ username: username }, function (err, user) {if (err) { return done(err); }if (!user) { return done(null, false); }if (!user.verifyPassword(password)) { return done(null, false); } return done(null, user);}); }));`
4. passport-local-mongoose: `passportLocalMongoose = require('passport-local-mongoose’); User.plugin(passportLocalMongoose); passport.use(new LocalStrategy(User.authenticate()));`
5. use static serialize and deserialize of model for passport session support: `passport.serializeUser(User.serializeUser()); passport.deserializeUser(User.deserializeUser());`

## OAuth
1. OAuth roles: resource owner, client app, resource server, authorization server
2. tokens: access token allow client app to access user data, has lifetime and scope, refresh token is to refresh an expired access token
3. authorization code: when client app is a web server, used to obtain a long-lived access token
4. client app registration: register the client application on the OAuth service provider; get client app id, client secret, set redirect URL for client to receive authorization code and access token
5. authorization code grant approach: user request authorization, authorize client app through browser; client app get authorization code, exchange authorization code with access token, request resource with access token
6. oauth passport module: set up facebook strategy `var FacebookStrategy = require('passport-facebook').Strategy; passport.use(new FacebookStrategy({clientID: config.facebook.clientID,clientSecret: config.facebook.clientSecret, callbackURL: config.facebook.callbackURL},function(accessToken, refreshToken, profile, done) {... }}); `, authenticate user `router.get('/facebook', passport.authenticate('facebook'), function(req, res){});router.get('/facebook/callback', function(req,res,next){ passport.authenticate('facebook', function(err, user, info) {...}) (req, res, next);•});`

## HTTPS
1. SSL/TLS handshake: client request server for communication, server send public key and CA to client, client verify server credentials and generate pre-master secret encrypted with server’s public key and send to server, then both generate same session key, from now on symmetric encrypted messages transferred with session key
2. HTTPS: upper layer of SSL/TLS, thus communication is secure
3. node https module: `var https = require('https');var fs = require('fs');var options = {key: fs.readFileSync(__dirname+'/private.key'), cert: fs.readFileSync(__dirname+'/certificate.pem')};var secureServer = https.createServer(options,app);`



