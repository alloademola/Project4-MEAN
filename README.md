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

