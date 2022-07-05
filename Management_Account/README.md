Overview

The purpose of this customizations for Control Tower (CfCT) template is to build and manage an Amazon Machine Image (AMI) using Amazon Linux 2. The same template can be used for any allowed images by EC2 image builder (just replace the content of the image recipe), https://aws.amazon.com/image-builder/faqs/.

Steps to deploy

1. Update manifest.yaml with the name of management account as described in AWS Organizations. Also specify the region for deployment.
2. Update all defaults in the parameters folder. (Make sure your subnet and security group exists in the same VPC)
3. Zip up updated parameters, templates folders and manifest.yaml files as a single file called custom-control-tower-configuration.zip (deployment assumes you already setup CfCT and uses S3).

Items to Note

1. Before deployment, on the management account check that the role, "AWSControlTowerExecution" doesn't exist in IAM. If it does, remove the entire resource, "rAWSControlTowerExecutionRole" from the template file before proceeding.
2. Parameter, "pCustomer" is only used for tagging purposes.
3. Parameter, "pManagementAccountid" is the management account id for your Control Tower.
4. Obtain paramaters, "pOrganizationid" and "pOrganizationalUnitid" by visting the AWS Organizations for your AWS Control Tower/Management Account.
5. For distributing the created AMI, this pattern focuses on distributing to an Organizational Unit (OU) ONLY. You can also distribute to a target account or to the entire organization as desired. https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-imagebuilder-distributionconfiguration.html