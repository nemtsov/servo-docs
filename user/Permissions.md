# Permissions

All aspects of the PaaS are tied together with permissions. A user will inherit the highest permission level they have for parent contexts, unless it is explicitly specified at the desired context. For example: an app owner will inherit the `owner` permission for all stacks created within the app.

Here are the 3 levels of permissions from lowest to highest, where resources are defined to be any of following: app/stack/distribution/origin

1. `user`
  * Can retrieve existing resources
  * Can create new resources
2. `member`
  * Has all the permissions of `user`
  * Can modify existing resources
3. `owner`
  * Has all the permissions of `member`
  * Can delete existing resources
  * Can grant permissions to other users.


## Related
1. [User Documentation](README.md)
2. [Network Access](Network.md)
