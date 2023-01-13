# Project4-MEAN

In this Task
we are going to implement a simple Book Register web form using MEAN stack.

so this are the steps to follow below

Step 1: Install NodeJs
Node.js is a JavaScript runtime built on Chrome’s V8 JavaScript engine. Node.js is used in this tutorial to set up the Express routes and AngularJS controllers.

so you will use this command below to Update your ubuntu

sudo apt update

<img width="1440" alt="Screenshot 2022-12-23 at 11 54 05" src="https://user-images.githubusercontent.com/118350020/209323763-bb83298d-39d0-44d3-9fa8-ade8cb88d8fc.png">

after that, you need to also Upgrade your ubuntu as well, using the code below

sudo apt upgrade

<img width="1440" alt="Screenshot 2023-01-03 at 14 32 52" src="https://user-images.githubusercontent.com/118350020/210367516-34215287-c3ee-4890-b153-78b0392d9649.png">

so after the upgrade,  we. are going to add this certificate below

Add certificates

sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates

<img width="1440" alt="Screenshot 2023-01-03 at 14 37 12" src="https://user-images.githubusercontent.com/118350020/210367963-1ec87d80-2356-470d-84f7-febb435a7485.png">

here is the second step for the certificate

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

<img width="1440" alt="Screenshot 2023-01-03 at 14 39 27" src="https://user-images.githubusercontent.com/118350020/210368428-7d9253d0-e6f9-4a77-9b4b-656ef60fbcbc.png">

so we are installing, NodeJS with the command below

sudo apt install -y nodejs
 so after installing the nodejs, we are going to move to Step 2 which is the Installation of MongoDB
 
 To do that, we are going to follow this step below
 
 MongoDB stores data in flexible, JSON-like documents. Fields in a database can vary from document to document and data structure can be changed over time. For our example application, we are adding book records to MongoDB that contain book name, isbn number, author, and number of pages.
mages/WebConsole.gif

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6

<img width="1440" alt="Screenshot 2023-01-03 at 15 49 15" src="https://user-images.githubusercontent.com/118350020/210381974-8373572c-e0b0-46d1-9c75-e0df17dab998.png">

so after this we are going to add the next key below


echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list

<img width="1440" alt="Screenshot 2023-01-03 at 15 57 46" src="https://user-images.githubusercontent.com/118350020/210382566-ea3d4033-cc2d-457e-9531-45e324d2933d.png">


now we are going to install MongoDB with the below command

sudo apt install -y mongodb

<img width="1440" alt="Screenshot 2023-01-09 at 14 49 26" src="https://user-images.githubusercontent.com/118350020/211323207-67806b9a-3d92-4c9f-b2d7-14ed8763b9aa.png">

so once you finish with the mongodb installation, you also. 
need to start to be sure you installed it correctly.
so we are going to use this command below

sudo service mongodb start 
and you also need to verify the status as well,  with this command line
sudo systemctl status mongodb

<img width="1440" alt="Screenshot 2023-01-09 at 15 03 03" src="https://user-images.githubusercontent.com/118350020/211326018-877091be-bb23-4c40-ad24-541205d39d60.png">

as you can see, mongodb is active and running

so the next step is to install resiposotory also known as package, with the command below

sudo apt install -y npm
<img width="1440" alt="Screenshot 2023-01-09 at 15 28 10" src="https://user-images.githubusercontent.com/118350020/211331852-04681fa1-0d51-47db-a5c9-dae5fc7e0436.png">
 so we also need body parser packaged  to help us process JSON files passed in requests to the server.
 so we are going to use the command line below to run that

sudo npm install body-parser
<img width="1440" alt="Screenshot 2023-01-09 at 15 36 31" src="https://user-images.githubusercontent.com/118350020/211333320-9793f558-4b7e-41a3-a77e-c09eea55de5c.png">
the next thing we have to do now is to Create a folder named ‘Books’ with the command below

mkdir Books && cd Books

<img width="1440" alt="Screenshot 2023-01-09 at 15 46 46" src="https://user-images.githubusercontent.com/118350020/211336518-daac19de-0176-4339-9af0-cd6a6f724103.png">

 so from here , we are going to Initialize npm project In the Books directory, with. this below command
 npm init
 
 <img width="1440" alt="Screenshot 2023-01-09 at 15 54 28" src="https://user-images.githubusercontent.com/118350020/211337862-b7eea76b-6efc-446a-bcab-317654fd027f.png">
 
 so we need to add a file called. 
<img width="1440" alt="Screenshot 2023-01-09 at 15 46 46" src="https://user-images.githubusercontent.com/118350020/211336518-daac19de-0176-4339-9af0-cd6a6f724103.png
                                                               
so we are going to add a file named server.js with the cammand below
vi server.js
<img width="1440" alt="Screenshot 2023-01-12 at 15 33 26" src="https://user-images.githubusercontent.com/118350020/212094430-e36ad4d3-46ee-41f4-9147-2fa18e311243.png">

Copy and paste the web server code below into the server.js file.

var express = require('express');
var bodyParser = require('body-parser');
var app = express();
app.use(express.static(__dirname + '/public'));
app.use(bodyParser.json());
require('./apps/routes')(app);
app.set('port', 3300);
app.listen(app.get('port'), function() {
    console.log('Server up: http://localhost:' + app.get('port'));
});

<img width="1440" alt="Screenshot 2023-01-12 at 15 36 23" src="https://user-images.githubusercontent.com/118350020/212095010-8f30acf0-3b1a-4ddb-9a63-4d6a9bc20eb9.png">

now we are going to the final stage
so we are going to INSTALL EXPRESS AND SET UP ROUTES TO THE SERVER

Step 3: Install Express and set up routes to the server
Express is a minimal and flexible Node.js web application framework that provides features for web and mobile applications. We will use Express in to pass book information to and from our MongoDB database.

We also will use Mongoose package which provides a straight-forward, schema-based solution to model your application data. We will use Mongoose to establish a schema for the database to store data of our book register.

so we are going to use this command below
sudo npm install express mongoose

<img width="1440" alt="Screenshot 2023-01-12 at 15 48 49" src="https://user-images.githubusercontent.com/118350020/212098177-c504d822-e27b-449a-a877-791b03f9f28d.png">

so In ‘Books’ folder, we are going to create a folder named apps with the below  command
mkdir apps && cd apps

so we are going to Create a file named routes.js with the command below

vi routes.js

<img width="1440" alt="Screenshot 2023-01-12 at 16 05 40" src="https://user-images.githubusercontent.com/118350020/212102555-3a1cd678-7e40-424f-bebe-bad89d934370.png">
and we are going to Copy and paste the code below into routes.js

var Book = require('./models/book');
module.exports = function(app) {
  app.get('/book', function(req, res) {
    Book.find({}, function(err, result) {
      if ( err ) throw err;
      res.json(result);
    });
  }); 
  app.post('/book', function(req, res) {
    var book = new Book( {
      name:req.body.name,
      isbn:req.body.isbn,
      author:req.body.author,
      pages:req.body.pages
    });
    book.save(function(err, result) {
      if ( err ) throw err;
      res.json( {
        message:"Successfully added book",
        book:result
      });
    });
  });
  app.delete("/book/:isbn", function(req, res) {
    Book.findOneAndRemove(req.query, function(err, result) {
      if ( err ) throw err;
      res.json( {
        message: "Successfully deleted the book",
        book: result
      });
    });
  });
  var path = require('path');
  app.get('*', function(req, res) {
    res.sendfile(path.join(__dirname + '/public', 'index.html'));
  });
};
                                                
 <img width="1440" alt="Screenshot 2023-01-12 at 16 09 21" src="https://user-images.githubusercontent.com/118350020/212103794-4de968d2-d20f-4377-a71d-cbe71b5204d1.png">                                              
 
 <img width="1440" alt="Screenshot 2023-01-12 at 16 09 30" src="https://user-images.githubusercontent.com/118350020/212103964-1609a231-f616-4e69-9fb9-f8002ed2b499.png">

    so in the app folder , we are going create a folder named models by using the cammand below
    
    mkdir models && cd models
    
    after this we are now going to Create a file named book.js with the command
    
    vi book.js
    
    <img width="1440" alt="Screenshot 2023-01-12 at 16 09 30" src="https://user-images.githubusercontent.com/118350020/212106139-cf579cf9-a77e-49d0-972b-edeae64680bc.png">
So after doing that, we are now going to Copy and paste the code below into ‘book.js’

var mongoose = require('mongoose');
var dbHost = 'mongodb://localhost:27017/test';
mongoose.connect(dbHost);
mongoose.connection;
mongoose.set('debug', true);
var bookSchema = mongoose.Schema( {
  name: String,
  isbn: {type: String, index: true},
  author: String,
  pages: Number
});
var Book = mongoose.model('Book', bookSchema);
module.exports = mongoose.model('Book', bookSchema);    

<img width="1440" alt="Screenshot 2023-01-12 at 16 20 24" src="https://user-images.githubusercontent.com/118350020/212106641-811f9d1d-1a17-40c2-9bf4-d65d218e9440.png">

So on our step 4, we are going Access the routes with AngularJS

AngularJS provides a web framework for creating dynamic views in your web applications. In this documentation we are going to use AngularJS to connect our web page with Express and perform actions on our book register.

so firstly we are going to Change the directory back to ‘Books’ using the  command below

cd ../..

so after that,  we are going to Create a folder named public. using the command below

mkdir public && cd public

And we are going to Add a file named script.js with the below command 

vi script.js

<img width="1440" alt="Screenshot 2023-01-12 at 16 20 24" src="https://user-images.githubusercontent.com/118350020/212108692-fcb0d193-ef1d-4419-a2a9-cab2de52b9b9.png">

So we are to Copy and paste the Code below (controller configuration defined) into the script.js file.

var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http( {
    method: 'GET',
    url: '/book'
  }).then(function successCallback(response) {
    $scope.books = response.data;
  }, function errorCallback(response) {
    console.log('Error: ' + response);
  });
  $scope.del_book = function(book) {
    $http( {
      method: 'DELETE',
      url: '/book/:isbn',
      params: {'isbn': book.isbn}
    }).then(function successCallback(response) {
      console.log(response);
    }, function errorCallback(response) {
      console.log('Error: ' + response);
    });
  };
  $scope.add_book = function() {
    var body = '{ "name": "' + $scope.Name + 
    '", "isbn": "' + $scope.Isbn +
    '", "author": "' + $scope.Author + 
    '", "pages": "' + $scope.Pages + '" }';
    $http({
      method: 'POST',
      url: '/book',
      data: body
    }).then(function successCallback(response) {
      console.log(response);
    }, function errorCallback(response) {
      console.log('Error: ' + response);
    });
  };
});

<img width="1440" alt="Screenshot 2023-01-12 at 16 29 02" src="https://user-images.githubusercontent.com/118350020/212109359-a3dab53b-6c36-4115-bf3c-96222cb49689.png">                                     

So in our In public folder,we are going to create a file named index.html;  with the below command

vi index.html

<img width="1440" alt="Screenshot 2023-01-12 at 16 29 02" src="https://user-images.githubusercontent.com/118350020/212110068-ddd24ea2-a56d-49d0-b96c-5b62f06110a3.png">

and later copy and paste the code below into index.html file.

<!doctype html>
<html ng-app="myApp" ng-controller="myCtrl">
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
    <script src="script.js"></script>
  </head>
  <body>
    <div>
      <table>
        <tr>
          <td>Name:</td>
          <td><input type="text" ng-model="Name"></td>
        </tr>
        <tr>
          <td>Isbn:</td>
          <td><input type="text" ng-model="Isbn"></td>
        </tr>
        <tr>
          <td>Author:</td>
          <td><input type="text" ng-model="Author"></td>
        </tr>
        <tr>
          <td>Pages:</td>
          <td><input type="number" ng-model="Pages"></td>
        </tr>
      </table>
      <button ng-click="add_book()">Add</button>
    </div>
    <hr>
    <div>
      <table>
        <tr>
          <th>Name</th>
          <th>Isbn</th>
          <th>Author</th>
          <th>Pages</th>

        </tr>
        <tr ng-repeat="book in books">
          <td>{{book.name}}</td>
          <td>{{book.isbn}}</td>
          <td>{{book.author}}</td>
          <td>{{book.pages}}</td>

          <td><input type="button" value="Delete" data-ng-click="del_book(book)"></td>
        </tr>
      </table>
    </div>
  </body>
</html>
                                                                                
                                                                                
<img width="1440" alt="Screenshot 2023-01-12 at 16 34 51" src="https://user-images.githubusercontent.com/118350020/212110689-d560ee77-8985-4858-a05f-d061a68225ef.png">                                                                              
<img width="1440" alt="Screenshot 2023-01-12 at 16 34 56" src="https://user-images.githubusercontent.com/118350020/212110800-49a2dae6-3c48-413c-97e0-eb4a588c6f8b.png">

so we are going to Change the directory back up to Books using the below command

cd ..

we can now Start the server by running this command below 

node server.js

<img width="1440" alt="Screenshot 2023-01-13 at 14 40 50" src="https://user-images.githubusercontent.com/118350020/212333563-9ad47401-87bb-48e4-96fd-ded3e1d38b19.png">

so your final outcome should look like this screenshoot below

<img width="1440" alt="Screenshot 2023-01-13 at 14 39 33" src="https://user-images.githubusercontent.com/118350020/212333909-2b51fbbe-dc92-4b2e-aa60-019bcf7edabc.png">

<img width="1440" alt="Screenshot 2023-01-12 at 16 34 56" src="https://user-images.githubusercontent.com/118350020/212110800-49a2dae6-3c48-413c-97e0-eb4a588c6f8b.png">

finish
