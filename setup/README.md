# Setup Documentation

Most of setup for `servo` requires AWS knowledge.

The setup for each component is contained within the documentation of the repository.

1. [`servo-core`](https://github.com/dowjones/servo-core/blob/release/OS/docs/README.md)
  * [IAM Role](https://github.com/dowjones/servo-core/blob/release/OS/docs/IAM.md)
  * [VPC](https://github.com/dowjones/servo-core/blob/release/OS/docs/VPC.md)
  * [Route53](https://github.com/dowjones/servo-core/blob/release/OS/docs/Route53.md)
  * [S3 Buckets](https://github.com/dowjones/servo-core/blob/release/OS/docs/S3.md)
  * [MongoDB](https://github.com/dowjones/servo-core/blob/release/OS/docs/Mongo.md)
  * [SQS](https://github.com/dowjones/servo-core/blob/release/OS/docs/SQS.md)
  * [SNS](https://github.com/dowjones/servo-core/blob/release/OS/docs/SNS.md)
2. [`servo-gateway`](https://github.com/dowjones/servo-gateway/blob/release/OS/docs/README.md)
  * [DynamoDB](https://github.com/dowjones/servo-gateway/blob/release/OS/docs/DynamoDB.md)
  * [Github Deploy Keys](https://github.com/dowjones/servo-gateway/blob/release/OS/docs/Deploy.md)
  * [Config](https://github.com/dowjones/servo-gateway/blob/release/OS/docs/Config.md)
  * [HTTPS Certs](https://github.com/dowjones/servo-gateway/blob/release/OS/docs/Certs.md)
  * [Route53 Entry](https://github.com/dowjones/servo-gateway/blob/release/OS/docs/Route53.md)
3. [`servo-console`](https://github.com/dowjones/servo-console/tree/release/OS)
  * Just configure [`lib/constants`](https://github.com/dowjones/servo-console/tree/release/OS/lib/constants)
  * Its a static site. :)
