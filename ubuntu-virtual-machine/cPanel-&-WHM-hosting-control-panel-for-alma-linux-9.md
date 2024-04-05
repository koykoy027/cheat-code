# cPanel & WHM Hosting Control Panel for AlmaLinux 9

## Usage Instructions:

1. Launch the product after subscribing via AWS Marketplace
2. Navigate to the EC2 Console to find the newly launched instance
3. SSH into the instance with username ec2-user, and wait for the installation to finish
4. Assign an elastic IP address to the instance to set a permanent address for the server
5. `sudo /usr/local/cpanel/scripts/mainipcheck`
6. `sudo /usr/local/cpanel/scripts/ensure_hostname_resolves --yes`
7. `sudo passwd root` Set a root password
8. Access WHM by going to https://IPADDRESS:2087 with the root login and password you just created

[reference here](https://aws.amazon.com/marketplace/pp/prodview-hgvsqazbjp6sc?ref_=beagle&applicationId=AWS-EC2-Console#pdp-usage)
