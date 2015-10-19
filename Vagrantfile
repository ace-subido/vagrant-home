require "yaml"

CONFIG = YAML.load_file(File.expand_path("../vagrant.yml", __FILE__))
VM_BOX = CONFIG["box_name"]
VM_IP_ADDRESS = CONFIG["ip"]
VM_MEMORY = CONFIG["memory"]
VM_CPU = CONFIG["cpus"]
INTERNAL_NETWORK = 'vboxnet0'

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.ssh.forward_agent = true
  config.vm.box = VM_BOX
  config.vm.synced_folder "./mnt", "/home/vagrant/src", nfs: true
  config.vm.network :private_network, ip: VM_IP_ADDRESS, virtualbox__inet: INTERNAL_NETWORK
  config.vm.network :public_network
  config.vm.hostname = CONFIG["host_name"]

  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", VM_MEMORY]
    v.customize ["modifyvm", :id, "--cpus", VM_CPU]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

end
