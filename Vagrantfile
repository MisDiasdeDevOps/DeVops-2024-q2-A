Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "20000"  # 20 GBs de RAM
    vb.cpus = 8
  end

  config.vm.define "VM-Arroyito" do |vm|
    # Configuración de la VM
    vm.vm.box = "debian/bookworm64"

    vm.vm.provider "virtualbox" do |vb|
      vb.memory = "20000"  # 20 GBs de RAM
      vb.cpus = 8
    end

    vm.vm.provision "shell", inline: <<-SHELL
      export DEBIAN_FRONTEND=noninteractive
      export DEBIAN_PRIORITY=critical
    
      # Actualizar el sistema
      sudo apt-get update
      sudo apt-get upgrade -y

      # Instalar paquetes necesarios para las Guest Additions
      sudo apt-get install -y build-essential dkms linux-headers-$(uname -r)

      # Montar el ISO de las Guest Additions
      sudo mkdir -p /mnt/vbox
      sudo mount -o loop "/mnt/d/Calilegua_MisProyectos/devops-2024-q2-a/practico-01/VBoxGuestAdditions.iso" /mnt/vbox

      # Descomprimir las Guest Additions (usando gzip en lugar de zstd)
      sudo tar xzf /mnt/vbox/VBoxLinuxAdditions.run --no-same-owner -C /tmp

      # Instalar las Guest Additions
      sudo sh /tmp/VBoxLinuxAdditions.run

      # Recargar módulos y servicios de VirtualBox Guest Additions
      sudo /sbin/rcvboxadd reload

      # Desmontar el ISO
      sudo umount /mnt/vbox
      sudo rmdir /mnt/vbox

      # Limpieza de paquetes
      sudo apt-get autoremove -y
      sudo apt-get clean

      # Actualizar el initramfs
      sudo update-initramfs -u

      # Reiniciar para aplicar los cambios
      sudo reboot
    SHELL
  end
end

