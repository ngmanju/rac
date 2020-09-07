# aws-cloudformation-HelloWorldWebsite

1.1 OBJECTIVE

Launch a simple web site in a load balanced and highly available manner utilizing automation
and AWS bestpractices.


1.2 REQUIREMENTS
- VPC withprivate/public subnets andall requireddependentinfrastructure (DO NOT USE THE
DEFAULT VPC)
- ELB to be used to register web server instances
o Include a simple health check to make sure the web servers are responding
o The health check should automatically replace instances if they are unhealthy, and the
instances should come back into service on their own
- Auto Scaling Group and Launch Configuration that launches EC2 instances and registers them
to the ELB
o Establish a minimum, maximum, and desired server countthat scales up/downbased on
a metric of your choice (and be able to demonstrate a scaling event)
- Security Group allowing HTTP traffic to load balancer from anywhere (not directly to the
instance(s))
- Security Group allowing only HTTP traffic from the load balancer to the instance(s)
- Remote management ports such as SSH and RDP must not be open to the world
- Some kind of automation or scripting that achieves the following:
o Install a web server (your choice – Apache and Nginx are common examples)
o Deploys a simple “hello world” page for the web server to serve up
o Can be written in the language of your choice (HTML, PHP, etc)
o Can be sourced from the location of your choice (S3, cookbook file/ template, etc)
o Must include the server’s hostname in the “hello world” presented to the user
- All AWS resources must be created using Terraform or CloudFormation
- No resources may be created or managed by hand other than EC2 SSH keys

1.3 SOLUTION
- Review code in each CloudFormation YAML file
 o [webapp.yaml, vpc.yaml ]
- Review code in each CloudFormation Bash script
[ vpc.sh, webapp.sh, testScaleUpPolicy.sh, testScaleDownPolicy.sh ]
- Run each Bash script in the following succession
vpc.sh → webapp.sh → testScaleUpPolicy.sh → testScaleDownPolicy.sh
- After each Bash script is run, review the results in the CloudFormation console, and in each respective console, i.e. EC2, ELB, etc.
- Delete each CloudFormation stack via the console
