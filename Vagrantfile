Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian12"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "20000"  # 20 GBs de RAM
    vb.cpus = 8
  end

  config.vm.define "VM-Arroyito" do |vm|
    # Configuración de la VM
  end

  config.vm.provision "shell", inline: <<-SHELL
    export DEBIAN_FRONTEND=noninteractive
    export DEBIAN_PRIORITY=critical
  
    # Actualizar el sistema
    sudo apt-get update
    sudo apt-get upgrade -y

    # Instalar paquetes necesarios para las Guest Additions
    sudo apt-get install -y build-essential dkms linux-headers-$(uname -r)

    # Montar el ISO de las Guest Additions
    sudo mkdir -p /mnt/vbox
    sudo mount -o loop /tmp/VBoxGuestAdditions.iso /mnt/vbox

    # Instalar las Guest Additions
    sudo sh /mnt/vbox/VBoxLinuxAdditions.run

    # Desmontar el ISO
    sudo umount /mnt/vbox
    sudo rmdir /mnt/vbox

    # Instalar Postfix sin interacción
    sudo DEBIAN_FRONTEND=noninteractive apt-get install -y postfix

    # Limpieza de paquetes
    sudo apt-get autoremove -y
    sudo apt-get clean
  SHELL
end
