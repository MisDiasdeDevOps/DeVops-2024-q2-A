# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Nombre de la máquina virtual
  ciudad = "cordoba"
  
  config.vm.define "vm-marcelo-A-#{ciudad}" do |vm|
    vm.vm.box = "debian/buster64"
    vm.vm.hostname = "vm-marcelo-A-#{ciudad}"
    
    # Configuración de VirtualBox
    vm.vm.provider "virtualbox" do |vb|
      vb.memory = "12000"
    end
  end
end
