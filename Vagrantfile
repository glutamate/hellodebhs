$script = <<SCRIPT

sed -i -e 's/us.archive.ubuntu.com/gb.archive.ubuntu.com/g' /etc/apt/sources.list

apt-get update

apt-get install -y build-essential libedit2 libgmp3-dev zlib1g-dev wget zile git haskell-platform

SCRIPT

Vagrant.configure("2") do |config|

  config.vm.box = "saucy-server-cloudimg-amd64-vagrant-disk1"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.synced_folder ".", "/home/vagrant/hellodebhs"

  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
  end
  config.vbguest.auto_update = true

  config.vm.provision "shell", inline: $script
end