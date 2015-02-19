#lahirajudDOTcom
Code Camper with Breeze, Mongo, Express, Angular, and Node

## Requirements
- MongoDB
- Node.js
- NPM
- Bower

## Setup
1. Unzip `/src/server/data/ngCodeCamper.zip` to expand the Mongo database
2. Run `npm install` (this will run `bower install` for you)

### MongoDB
Install mongo via [Home Brew](http://brew.sh/) via Mac. Or install on Windows using from [MongoDB web site instructions](http://www.mongodb.org/downloads).

    brew install mongodb

After installing MongoDB, open this file `src\server\data\mongodb.config` add your path to location of your database. It may look something like this:

```
dbpath=/Users/username/documents/lahirajudDOTcom/server/data/ngCodeCamper
```

## Running CC-BMEAN
1. Run the MongoDB `mongod --config server/data/mongodb.config`
2. `gulp serve-dev`
4. Browse to [http://localhost:3001](http://localhost:3001)

# MongoDB and WebStorm

## MongoDB Primer
http://openmymind.net/mongodb.pdf

## Install
http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/

## Permissions
Allow users to read the the database
`sudo chown `id -u` /data/db`

### Config
	#logpath=c:\mongodb\log\mongo.log
	dbpath=/Users/username/mongodb/data
	rest=true

## Module Structure
Example structure may look like this:

```
app --> [
          app.featureA
          app.featureB
          app.featureC
          app.layout
          app.widgets
        ]  --> app.core --> [
                                common,
                                blocks.logger,
                                blocks.exception,
                                ui-bootstrap,
                                ngRoute,
                                ngAnimate
                            ]
```

### app
The `app` module is the root of the entire application. This would be named more appropriately to reflect the application. Little or no functionality is here other than aggregating all of the app features which are in other module dependencies.

The `app` module depends on feature modules, which use the naming convention `app.*`

### app.* modules
The `app.*` modules are feature areas for the main app. These all depend on `app.core`.

One example may be `app.orders` which may be a feature area for order information int he app. There may also be `app.layout` which contains all the layout logic for the app, such as login, navbars and menus. There may also be app specific widgets in `app.widgets`.

### app.core
The `app.core` module contains all application specific services and shared code that all (or most) features may require. Thus the `app.*` modules depend on `app.core`.

The `app.core` module also serves as an agregator of all generic, common, 3rd party, and angular modules that are shared across the application. These may include common function helpers, reusable blocks such as a logger, ui-bootstrap or kendo integration, and ngRoute (ng* modules).

### common
The `common` module contains code that may be useful to many applications. Generally very small helpers.

### blocks.*
The `blocks.*` modules contains reusable blocks such as logging and exception handling that can be used by any app.

