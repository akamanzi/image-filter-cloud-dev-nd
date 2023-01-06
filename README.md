# Udagram Image Filtering Microservice

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. The filtering microservice is a Node-Express application which runs a simple script to filter images returns filtered versions of the images.

## Tasks involved in this project

### Setup Node Environment

You'll need to create a new node server. Open a new terminal within the project directory and run:

1. Clone this repository
2. Install the packages: `npm i`
3. run the development server with `npm run dev`

### Create a filterimage endpoint

Create a new endpoint `filteredimage` which takes as a parameter the image url. This endpoind does the following

  1. Validate the `image_url` parameter
  2. Filter the images
  3. Return the filtered image
  4. Deletes the image after it is returned.

The endpoint uses helper methods below to filter the images.

```typescript
import {filterImageFromURL, deleteLocalFiles} from './util/util';
```

### Deploying your system

This application was deployed to AWS using Elastic Beanstalk (EB). The following steps were followed to deploy the application using EB

1. build the project: run `npm run build` command to build the project into `Archive.zip` in a `www` folder
2. Create EB application: `eb init`, this launches an interactive cli where you enter the details of the application such as application name...etc. In addition this command creates a configuration file which is used when deploying.
3. Create the application environment: `eb create` creates the environment which you want to run the application and deploys the application. For this project a dev environment was created but in a real world scenario, it is ideal to have a staging and production environment.
4. Deploy updates: `eb deploy` updates the environment with new changes.

### Testing the application

To test this application in the web browser add: `http://image-filter-service-dev.us-east-1.elasticbeanstalk.com/filteredimage?image_url=https://upload.wikimedia.org/wikipedia/commons/2/27/Capitol_Building_Full_View.jpg` in the browser of your choice.

This should return filtered version of the image

Using postman:
create a get request add the url: `http://image-filter-service-dev.us-east-1.elasticbeanstalk.com/filteredimage`
Add `image_url` in the params tab and use `https://upload.wikimedia.org/wikipedia/commons/2/27/Capitol_Building_Full_View.jpg` as the value.


**NOTE**: By the time you access this link, the above urls may not be still accessible. In this case it is ideal to run the application locally as indicated in the [setup-node-environment](#setup-node-environment)