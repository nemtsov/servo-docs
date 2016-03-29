# Deploying an Application

Currently servo can build/deploy Docker containers and native NodeJS applications.
A `deployment` is broken into two steps:

1. Build
2. Deploy

The `build` process, takes your code and packages it into a build artifact and pushes it to S3. These build artifacts are environment agnostic and shouldn't necessarily vary based on staging/production. The idea is to take the same build that works in staging and deploy it to a production stack. For this reason, servo does not allow different builds/build processes based on environment.

The `deploy` process, uses an existing build and deploys it on a scalable application infrastructure with a click of a button. Environment variables set from the `Configure` tab will be passed into the application on every deploy. The different runtime behavior can be dictated by these environment variables.

## Application basics

1. App server must listen to the `PORT` environment variable.
  * `53840` for Node 
  * `80` for Docker.
2. Should respond with a `200` for the route `/_health`;

## Supported platforms
1. [NodeJS](NodeJS.md)
2. [Docker](Docker.md)
