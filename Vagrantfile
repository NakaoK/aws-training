Dotenv.load

Vagrant.configure("2") do |config|
  # Vagrant Box
  config.vm.box = "dummy"

  # Rsync Directory
  config.vm.synced_folder "setup", "/vagrant", type: "rsync"

  # Ansible
  config.vm.provision "ansible_local" do |ansible|
    #ansible.playbook = "provision/common/docker.yml"
    ansible.playbook = "provision/master.yml"
  end

  # AWS
  config.vm.provider :aws do |aws, override|
    # AWS Account
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']

    # Instance Configuration
    aws.tags = {
      'Name' => 'DevelopEnvironment',
      'Description' => 'Deploy Ethereum Demo, GitLab, Jenkins, Docker, ...etc'
    }
    aws.instance_type = "t2.micro"
    aws.ami = "ami-c68fc7a1"
    aws.region = "ap-northeast-1"
    aws.availability_zone = "ap-northeast-1c"
    aws.security_groups = ENV['AWS_SECURITY_GROUP']
    aws.elastic_ip = true
    aws.associate_public_ip = true
    aws.subnet_id = ENV['AWS_SUBNET_ID']

    # Login Configuration
    aws.keypair_name = ENV['AWS_KEY_PAIR_NAME']
    override.ssh.username = "ubuntu"
    override.ssh.private_key_path = "~/.ssh/default.pem"

    # SSH accessable
    aws.user_data = "sed -i -e 's/^\\(Defaults.*requiretty\\)/#\\1/' /etc/sudoers"

  end
end

