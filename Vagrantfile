Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.hostname = "VM-Arroyito"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "VM-Arroyito"
    
    unless vb.customizations["storagectl"].any? { |args| args.include?("--name") && args.include?("SATA Controller") }
      vb.customize ["storagectl", :id, "--name", "SATA Controller", "--add", "sata", "--controller", "IntelAHCI"]
    end

    vb.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", "1", "--device", "0", "--type", "dvddrive", "--medium", "D:\\Calilegua_MisProyectos\\devops-2024-q2-a\\practico-01\\VBoxGuestAdditions.iso"]
    vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
  end
end





