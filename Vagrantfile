Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "20000"  # Cambiar la memoria asignada a 20GB

    # Agregar el CDROM al controlador IDE existente
    vb.customize ['storageattach', :id,
                  '--storagectl', 'IDE Controller',
                  '--port', 1,
                  '--device', 0,
                  '--type', 'dvddrive',
                  '--medium', 'D:\Calilegua_MisProyectos\devops-2024-q2-a\practico-01\VBoxGuestAdditions.iso']
  end
end

# D:\Calilegua_MisProyectos\devops-2024-q2-a\practico-01