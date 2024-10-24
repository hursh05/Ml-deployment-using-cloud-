# Ml-deployment-using-cloud-

Overview
In this challenge we developed a crawler application which retrieves information about how many times a link was referenced in another page and save this information in a database. After that, we enriched each link with features of themself. With this features, we made a model to predict references of a link and serves this model in a REST API.

Goals
Develop a Crawler that saves link references in a database;
Develop an API do get features of links (if the link already exists use it features, else create then);
Train a Random Forest that predict link references;
Deploy this model and serves with an API.

Assumptions
The depth of crawler search was defined as 3. You can change this at infra.yaml (inside the BatchEvent Resource);
I used only a few link to create the database because I don't want to be charged by AWS and DynamoDB has a limit of throughput of 5 in the free-tier (for read and write);
After crawler finished, I used the export to S3 function of DynamoDB and downloaded the data to train the model in my local machine.

Future works
All this work was developed with free-tiers components in order to reduce costs. For future works we can do:

Change DynamoDB ProvisionedThroughput for PAY_PER_REQUEST, in other to scales our application;
Create the buckets in another repository, in order to don't have problems when we need to delete the stack;
Create CI steps to test the integration between components, not only unit tests;
Change Lambda predict to an on-demand instance, in order to reduce cold start.
