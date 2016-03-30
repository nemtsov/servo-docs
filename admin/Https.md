# Setting up HTTPS

The application should not concern itself over HTTPS negotiations and therefore is handled at the AWS level.

1. Locate the appropriate ELB
2. Add listener for 443 on the ELB to 443 on the instance.
  * Add a listener for 443 to 444 if all traffic should be redirected to 443.
3. Upload appropriate private key & certificate chain in PEM-encoded format with the password removed.
4. Enjoy the HTTPS site. :)

## Related
* [Admin Documentation](README.md)
