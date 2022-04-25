# Updating Let's Encrypt Certification

Our RStudio server is also covered by an SSL certificate from Let's Encrypt, and occasionally we'll need to renew this certificate (an email will be sent out when the certificate is about to expire). This requires a few simple steps.

1. First, you need to start the RStudio EC2 instance:
  * Get into AWS – see instructions at  https://github.com/arcus/intro-to-r-for-clinicians-chop/blob/master/server_setup/README.md
  * Go to AWSAdministratorAccessManagement console
  * **Start** (don't launch) the EC2 instance of the RStudio server


2. Find your private key (one for use by Arcus Education is stored in Vault).

3. ssh into the VM using its IP address (which you can find on the EC2 instance info page) and this command (also from aforementioned server setup readme):
  `ssh -i path/to/rsp-train.pem ubuntu@<your_server>`
  (substitute <your_server> for either the public IPv4 address or the domain name of the server and including the path to your downloaded key)

4. Once you're in the VM, run the following command (from https://docs.digitalocean.com/support/how-can-i-renew-lets-encrypt-certificates/):

  `sudo certbot renew`

5. **Stop** (don't terminate) the EC2 instance.
