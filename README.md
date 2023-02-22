# Data-Infrastructure-Setup-IAC

Set up data infrastructure
We will set up the data infra locally  and run the required data components with docker-based containers and 
run the required data components in our local machine using docker-based containers.

 Manage cloud infrastructure with code
While we can create, & manage cloud services with custom code, UI, etc., Having the infrastructure defined as code is beneficial. Infrastructure as code (IAC) allows you to store the configuration on version control and easily spin up or bring down services. We can recover quickly in case of accidental deletions. We will use AWS for our projects.

We will use Terraform as our IAC framework (others are Pulumi, etc.). Our terraform folder has 3 files

###main.tf 
defines all the services we need. In our main.tf , we create an EC2 instance, its security group where we configure access and a cost alert. Note that in the EC2, we run a script with user_data; this is a script run at EC2 initialization time (cloud-init ). Note that we can define our services in multiple files, like s3.tf, emr.tf, etc., if we choose to.

###variable.tf 
These are  variables that can be provided as inputs when spinning up the infrastructure. The main.tf file uses the variables defined in the variable.tf with var.variable_name.

###output.tf
output.tf defines all the configurations we want to print out when we use the command terraform output. We have described the ec2 public DNS, private and public keys in our output.tf. We will later use the private key to connect to our EC2 instance.
