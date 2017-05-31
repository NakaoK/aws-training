# Environment

- OS: Windows 10 or Mac OS X
  - Windows 10 Console: Bash on Ubuntu on Windows
  - Mac OS X Console: zsh
- Vagrant: 1.9.5
  - vagrant-aws: 0.7.2
  - dotenv: 2.2.1

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
    - Windows 10
        
        ```
        $ wget https://releases.hashicorp.com/vagrant/1.9.5/vagrant_1.9.5_x86_64.deb
        $ ls
        vagrant_1.9.5_x86_64.deb
        $ dpkg -i vagrant_1.9.2_x86_64.deb
        $ rm vagrant_1.9.2_x86_64.deb
        $ vagrant -v
        Vagrant 1.9.5
        ```
    - Mac OS X
        1. Access Vagrant Download Page and Download vagrant_1.9.5_x86_64.dmg file  
            URL: https://www.vagrantup.com/downloads.html
        1. Execute vagrant_1.9.5_x86_64.dmg
1. Install libiconv(Mac Only)  

    ```
    $ brew tap homebrew/dupes
    $ brew install libxml2 libxslt libiconv
    $ brew link --force libxml2 libxslt libiconv
    ```
1. Install plugin  

    ```
    $ vagrant plugin install vagrant-aws 
    $ vagrant plugin install dotenv
    $ vagrant plugin list
    dotenv (2.2.1)
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
1. Download dummy box for Vagrant

    ```
    $ vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
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

