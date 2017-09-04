# Description

This template uses Packer's inline [shell provisioner](https://www.packer.io/docs/provisioners/shell.html) to create an Amazon Linux machine image with Sumo Logic's collector built in.

The 3 components of Sumo Logic's collector are the [collector agent](https://help.sumologic.com/Send-Data/Installed-Collectors/04Install-a-Collector-on-Linux), the [sources.json](https://help.sumologic.com/Send-Data/Sources/03Use-JSON-to-Configure-Sources
) file that describes which log files to collect, and the [user.properties](https://help.sumologic.com/Send-Data/Installed-Collectors/05Reference-Information-for-Collector-Installation/06user.properties) config file which is created for you based on parameters in the command used to install the collector.

If you decide to build an image with a binary package (e.g. tarball), you will need to create the user.properties file manually.

# Instructions

After downloading Packer, use the command line to cd to the directory with the Packer+Sumo_Shell_Provisioner.json file that you've copied locally. To ensure Packer can access your AWS account resources, make sure you have an AWS authentication method to allow Terraform to control AWS resources:

- Option 1: User key pair
- Option 2: Set up the AWS CLI or SDKs in your local environment

I have chosen option 2 here so my Packer build command will not need AWS access key pair information. After completing the above steps:

1. Create a Sumo Logic free trial [here](https://www.sumologic.com/signup-free/?utm_medium=sales+email) if you don't already have an account
2. Generate a [Sumo Logic key pair](https://help.sumologic.com/Manage/Security/Access-Keys) inside you Sumo Logic account
3. Test and run the Packer template
- `/path/to/packer validate Packer+Sumo_Shell_Provisioner.json`
- ```/path/to/packer build Packer+Sumo_Shell_Provisioner.json
\ -var 'sumo_access_id=<sumo_access_id>' 
\ -var -sumo_access_key=<sumo_access_key>'```
