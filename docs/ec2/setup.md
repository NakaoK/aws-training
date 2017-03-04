# Environment

- OS: Windows 10
  - Console: Bash on Ubuntu on Windows
- Vagrant: 1.9.1
  - vagrant-aws: 0.7.2
  - dotenv: 2.2.0

# Precedure
## AWS

1. Create AWS account
1. Create IAM account for AWS
1. Get access key to IAM account
1. Set keypair to Amazon EC2
1. Create VPC & Subnet
1. Create Security Group with VPC to Amazon EC2

## Console

1. Install Vagrant  

    ```
    $ wget https://releases.hashicorp.com/vagrant/1.9.2/vagrant_1.9.2_x86_64.deb
    $ ls
    vagrant_1.9.2_x86_64.deb
    $ dpkg -i vagrant_1.9.2_x86_64.deb
    $ rm vagrant_1.9.2_x86_64.deb
    $ vagrant -v
    Vagrant 1.9.2
    ```
1. Install plugin  

    ```
    $ vagrant plugin install vagrant-aws 
    $ vagrant plugin install dotenv
    $ vagrant plugin list
    dotenv (2.2.0)
    vagrant-aws (0.7.2)
    ```
1. Download this repository  

    ```
    $ git clone https://github.com/nakao4532/aws-training.git
    $ ls
    aws-training
    ```
1. Create .env  

    ```
    $ cd aws-training
    $ vim .env
    AWS_ACCESS_KEY_ID='AKIXXXXXXXXXXXXXXXXX'
    AWS_SECRET_ACCESS_KEY='fXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
    AWS_SECURITY_GROUP='Your security ID'   # Security group cannnot set multi value
    AWS_SUBNET_ID='Your subnet ID'
    AWS_KEY_PAIR_NAME='Your key pair name'
    ```
1. Create instance to Amazon EC2  

    ```
    $ vagrant up
    ```

# Other

If you 
- connect instance ...  

    ```
    $ vagrant ssh
    ```
- check instance status ...  

    ```
    $ vagrant status
    ```
- shutdown instance ...  

    ```
    $ vagrant halt
    ```
- delete instance ...  

    ```
    $ vagrant destroy
    ```

