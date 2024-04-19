Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.hostname = "VM-Arroyito"  # Nombre de la máquina virtual
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "VM-Arroyito"  # Nombre de la máquina virtual en VirtualBox
    vb.memory = "20000"  # Cambiar la memoria asignada a 20GB

    # Verificar si el controlador SATA ya existe
    if !vb.customizations['storagectl'].any? { |args| args.include?('--name') && args.include?('SATA Controller') }
      vb.customize ['storagectl', :id, '--name', 'SATA Controller', '--add', 'sata', '--controller', 'IntelAHCI']
    end
    
    # Adjuntar el CDROM al controlador SATA
    vb.customize ['storageattach', :id, '--storagectl', 'SATA Controller', '--port', 1, '--device', 0, '--type', 'dvddrive', '--medium', 'D:\Calilegua_MisProyectos\devops-2024-q2-a\practico-01\VBoxGuestAdditions.iso']
    
    # Habilitar el soporte de bidireccionalidad para copiar/pegar
    vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
  end
end
