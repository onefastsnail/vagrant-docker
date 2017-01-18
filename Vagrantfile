# Optimized for Vagrant 1.7 and above.
Vagrant.require_version ">= 1.7.0"

Vagrant.configure(2) do |config|

  #using a standard ubuntu image
  config.vm.box = "ubuntu/trusty64"

  #our sync protocol, 
  #vers=3 specifies version 3 of the NFS protocol to use
  #tcp specifies for the NFS mount to use the TCP protocol.
  #fsc will make NFS use FS-Cache
  #actimeo=2 absolute time for which file and directory entries are kept in the file-attribute cache after an update
  config.vm.synced_folder "./sites", "/vagrant", type: "nfs",  mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']

  #experimenting with an rsync option for peformance
  #config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: [".git/", "node_modules/", "data/"], rsync__auto: true

  #enable NAT hosts DNS resolver
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--ioapic", "on"]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  #pass on our current ssh agent to VM
  config.ssh.forward_agent = true

  #using the docker provisoner to add docker to VM
  config.vm.provision "docker"

  #lets use the ansible provisioner to add some things like WP CLI
  # config.vm.provision "ansible" do |ansible|
  #   ansible.verbose = "vv"
  #   ansible.playbook = "playbooks/vagrant.yml"
  # end

  #config.vm.network "forwarded_port", guest: 80, host: 8080

  #specify our VM IP
  config.vm.network "private_network", ip: "192.168.50.4"

end