Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  
  # Configuración específica del proveedor para VirtualBox
  config.vm.provider "virtualbox" do |vb|
    # Mostrar la GUI de VirtualBox al arrancar la máquina
    vb.gui = true
    
    # Personalizar la cantidad de memoria en la VM: 20 GB
    vb.memory = "20000"
    
    # Configurar el número de CPUs a 8
    vb.cpus = 8
    
    # Agregar 64 MB de VRAM
    vb.customize ["modifyvm", :id, "--vram", "64"]
    
    # Establecer el nombre de la VM
    vb.name = "VM-Arroyito"
  end
  
  # Crear un mapeo de puerto reenviado que permite acceder a un puerto específico
  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  
  # Crear una red privada, que permite el acceso solo desde el host a la máquina
  config.vm.network "private_network", ip: "192.168.33.10"
  
  # Deshabilitar el directorio compartido predeterminado del directorio de código actual
  config.vm.synced_folder ".", "/vagrant", disabled: true
  
  # Establecer el nombre de la VM como "vm-Arroyito"
  config.vm.define "vm-Arroyito"
end
