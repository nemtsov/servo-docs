# Servo (The PaaS)

Made by developers for developers!

Applications deployed on Servo should follow the [12 Factor App](http://12factor.net/) guidelines.

[Deployment Basics](Deploy.md)

## Quick Start
1. Push code to GitHub
2. Create an App in Servo linked to the GitHub repo
3. Create a Stack
4. Run a Build of the commit you would like to Deploy
5. After the Build completes, Deploy the Build to the Stack
6. Configure the Network Access for the Stack to allow traffic
7. Access the Stack through one of the Endpoint links on the Stack page
8. Take some time for yourself with all the time you just saved!


## Terminology
### Org
An isolated Servo environment with separate permissions and networks.

### Region
An AWS region, pretty simple.

### App
A codebase from specific code repository within a specific Org and Region.
### Stack
An isolated instance of an App, very similar to environments. Servo supports the concept of number of Stacks of an App. You can have a traditional set of stacks like dev, staging, and production or you can create Stacks for each team member or stakeholder group. They no predefined impact on the runtime of your app.

### Build
A specific commit from the GitHub repo that has gone through a user-defined build script. This script is usually used to install dependencies, compile assets, and run tests. Builds are stored as immutable artifacts on AWS S3 in the Region.

### Deploy
An event to push code and config changes to a stack.

## Components

### [servo-core](http://github.com/dowjones/servo-core)
The heavy lifter! This layer communicates with AWS via APIs to create an immutable application infrastructure. Each organization can have its own core managing org specific apps within the same AWS account. When deploying an application within servo, it manages AWS resources for deploys so you don't have to.

### [servo-gateway](http://gihub.com/dowjones/servo-gateway)
The layer that handles permissions within the servo environment. All requests are proxied to through layer & VPCs are configured such that only gateway can communicate with core. Handles the CRUD of user permissions on orgs/apps/stacks. These permissions are handled within a DynamoDB. There only needs to be one gateway per region & it should be aware of the endpoints for particular orgs.


### [servo-console](http://github.com/dowjones/servo-console)
This is a simple React powered single page app which communicates via APIs to the underlying layers of servo. This UI isn't essential for the deployment of an app, but it aggregates data from many different API endpoints to give you a good application overview.
