# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.6.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Configure base box parameters
  config.vm.communicator = "winrm"
  config.vm.guest = "windows"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  #
  config.vm.provider "vmware_fusion" do |v, override|
    override.vm.box = "win2012r2-x64-vmwarefusion5-nocm"
    override.vm.box_url = "http://int-resources.ops.puppetlabs.net/vagrant/win2012r2-x64-vmwarefusion5-nocm.box"

    # Don't boot with headless mode
    v.gui = true
    v.cpus = 4
    v.memory = 4096
  end

  config.vm.provider "virtualbox" do |vb, override|
    override.vm.box = "win2012r2-x64-vbox4216-nocm"
    override.vm.box_url = "http://int-resources.ops.puppetlabs.net/vagrant/win2012r2-x64-vbox4216-nocm.box"

    # Don't boot with headless mode
    vb.gui = true
    vb.cpus = 4
    vb.memory = 4096
  end

  config.vm.provision "shell", path: "./win2012r2_bootstrap.ps1"
  config.vm.synced_folder "./", "/shared"
end
