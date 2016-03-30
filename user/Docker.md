# Docker
Servo supports the use of Docker as a packaging format to allow engineers to express their custom needs for how to Build and Deploy their application. Servo deploys a single Docker container to each EC2 instance and scales horizontally just like our other platforms.


## Structure
Servo will auto detect the platform to be `Docker` if the root of the repository contains **only** a `Dockerfile`.

In addition, you can skip auto-detection by placing a `.servo` file in the root directory with the following content:
```
{
  "platform": "docker"
}
```
*This still requires the existence of a `Dockerfile` in the root of the repository.*

The Dockerfile should add the code to the image & run the application at the end. This means that the last line of the Dockerfile should be a `CMD` entry that runs the application. *No arguments can be passed into the `docker run` command.*

## Build
The build process is very simple and just calls one command: `docker build` from the root of your repository. No additional parameters are passed in during the build process and the resulting image is saved and pushed to S3.

**NOTE**: As a developer, you need to ensure your application currently works within your container!

## Deploy
When deploying a Dockerized application with servo, the environment variables are packaged into a file and passed into the container using the `--env-file` option.
The resulting run command looks like the following:

`docker run --restart=always --env-file=/home/app/envfile`

*A small note about logs*: Even though your application may generate log files within the container, servo will only be able to display what is being logged to `STDOUT`. This would be the same if you typed `docker logs`, while the container was running.


## Related
* [Deployment Basics](Deploy.md)
* [NodeJS](NodeJS.md)
