# mediawiki
Setup 2 aws instances one for webserver and 2nd for mysql.
Done with Ansible playbook to setup Webserver where apache and application is running.
In other instance Mysql database is running.
In Ansible hosts file we mention the IP of websever and myssql
[test-1]
Web server IP
[test-2]
Mysql server IP
Run the master playbook from where both playbooks call.
For Autoscaling for same application;
Step:1 Create AMI of webserver 
Step:2 Create AWs ELB where webserver is under elb handling the request
Step:3 Create Auto Scaling Group where We setup If CPU is Greater than 60 then autoscale the application.
Step:4 We provide the desired MIN and MAX server
Step:5 In route53 We create the Hosted zone then point to vinamratest.com to ELB Endpoint.

For Deployment for same application;
Step:1 Setup Jenkins Jobs for deployment
Step:2 Job take the Parametes As tag or branch 
Step:3 Then By help of jenkins We take the git checkout branchname 
Step:4 Put Latest code to S3
Step:5 Ssh to given Webserver download the latest code
Step:6 Reload Apache ( Optional for PHP APPlication ).

Here I am using the Terraform to Create the EC2 Instances for webserver and mysql server then Run the desired Ansible playbook.
