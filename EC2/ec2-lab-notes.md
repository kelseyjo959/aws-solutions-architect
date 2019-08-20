# EC2 Lab Notes

* Step 1: Choose Amazon Machine Image (AMI) - AWS 2 AMI for most of the course
* Step 2: Choose Instance Type
  * T2 Free Instance
* Step 3: Configure Instance Details
  * leave everything defaulted except `enable termination protection`
  * `advanced details` allows for bootstrap scripts
* Step 4: Add Storage
  * Only so many options are available for the first drop down under `Volume Type`
    * this is because it is the root instance volume
    * root can only launch on SSD or Magnetic Standard
    * add another Volume to get expanded Volume Types
    * root volume is where OS is going to be installed
* Step 5: Add Tags
  * helpful for keeping track of different EC2 instances and AWS web infrastructure
* Step 6: Configure Security Group (virtual firewall)
* Step 7: Review and Launch
  * need to set up key pair for asynchronous encryption
  * public and private key
  * store created keys in safe place
    * `CHMOD 400` + `filename`

## Accessing EC2 Instance

* `ssh ec2-user@` + IP addr + `-i` + filename
* `sudo su` to change permissions

* Chrome browser extension = Secure Shell App
  * chrome://apps
* `yum update -y`
* `yum install httpd -y` to get apache web server
* `cd /var/www/html` to add anything to web server
* create html file and start server with `service httpd start`
* `chkconfig on` makes sure service starts if server restarts

* **Status Systems Check** checks on the Hypervisor on physical machine

## Exam Tips

* **termination protection is turned off by default**
* default action for terminating an EC2 instance will also terminate the virtual hard drive
  * **root EBS volume will be deleted by default** 
  * root volume == operating system volume
* **EBS root volumes of Default AMI's cannot be encrypted, must be done by 3rd party**
  * **additional volumes add on top of the root can be encrypted**
