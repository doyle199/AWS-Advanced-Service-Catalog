# AWS-Advanced-Service-Catalog
AWS Advanced Service Catalog

Make sure the admin users have the correct permissions for AWS Service catalog. Download the following template, which launches a single Linux instance configured for SSH access: https://awsdocs.s3.amazonaws.com/servicecatalog/development-environment.template. Create a key pair if one hasn’t already. Navigate to the AWS Service Catalog console. Click on portfolios in the left menu then create portfolio.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/create_portfolio.png)

Enter a portfolio name, description, and owner and click create.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/portfolio1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/portfolio_success.png)

To create a cloud development environment that runs on Amazon Linux, open the portfolio just created. Click on upload new product.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/profile_details.png)

In the product details section, enter a product name, description, and owner. In the version details section, select use a template file, upload the template that was downloaded before, enter a version number and a description. In the support details section, enter a contact email, support link, and support description, Click Review. On the review page, click create.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/product_details_2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/version.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/support.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/success.png)

Add a template constraint to the Linux desktop product that limit instance size for users at launch time. In the portfolio just created click on the constraints tab and click create constraint.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/create_constrant.png)

For the product dropdown select Linux Desktop. For the constraint type select template. For the template constraint select text editor and enter the following JSON: https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/template1.jscsrc. Enter a constraint description and click create.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/contraint2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/contraint3.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/constraint4.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/constraint5.png)

Add a launch constraint to assign an IAM role. Without a launch constraint one would need to give additional permissions to users to use the Linux Desktop product. To add a launch constraint, navigate to the IAM console. Click policies in the left menu, then create policy.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/policy1.png)

Click the JSON tab and paste the following JSON replacing what is there and click review policy: https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/template2.jscsrc

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/JSON1.png)

Name the policy LinuxDesktopPolicy, create a description, and click create policy.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/create2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/created.png)

Click roles in the left menu then create role.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/create_role1.png)

Select AWS service then Service Catalog and click Next: permissions.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/AWS_Service.png)

Search for LinuxDesktopPolicy, check the box for it, and click next tags then next review. Name the role LinuxDesktopLaunchRole and click create role.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/desktop_role.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/created2.png)

Navigate back to the Service Catalog console, go into the portfolio created before and click the constraints tab and click create constraint. For the product choose Linux Desktop. For the constraint type select launch. For the launch constraint choose select IAM role and choose the LinuxDesktopLaunchRole and click create.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/launch1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/launch2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/launch3.png)

To grant end users access to the portfolio, Create a group for the users, navigate to the IAM console and click groups in the left menu then create new group.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/create_new_group.png)

Name the group endusers and click next step.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/endusers.png)

Search for AWSServiceCatalog and check the box for AWSServiceCatalogEndUserFullAccess and click next step.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/attach_policy!.png)

Review and click create group.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/review_group.png)

Select users in the left menu and click add user.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Add_user.png)

Create a username. Check the box for AWS Management Console access, check the custom password box and create a password, uncheck require password change, click next: permissions.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/access_type.png)

Select add user to a group, check the box for the Endusers group, click Next: tags. Click next: review, click create user.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/user_success.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Add_User_To_Group.png)

Back in the portfolio, select the groups, roles, and users tab and click add groups, role, users.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/port2.png)

In the groups tab, check the box for the Endusers group and click add access.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/add_access!.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/add_access_2.png)

To verify that the user can access the end user console log into AWS as the user and perform the following steps. Navigate to the service catalog console and select Linux Desktop product.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/SC_!.png)

Click Launch Product.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/launch_product_1.png)

Enter Linux-Desktop as the name, select the v1.0 and click next. 

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/version_1.png)

Choose a server size, keypair, CIDR range and click next.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/params.png)

Click next, next, and then launch.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Launch_3.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/internal.png)

Use AWS Service Catalog to build a custom catalog of AMIs from AWS Marketplace. Revoke AWS Marketplace permissions and grant AWS Service Catalog permissions to one’s catalog users. As the Admin, navigate to service catalog, click on polices in the left menu and click create policy.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/create_policy_3.png)

Click the JSON tab and paste the following JSON, replacing what’s there: https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/template3.jscsrc Click review policy. 

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/review_policy_2.png)

Give the policy a name and description and click create policy.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/deny_1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/deny2.png)

Click on groups in the left menu, go in the Endusers group, click on the permissions tab, click on attach policy.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Attach_4.png)

Search for the policy, check the box next to it and click attach policy. Make sure the group had the AWSServiceCatalogEndUserFullAccess policy as well.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Deny_Outside_AMI.png)

Subscribe to AWS Marketplace AMI product you want to distribute. Navigate to the AWS Marketplace console, search for the product one wishes to use and click on it.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/AMI1.png)

Select continue to subscribe.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/sub!.png)

Click continue to configuration.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/continue_to.png)

Click continue to launch.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/continue_to_launch.png)

For the choose action, select copy to Service Catalog. Make sure the correct region is selected and click copy to Service Catalog. 

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Config2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/copy.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/copied.png)

Create a portfolio like before or use an existing to distribute the product to one’s users. In the portfolio add the service to the portfolio.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/portfolio2.png)

In IAM, Create a policy for a launch constraint with the following JSON like before: https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/template4.jscsrc

Create a role, select, AWS service and Service Catalog, select the policy just created continue through as before.	In Service Catalog, click on the portfolio, click on the constraints tab and click on create constraint and add the new policy like before.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/contraint3.png)

Add the users group.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Endusers_2.png)

Log in as the user and test deployment.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/products_list.png)

The parameters ask for more information with this setup.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/params_2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/params_3.png)

Create an approval flow for an AWS Service Catalog product launch using AWS Lambda, AWS CloudFormation, Amazon API Gateway, and AWS Service Catalog administrator. Download the following template: https://s3.amazonaws.com/service-catalog-approval-flow/v1/resources_for_approval_template.yaml. The template will create an SNS topic, SNS notification function, and approval function, API Gateway, API and IAM roles. Run the template in AWS CloudFormation, go through the steps, check the acknowledgement box and click create stack. Enter an email for notification. Click on the outputs tab and copy the Lambda ARN. 

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/stack_complete_2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/sub_con_1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/sub_con_1.png)

•	Download the following template: https://s3.amazonaws.com/service-catalog-approval-flow/v1/sample_wordpress_for_approval_template.yaml. Open the template in an editor and past the Lambda ARN where it says “replace your lambda ARN” next to ServiceToken: on line 395.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/yaml_1.png)

Save the template. Run the template in CloudFormation, it has a wait condition for approval status.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/details_1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/details_2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/wait_condition_1.png)

The stack sent an approval notification to the email. Click the link to approve.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/app_email.png)

It will say successfully approved in the web browser. Then the stack resumes creation because the Lambda function sends a confirmation for WaitHandle to continue.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Wait_complete.png)

Next, To use AWS Service Catalog for Code Deployments, enable CloudTrail and AWS Config, navigate to the AWS CloudTrail console, click on create a trail. Enter a trail name, check the box for enable for all accounts, create and AWS KMS alias name, enable CloudWatch Logs, make a role name, click next.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/trail_att_1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Trail_att_2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Trail_att_3.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/Trail_att_4.png)

Choose an event type, click next, click create trail.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/event1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/event2.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/event3.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/event4.png)

Navigate to AWS Config console, click get started. On step 1: settings, leave the defaults and click next.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/set1.png)

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/set2.png)

Choose any rules one wants and click next then click create.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/dash1.png)

Navigate to IAM and create a group called HealthcareDeveloper and attach the policy AWSCodeCommitPowerUser and the AWSServiceCatalogEndUserFullAccess, this group will not be able to delete projects. Also Add users.

![alt text](https://github.com/doyle199/AWS-Advanced-Service-Catalog/blob/master/group%40.png)

Navigate to the Service Catalog console, create a new portfolio. Go into the portfolio and click on upload new product.









