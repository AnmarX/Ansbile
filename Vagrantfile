require 'dotenv'
# vagrant plugin install dotenv



# ====== hyberv on win ==========#

#REMOVE Vm from terminal on win
#1- get-vm
#2- remove-vm "<Name of the vm>"

Vagrant.configure("2") do |config|
  # vm conroller ========================= #
  # config.vm.box = "gusztavvargadr/ubuntu-desktop-2204-lts"
  # config.vm.box_version = "2204.0.2409"
  config.vm.define "ansbile_controller" do |controller_config|
    controller_config.vm.hostname= "controller"
    controller_config.vm.box = "gusztavvargadr/ubuntu-desktop-2204-lts"

    config.vm.provider "hyperv" do |h|
      h.memory = 2048  # Set memory
      h.cpus = 2       # Set CPU count
      h.vmname  = "ansbile_controller"
      # h.vlan_id = 1
    end

    controller_config.vm.synced_folder ".", "/vagrant", type: "smb",
      smb_username: ENV['SMB_USERNAME'],
      smb_password: ENV['SMB_PASSWORD']

    controller_config.vm.provision "shell", path: "install_ansible.sh"
  end
  # vm conroller ========================= #




  # vm guest 1  ========================= #
  config.vm.define "ansbile_guest1" do |guest1_config|
    guest1_config.vm.box = "gusztavvargadr/ubuntu-server-2204-lts"
    guest1_config.vm.hostname= "guest1"


    guest1_config.vm.provider "hyperv" do |h|
      h.memory = 1024
      h.cpus = 1
      h.vmname = "guest1"
    end

    guest1_config.vm.synced_folder ".", "/vagrant", type: "smb",
      smb_username: ENV['SMB_USERNAME'],
      smb_password: ENV['SMB_PASSWORD']

    guest1_config.vm.provision "shell", path: "UpdateUpgrade.sh"
  end
  # vm guest 1 ========================= #



  # vm guest 2 ========================= #
  config.vm.define "ansbile_guest2" do |guest2_config|
    guest2_config.vm.box = "gusztavvargadr/ubuntu-server-2204-lts"
    guest2_config.vm.hostname= "guest2"


    guest2_config.vm.provider "hyperv" do |h|
      h.memory = 1024
      h.cpus = 1
      h.vmname = "guest2"
    end

    guest2_config.vm.synced_folder ".", "/vagrant", type: "smb",
      smb_username: ENV['SMB_USERNAME'],
      smb_password: ENV['SMB_PASSWORD']

    guest2_config.vm.provision "shell", path: "UpdateUpgrade.sh"
  end
  # vm guest 2 ========================= #

end
# ====== hyberv on win ==========#


# ====== vmware for mac ==========#
# 1- install 2.4.1 vagrant version
# 2- install this below:
# brew install --cask vagrant-vmware-utility
# vagrant plugin install vagrant-vmware-desktop

# Vagrant.configure("2") do |config|
#   # headless 
#   # config.vm.box = "gyptazy/ubuntu22.04-arm64"

#   # Desktop
#   config.vm.box = "gusztavvargadr/ubuntu-desktop-2204-lts"

#   config.vm.provider "vmware_desktop" do |v|
#     v.memory = 1024  
#     v.cpus = 1
#     v.gui=false
#     v.vmname  = "host"

#   end
  
# end
# ====== vmware for mac ==========#



  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessible to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

