# ansible-playbooks
This is a repository for ansible playbooks

after setting up vpc and security group

security-group
alb security group
port = 80 and 443  source = 0.0.0.0/0

bastion security group
port =22 source = your ip address

ansible security group
port = 22  source bastion security group


webserver security group
port = 80 and 443 source = alb security group
port = 22 source = ansible server security group


Note

create bastion host on amazon linux 
attached to public sub az1
security bastion-host sg


create webserver az1 and 2 amazon linux keypair ansiblekey
connect to private app subnetaz1 and az2 
security-webserver sg



ansible server ami created ansible key pair

inventory
change the ip to private ip for the webserver az1 and az2

connect to bastion host through putty
connect webserver to ubuntu and update the webservers 
 ssh ubuntu@10.0.2.162
 ssh ec2-user@webservr private ip

sudo yum update -y
sudo yum -y install python-pip
sudo pip install boto3


cd ansible-playbook

git pull 


command to ping your webservers
ansible all --key-file ~/.ssh/id_rsa -i inventory -m ping -u ec2-user

ansible all -m ping




cmd to deploy jupiter site

ansible-playbook deploy-jupiter-website.yml


create alb for ansible server
attached route-53 to your alb
attached cm to alb for ssl connection secure