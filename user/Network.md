# Network

Servo, by default, is a trust nothing environment. Nothing has access to your application unless you explicitly grant it access. This can be granted via the `Configure->Network Access` page within the console.
All rules use CIDR Ranges. [This Utility](http://www.ipaddressguide.com/cidr) can help with determining the appropriate range for your use. For example: if you only want to allow access from `1.2.3.4`, the corresponding CIDR range would be: `1.2.3.4/32`

### Ingress
Ingress rules are only allowed to be over port `80` & `443` and adding a rule adds access over both ports.

### Egress
Egress rules can be over any port. Remember to configure these if the app is connecting to any database, cache, etc. If no ports are specified `80` & `443` are added by default.

## Related
1. [User Documentation](README.md)
