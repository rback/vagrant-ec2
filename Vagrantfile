Vagrant.configure("2") do |config|
  config.vm.synced_folder "chef", "/vagrant"

  config.vm.define :vbox do |vbox_config|
    vbox_config.vm.box = "precise64"
    vbox_config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    vbox_config.vm.provider :aws
  end

  config.vm.define :aws do |aws_config|
    aws_config.vm.box = "precise64"
    aws_config.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"
    aws_config.vm.provider :aws do |aws, override|
      aws.keypair_name = "vagrant"
      aws.ami = "ami-ce7b6fba"
      aws.region = "eu-west-1"
      aws.instance_type = "t1.micro"
      aws.security_groups = ["vagrant"]

      override.ssh.username = "ubuntu"
      override.ssh.private_key_path = "./vagrant.pem"
    end
  end
end