# cf-node-mongo
# Node Cellar Sample Application with Backbone.js, Twitter Bootstrap, Node.js, Express, and MongoDB#

"Node Cellar" is a sample CRUD application built with with Backbone.js, Twitter Bootstrap, Node.js, Express, and MongoDBto be deployed on Pivotal Cloud Foundry.

The application allows you to browse through a list of wines, as well as add, update, and delete wines.

The application is also hosted online. You can test it [here](http://nodecellar.cfapps.io).


## To run the application on Cloud Foundry:##

1. Install the [Cloud Foundry CLI](https://github.com/cloudfoundry/cli)

2. [Sign up](http://run.pivotal.io/) for a Pivotal Web Services account

3. Git clone this repository 

        $ git clone https://github.com/kingfadzi/cf-node-mongo
        
4. Install npm modules

        $ cd [my-app-directory]
        $ npm install body-parser
        $ npm install express
        $ npm install mongodb
        $ npm install mongodb-uri
        $ npm install sockets.io
        
5. Log into Cloud Foundry

        $ cd [my-app-directory]
        $ cf api api.[my-cloudfoundry].com
        Setting api endpoint to https://api.[my-cloudfoundry].com...
        OK
        
        $ cf login
        API endpoint: https://api.[my-cloudfoundry].com
        
        Email> [my-email]
        
        Password> [my-password]
        Authenticating...
        OK

6. List available services

        $ cf marketplace
        service          plans                    description
        ....
        mongolab         sandbox                  Fully-managed MongoDB-as-a-Service
        ...


6. Create mongodb Service Instance called "cf-workshop-node"

        $ cf create-service mongolab sandbox cf-workshop-node


7. Give your application a name in the 'manifest.yml' file

        applications:
        - name: [appname]
          memory: 512M
          instances: 1
          timeout: 60
          services:
           - cf-workshop-node



8. Push the app (from the application root directory)

        $ cf push 

9. Go to your browser http://[appname].cfapps.io


## To run the application on local machine:## 

1. Install mongodb
2. Create a database called "cf-workshop-node"
3. Run the app

        $ cd [my-app-directory]
        $ node server.js
        
4. Fire up web browser and point to: http://localhost:3000

## Issues:## 
1. db.listCollections seems to return 'undefined'
2. kill button requires a browser manual reload.. need to auto-reload the current page to show site is down
3. Allow multiple click of the same menu item (currently you have to go another link then return, for link to work.. its probably a backbone.js feature?)
4. collection name is hardcoded

