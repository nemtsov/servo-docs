# NodeJS
Servo follows several common patterns in the Node.js community. It will run a single node process on each EC2 instance and scale instances horizontally.

Servo also respects the [`engines` field](https://docs.npmjs.com/files/package.json#engines) in the `package.json` for the version of node, and automatically uses the `npm` which matches that version.

Under the covers it uses the npm package [`n`](https://github.com/tj/n) to manage node versions.

## Structure
Servo will auto detect the platform to be `NodeJS` if the root of the repository contains a `server.js` AND `package.json`.

**NOTE**: Both files must exist for auto-detection to work.

In addition, you can skip auto-detection by placing a `.servo` file in the root directory with the following content:
```
{
  "platform": "nodejs"
}
```
*This still requires the existence of `server.js` & `package.json` in the root directory.*

## Build
The build executes the following commands:

1. `npm install --unsafe-perm`
2. `npm test`
3. `npm prune --production`

If the command `npm test` fails, the build will also fail. Ensure all tests are running locally without any environment dependencies.

## Deploy
The app is run using the library [`forever`](https://www.npmjs.com/package/forever) with a fixed `PORT` environment variable. Logs sent to `STDOUT` will be viewable in the log explorer within the console.


## Related
1. [Deployment Basics](Deploy.md)
2. [Docker](Docker.md)
