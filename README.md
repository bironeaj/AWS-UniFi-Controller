
# AWS UniFi Controller CloudFormation Template
This CloudFormation template was designed for new and experienced AWS users to launch a UniFi controller with minimal effort. 

##  What this template does for you

 - Creates a VPC and public subnet for your controller
 - Allocates an EIP for your controller
 - Launches an EC2 instance with the required firewall rules
 - Installs MongoDB and UniFi Controller.
 - Can ~~optionally~~ setup Let's Encrypt and import the SSL certs in to UniFi automatically ([thanks to Steve Jenkins](https://github.com/stevejenkins/unifi-linux-utils)).

## **Warning:** Work In Progress
This template is still a work in progress. **As of now, Let's Encrypt is being setup whether or not you select Yes/No on the parameter page. This requires you to update your DNS A record as soon as the template launches for Let's Encrypt to successfully run. Set your TTL on the DNS record to 1 minute or the minimum time so that it will update and propagate faster. I am currently researching how I can enable/disable this conditionally.** If you have any issues running this template, please post the errors on the GitHub Issues page.

## How to Use
For these instructions, I will assume you have signed up for a free AWS account and are logged in to the AWS console.

 1. Download the UniFi-Controller.yaml file from this repo.
 2. From the AWS console, navigate to Services > CloudFormation.
 3. Click "Create Stack".
 4. Select the Upload File option and choose the UniFi-Controller.yaml file you previously downloaded. Click Next.
 5. Enter a Stack Name (just for your future reference) and fill out all the parameters. [**Note: The t2.micro instance type is available for free tier.**](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=categories#featured) Click Next.
 6. On the Stack Options page, click next. Then, click Create Stack.
 7. At this point, you should click on the Resources tab for your stack. Shortly after the template begins creating the resources, you will see an EIP listed. You will need to create a DNS A record for the FQDN that points to this IP address.
 8. You should now be able to navigate to https://<FQDN>:8443 and setup your UniFi Controller.

## Credits
Thanks to the following sources! These were referenced/used in creating this template.

 - [Crosstalk Solutions - Definitive Guide to Hosted UniFi](https://crosstalksolutions.com/definitive-guide-to-hosted-unifi/)
 - [Steve Jenkins - unifi-linux-utils](https://github.com/stevejenkins/unifi-linux-utils)
