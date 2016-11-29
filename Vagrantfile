Vagrant.configure(2) do |config|
  ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
  config.vm.box = "xenial"
  config.vm.box_url = "https://share.phys.ethz.ch/~isg/vagrant/xenial64.box"

  config.vm.define 'bang-dev', primary: true do |host|
    config.vm.hostname = "bang-dev"

     config.vm.network "private_network", ip: "192.168.13.100"

    config.vm.provider :virtualbox do |vb|
      vb.customize [ "modifyvm", :id, "--nictype1", "virtio" ]
      vb.memory = 256
      vb.cpus = 1
    end
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo DEBIAN_FRONTEND=noninteractive apt-get update
    sudo DEBIAN_FRONTEND=noninteractive apt-get -y upgrade
    sudo DEBIAN_FRONTEND=noninteractive apt-get install -y python
  SHELL


  config.vm.provision "ansible" do |ansible|
    ansible.groups = {
      "bang" => [ "bang-dev" ],
      "bangweb" => [ "bang-dev" ],
      "bangweb-vagrant" => [ "bang-dev" ],
    }
    ansible.sudo = true
    ansible.playbook = "./site.yml"
#    ansible.verbose = "vvv"
  end
end
# vi: set ft=ruby nofoldenable:
