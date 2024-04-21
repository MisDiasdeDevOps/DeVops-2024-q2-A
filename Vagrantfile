Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.hostname = "VM-Arroyito"
  config.vm.boot_timeout = 120 # Aumenta el tiempo de espera de arranque a 120 segundos

  config.vm.provider "virtualbox" do |vb|
    vb.name = "VM-Arroyito"
    vb.memory = 20000

    # Intenta eliminar el controlador SATA existente
    vb.customize ["storagectl", "VM-Arroyito", "--name", "SATA Controller", "--remove"]

    # Agrega el controlador SATA
    vb.customize ["storagectl", "VM-Arroyito", "--name", "SATA Controller", "--add", "sata", "--controller", "IntelAHCI"] do |result|
      # Si el controlador se agregó correctamente, adjunta la unidad de DVD
      vb.customize ["storageattach", "VM-Arroyito", "--storagectl", "SATA Controller", "--port", "1", "--device", "0", "--type", "dvddrive", "--medium", "D:\\Calilegua_MisProyectos\\devops-2024-q2-a\\practico-01\\VBoxGuestAdditions.iso"]
    end

    vb.customize ["modifyvm", "VM-Arroyito", "--clipboard", "bidirectional"]
  end
end

