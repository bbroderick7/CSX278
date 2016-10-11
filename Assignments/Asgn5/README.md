# Assignment 5 Spec (ELK)

## Elasticsearch, Logstash, and Kibana Reading (before 10/6)

What the stack is from the creators:

- [Kibana](https://www.elastic.co/products/kibana)
- [Elasticsearch](https://www.elastic.co/products/elasticsearch)
- [Logstash](https://www.elastic.co/products/logstash)

Using the stack:

- [The Complete Guide to the ELK Stack](http://logz.io/learn/complete-guide-elk-stack/)
- [Logstash Tutorial: How to Get Started](http://logz.io/blog/logstash-tutorial/)
- [Using Kibana for the First Time](https://www.elastic.co/guide/en/kibana/3.0/using-kibana-for-the-first-time.html)
- [Elastic Search 101](http://joelabrahamsson.com/elasticsearch-101/)
- [Monitoring Your JHipster Application](https://jhipster.github.io/monitoring/)


### Acknowledgements

The preliminary reading material comes from the creators of the ELK stack.

Reading was also selected based on the [recommendations](http://logz.io/blog/10-resources-you-should-bookmark-if-you-run-your-own-elk-stack/) of Daniel Berman, who works at Logz.io, which is a log platform built on the ELK Stack.

The other articles selected were written by people with extensive experience using the ELK Stack. Asaf Yigal is the co-founder of Logz.io, which is based on the ELK Stack. Jurgens du Toit also works at Logz.io and works extensively with Logstash and Elasticsearch.

## Assignment Spec

Please turn in Part 1 for credit. In order to help you enjoy your fall break, Part 2 will be counted as extra credit.

### Before Class

#### Goals
1. To setup Logstash, Elasticsearch, and Kibana on your machine
2. To install node.js on your machine
3. To run each application to make sure it is operating

#### Installing ElasticSearch
1. Download the ElasticSearch Zip from https://www.elastic.co/downloads/elasticsearch
2. Extract the files from ElasticSearch and put them on your desktop or another easily accessible folder
3. Open your Command Prompt and type ‘curl --version’. If this command fails, git is not in your system’s path. Research how to add a command to your system’s path (this should not be a problem on Mac)
4. Using your Command Prompt, navigate to the  elasticsearch-2.4.0/bin/ folder and type `./elasticsearch.bat` (Windows) or `./elasticsearch` (Mac)
5. The server should be running! You’re now ready to begin the tutorial. Open another command window(leave the previous one open) and you can start querying the database.

##### Check ElasticSearch

Before class, start the server and run `curl -X GET http://localhost:9200` in a different command window. Send the resulting JSON to a Ashley Peck (ashley.m.peck@vanderbilt.edu) before class to show you have Elasticsearch setup.

#### Installing Kibana

1. Download Kibana Zip from https://www.elastic.co/guide/en/kibana/current/setup.html
2. Extract the files from Kibana and put them on your desktop or another easily accessible folder
3. Navigate the kibana bin folder and type `./kibana.bat` for windows or `./kibana` for Mac

##### Check Kibana

Before class, start the Kibana server and navigate to localhost:5601 in a browser. Include a screenshot of this in your email to Ashley.

#### Installing Node.js

Go to https://nodejs.org/en/download/ and download node onto your machine.  Open the installer and follow the instructions to complete installation.  Once you’ve installed node, open your terminal and enter the command “node -v”.  This should return a version number.  Send a screenshot of the resulting version.  Note: before running the provided client.js file you must install the elasticsearch javascript package using node package manager.  This can be done by navigating to the folder that contains client.js in your terminal and entering the command “npm install elasticsearch”.  You may now run client.js with the command “node client.js”.  For anything to occur your instance of elasticsearch must be up and running when you execute client.js.

#### Installing Logstash

Note: for the purposes of this assignment, Logstash does not need to be installed independently as the JHipster Console will download it for you in the second part of the assignment. Instructions for installation are included below if you want to use the ELK stack independent of this project.

1. Download Logstash Zip from https://www.elastic.co/downloads/logstash
2. Create a .conf file specifying inputs, filters and outputs
3. Navigate to the directory containing the extracted logstash files
4. Run `bin/logstash.bat agent -f logstash.conf` on Windows or `bin/logstash agent -f logstash.conf` (Where logstash.conf is the .conf created earlier)

### Part 1 (In class) - Intro to Elasticsearch and Kibana

#### Goals:

1. To familiarize yourself with the JSON data format used with Elasticsearch
2. To learn how to create and populate an index in Elasticsearch
3. To learn how to query an elasticsearch database (including filtering results)
4. To learn how to delete a document and an index in Elasticsearch

#### Setup:

The first thing we need to do is start up our instance of Elasticsearch.  Use the terminal to navigate to the bin folder within the Elasticsearch folder you downloaded.  Once you are in this folder, run the “elasticsearch” executable (or the “elasticsearch.bat” executable if you are on Windows).  You should see it begin setup.  After it finishes, you can communicate with your Elasticsearch instance through a REST-based API on localhost port 9200. In this part of the assignment, you will be filling in parts of code included in this assignment folder.

We will be using a dataset of James Bond movies throughout this portion of the assignment.  The first step is to place all of the movies into an index (a query that does this has been done for you except for the first movie).  A table of the movies can be found in the “Box Office and Budget” table here: https://en.wikipedia.org/wiki/List_of_James_Bond_films.

Note: We are using the “setTimeout()” function to run our elasticsearch commands to ensure that they happen in the desired order.  

#### Step 1: Creating, Populating, and Deleting an Elasticsearch Index

1. addMovie1(): Create an index called “bond_movies” and populate it with the first bond movie (“Dr. No”) with an id of 1.
2. addBondMovies(): Populate the index with the rest of the bond movies found in the table (Hint: use “bulk” command).
3. createTest(): Create a new index called “test” and populate it with one document of your choosing.  
4. deleteTest(): Delete this new document from the index.

#### Step 2: Writing Elasticsearch Queries

1. queryAll(): Write a query that returns all of the movies
2. getID1(): Write a query that returns the movie with an ID of 1 (should return “Dr. No”)
3. queryKill(): Write a query_string query that returns all movies that have the word “kill” in the title (should have 2 hits)
4. query1967(): Write a term query that returns all movies made in 1967 (should have 2 hits)
5. queryCasino1967(): Write a filtered query that returns all movies made in 1967 with the word “Casino” in the title (should have 1 hit)

#### Step 3: Intro to Kibana:

1. Start up your Kibana instance (follow the above Elasticsearch instructions only for the Kibana folder).
2. Point your browser to “localhost:5601”.  This should take you to the Kibana dashboard.
3. Create a visualization that shows what percentage of bond movies have Sean Connery starring as James Bond.  Add that visualization to your dashboard.

#### Turn in

Add your code to Solutions/Asgn5 in your repository.

### Part 2 - Using the ELK Stack with Log Data

#### Goals
The goal of this assignment is to learn how to use the JHipster Console to monitor the performance and logging of a JHipster service. This console uses the ELK stack, and it is much easier to implement than trying to implement each layer of the stack independently.

#### Installation
 This project will build on the JHipster Microservice Team's project. Read through The [JHipster Console Installation Instructions](https://jhipster.github.io/monitoring/) to learn about the console.
 
##### Necessary Changes

The console is easy to set up once you have a working JHipster Microservice. Remove the `docker-compose.yml` file you generated in the previous assignment. Inside the docker-compose directory, run `yo jhipster:docker-compose` to generate a new docker-compose file. This yes, select "Yes" when it asks if you want to integrate the JHipster Console. This will generate the necessary files including the new `docker-compose.yml` file that includes the services necessary to generate logs and run the console.

If you are running a Windows machine, you may need to replace this file with the `docker-compose.yml` file included in this directory (similar to the previous assignment).

You can now start the containers by running `docker-compose up -d`. Once the containers start, you can access the console by directing a browser to `machine-ip:5601`. You can find your machine's ip by running `docker-machine ip`.

##### Instructions

Start your service and JHipster console.

###### Adding Visualization To Dashboard

Kibana comes with some pre-made visualizations that you can quickly add to your dashboard. Navigate to the "Dashboard" tab in the JHipster console and add the pre-made visualization "Log Count". Click on the name in the legend and change the color of the series. Click the arrow at the bottom chart and select the "Request" option. Copy the json object into a file called **"logcountrequest.json"**. Next, select the "Response" option and copy the json object into a file called **"logcountresponse.json"**. It is very important that you follow the correct naming conventions or the tests will not pass. In Kibana, you can also create your own visualizations that are more specific to your project.

###### Creating Custom Visualizations

You will first create a visualization based on the automatically added performance metrics. Navigate to the JHipster console in a browser and select the "Visualize" tab. From here, create a new line chart using the logstash pattern that maps the number of "INFO" logs over time. Under "buckets" you will choose "x-axis" with a "Date Histogram" aggregation, "@timestamp" field and and "Auto" Interval. The y-axis should be labeled "INFO Logs" and the x-axis should be "@timestamp per 30 seconds". Save this visualization as "INFO Logs Over Time" and then add it to your dashboard. Click the arrow at the bottom chart and select the "Request" option. Copy the json object into a file called **"infologsrequest.json"**. Next, select the "Response" option and copy the json object into a file called **"infologsresponse.json"**.

The last visualization you should create is one of your choosing. Use a new query and design the visualization however you like. Add this new visualization to your dashboard. Click the arrow at the bottom chart on the dashboard and select the "Request" option. Copy the json object into a file called **"myrequest.json"**. Next, select the "Response" option and copy the json object into a file called **"myresponse.json"**.

To turn in this part of the assignment, create the folder Solutions/Asgn5 in your repo and add the 8 json files and a screenshot of your dashboard.

#### Turn in
Your final repository directory should contain the following files:

1. client.js
2. logcountresponse.json
3. logcountrequest.json
4. infologsrequest.json
5. infologsresponse.json
6. newobjectrequest.json
7. newobjectresponse.json
8. myrequest.json
9. myresponse.json
10. a screenshot of your dashboard

It is very important that the json files are correctly named. For your visualizations to be correct, they must display results (no empty query sets).

### Team Members

- Malla,Janak
- Nguyen,Amy
- Peck,Ashley M
- Kim,Kyuhoon
- Quinones,Peter J
- Dubashi,Arjun
- Zhan,ZeJian
- Hurd,Sam P

