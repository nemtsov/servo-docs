# Servo (The PaaS)

## What is Servo?
Servo allows developers to deploy their NodeJS or Docker applications on a scalable application infrastructure within the cloud with a click of a button. 

By deploying within Servo, you automatically recieve the following:
* Environments
  * Ability to create multiple stacks for different environments (dev, staging, production)
  * Each can be configured with different environment variables.
* Security
  * App owners can control user permissions on their applications and stacks. 
  * Lock down network access to your application to only trusted IP ranges
* Monitoring
  * Log monitoring for application logs
  * Application & Server monitoring in NewRelic with NodeJS applications (if configured)
* Notifications
  * Email, Slack, Twilio, Webhook, or Opsgenie notifications
  * On any events related to Autoscaling, Site Health, Deployments, etc. 
* SiteControl
  * Manage traffic across multiple regions with failover options
  * Allows app teams to suspend an origin in under 3 minutes
* Many more features that make your life easier! :)

Applications deployed on Servo should follow the [12 Factor App](http://12factor.net/) guidelines.

The purpose of Servo is to abstract the technicalities of the cloud and provide a clean experience for developers to deploy their applications. Through the process of abstracting the details, servo standardizes that creation and management of cloud resources. 
Currently it is built upon Amazon Web Services(AWS), but its principles can be extended to any other cloud provider. 

The documentation is broken up into the following sections:
* [Setup Documentation](setup/README.md)
* [Admin documentation](admin/README.md)
* [User documentation](user/README.md)


##  Common Terminology
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

### [servo-ami](https://github.com/dowjones/servo-ami)
This is the AMI that powers all of the deployments within the PaaS. It sets up a small nginx server in front of your app and installs basic dependencies for Node, Docker & AWS CloudWatch Logs.

### [servo-core](https://github.com/dowjones/servo-core)
The heavy lifter! This layer communicates with AWS via APIs to create an immutable application infrastructure. Each organization can have its own core managing org specific apps within the same AWS account. When deploying an application within servo, it manages AWS resources for deploys so you don't have to.

### [servo-gateway](https://github.com/dowjones/servo-gateway)
The layer that handles permissions within the servo environment. All requests are proxied to through layer & VPCs are configured such that only gateway can communicate with core. Handles the CRUD of user permissions on orgs/apps/stacks. These permissions are handled within a DynamoDB. There only needs to be one gateway per region & it should be aware of the endpoints for particular orgs.


### [servo-console](https://github.com/dowjones/servo-console)
This is a simple React powered single page app which communicates via APIs to the underlying layers of servo. This UI isn't essential for the deployment of an app, but it aggregates data from many different API endpoints to give you a good application overview.
