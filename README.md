# cf-MultiAZ-AutoScaling-NGINX-ServerInfo
____________________
# Purpose
Cloud formation template to create Multi AZ, Auto scaled, Nginx web server group. 
Customer Directly hits to the DNS of ELB, and request can be routed to any of the attached instances and returnes default HTML page that shows the Instance's meta data. It also sets serevers behind the autoscaling group to scale in and scale out depending on CPU usage. It setup minimum 3 instanse in different Availability Zone to maximum 9 instances. It Scale-out if CPU > 90% for 10 minutes & Scale-in if CPU < 70% for 10 minutes. It uses ELB helth check to mark instance helthy, if not to mark it as unhealthy and add new add healthy instance. 
_____________________
***Warning :*** Resources created using this cloud formation tamplete might incure charges.  

***Resources Created:***
- Instances: minimum 3 in diffrent Availability zones
- Auto Scaling Group: 
- WebServer Group: Web server group of minimum 3 max 9
- Launch Config: Launch configuraion is created according to the parameter   selected during stack creation.
- Elastic Load Balancer: Classic Elastic Load Balancer.
- Shell Script: Shell Script to install Nginx
- Security Group: Two Security group, One  for Elastic load balancer and one for Instance group (web server group).

___________________________

# Walkthrough

**Prerequisites: AWS Account with Defualt VPC\* and Key Pair\*\***
*If default VPC is not there please contact the AWS support to retrive the Default VPC.
**To create key-pair please follow this tutorial: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair

- **Step 1:** Login to AWS account
    https://console.aws.amazon.com/console/home
- **Step 2:** Navigate to CloudFormation Service.
   ![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/1_Select_CloudFormation.png)
- **Step 3:**Click on Create new Stack button.
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/2_Create_New_Stack.png)
- **Step 4:** You can choose donwloaded cloudformation template or you can Spacify this S3 url : https://s3-us-west-2.amazonaws.com/cf-images-multiaz/cf-MultiAZ-AutoScaling-Nginx
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/3_Select_template.png)
- **Step 5:** Enter the Stack name, Instance type needed, Existing Key pair and IP where you want to allow SSH. 
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/4_parameters.png)
- **Step 6:** These are the options that you can spesify for rollback action and CPU alarm notification.
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/5_options.png)
- **Step 7:** Review all the settings and hit create.
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/6_Review.png)
- **Step 8:** In events tab you can monitor the progress of the stack creation or any errors. 
 ***In occurrence of any error default action is to rollback stack***
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/7_stack_creation_progress.png)
- **Step 9:** Go to the outputs tab to select the ELB URL.
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/8_stack_complete.png)
- **Step 10:** It will redirect to one of the instance and shows diffrant server details on refresh.
![alt text](https://s3-us-west-2.amazonaws.com/cf-images-multiaz/9_ServerDetails.png)


***Be updated, Stay upgraded.***

Thankyou!!!
