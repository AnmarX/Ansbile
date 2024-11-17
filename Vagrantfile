# require 'dotenv'
# vagrant plugin install dotenv



# ====== hyberv on win ==========#

#REMOVE Vm from terminal on win
#1- get-vm
#2- remove-vm "<Name of the vm>"


# config.vm.box = "gusztavvargadr/ubuntu-desktop-2204-lts"
# config.vm.box_version = "2204.0.2409"

Vagrant.configure("2") do |config|
  # Define the Ansible Controller VM
  config.vm.define "ansbile_controller" do |controller_config|
    # Set the hostname and box
    controller_config.vm.hostname = "controller"
    # controller_config.vm.box = "gusztavvargadr/ubuntu-server-2204-lts"
    controller_config.vm.box = "gusztavvargadr/ubuntu-desktop-2204-lts"

    # Configure Hyper-V provider-specific settings
    controller_config.vm.provider "hyperv" do |h|
      h.memory = 2048            # Set memory (in MB)
      h.cpus = 2                 # Set number of CPUs
      h.vmname = "ansbile_controller"  # Set VM name in Hyper-V
      # Uncomment and set if using VLANs
      # h.vlan_id = 1
    end


    controller_config.vm.synced_folder ".", "/vagrant", disabled: true
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

    guest1_config.vm.synced_folder ".", "/vagrant", disabled: true

    guest1_config.vm.provision "shell", path: "UpdateUpgrade.sh"
  end
  # # vm guest 1 ========================= #



  # # vm guest 2 ========================= #
  config.vm.define "ansbile_guest2" do |guest2_config|
    guest2_config.vm.box = "gusztavvargadr/ubuntu-server-2204-lts"
    guest2_config.vm.hostname= "guest2"


    guest2_config.vm.provider "hyperv" do |h|
      h.memory = 1024
      h.cpus = 1
      h.vmname = "guest2"
    end

    guest2_config.vm.synced_folder ".", "/vagrant", disabled: true

    guest2_config.vm.provision "shell", path: "UpdateUpgrade.sh"
  end
  # vm guest 2 ========================= #


end
# ====== hyberv on win ==========#





#===============================================================================================================






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



 