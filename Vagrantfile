MACHINES={
 :"pam" => {
              :box_name => "ubuntu/jammy64",
              :cpus => 2,
              :memory => 1024,
              :ip => "192.168.57.10",
            }
}

Vagrant.configure("2") do |config|
  MACHINES.each do |boxname, boxconfig|
    config.vm.synced_folder ".", "/vagrant", disabled: true
    config.vm.network "private_network", ip: boxconfig[:ip]
    config.vm.define boxname do |box|
      box.vm.box = boxconfig[:box_name]
      box.vm.box_version = boxconfig[:box_version]
      box.vm.host_name = boxname.to_s

      box.vm.provider "virtualbox" do |v|
        v.memory = boxconfig[:memory]
        v.cpus = boxconfig[:cpus]
      end
      config.vm.provision "shell", inline: <<-SHELL
	  sudo mkhomedir_helper otusadm
	  sudo mkhomedir_helper otus
	  echo "PasswordAuthentication yes" | sudo tee /etc/ssh/sshd_config.d/01-auth.conf         
	  systemctl restart sshd.service

	  sudo chsh -s /bin/bash otusadm
          sudo chsh -s /bin/bash otus

      SHELL
    end
  end
end
