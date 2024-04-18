Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "20000"  # Cambiar la memoria asignada a 20GB

    # Agregar un controlador IDE
    vb.customize ['storagectl', :id,
                  '--name', 'IDE Controller',
                  '--add', 'ide']

    # Agregar el CDROM al controlador IDE
    vb.customize ['storageattach', :id,
                  '--storagectl', 'IDE Controller',
                  '--port', 1,
                  '--device', 0,
                  '--type', 'dvddrive',
                  '--medium', '/path/to/VBoxGuestAdditions.iso']
  end
end


