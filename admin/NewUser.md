# Adding a new user

Adding a new user is currently a manual process but something that can definitely be automated.

1. Open the users DynamoDB table and click `Create Item`.
2. The  `username` field should be empty since it is specified as the *hashkey*, so fill it with the users email address
3. Add the field `name` with the full name of the user.
4. Run the `scripts/passwordGenerator.js` script in the `servo-gateway` repository. Note the un-hashed password.
5. Add the field `password` with the hashed password generated in the previous step.
6. Open the permissions table in DynamoDB and click `Create Item`.
7. The `username` and `context` field already exist and be empty.
8. Fill `username` with the email address of the user.
9. Fill `context` with the organization you would like to give the user access to.
10. Add the field `userrole` with the value `user`, `member`, or `owner`.
11. Email the user with their un-hashed password from step 4.


## Related
* [Admin Documentation](README.md)
