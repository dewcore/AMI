Overview

The purpose of this template is to build and manage an Amazon Machine Image (AMI) using Amazon Linux 2. The same template can be used for any allowed images by EC2 image builder (just replace the content of the image recipe), https://aws.amazon.com/image-builder/faqs/.

Steps to deploy

1. Update ami_build_amazon_linux_2.yml with the parameters information. (These are customer name, subnet, security group and the Ids of the accounts that the AMI should be distributed to)
2. Update all defaults in the parameters folder. (Make sure your subnet and security group exists in the same VPC)

Items to Note

1. Before deployment, ensure that the AMI Administrator have the permissions to create a CloudFormation stack, run EC2 Image Builder as well as create the resources in the template.
2. Parameter, "pCustomer" is only used for tagging purposes.
3. For distributing the created AMI, this pattern focuses on distributing to specific AWS accounts ONLY. You can also distribute to an organization unit or to the entire organization as desired. https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-imagebuilder-distributionconfiguration.html