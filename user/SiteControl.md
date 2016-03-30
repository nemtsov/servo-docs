# SiteControl [WIP]

SiteControl is a feature built within Servo, however it is not directly related to an app/stack. It allows you to create DNS based load balanced endpoints which take client location, origin health, custom weights and failover rules into consideration. Changes take approximately 1 minute to take effect. Distributions are global and can be managed through any Servo region.

**Distribution**: A top level Route53 entry that points to another internal Route 53 entry of an `origin`

**Origin**: A Route53 entry that is a CNAME entry to a particular endpoint. It has the following properties:

* Region
* Weight
* HealthCheck
  * Type of healthcheck to determine the health of an origin
* Failover

## Related
1. [User Documentation](README.md)
