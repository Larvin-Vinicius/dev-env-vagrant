Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "dev-env"
  config.vm.define "dev-env"
  config.vagrant.plugins = ['vagrant-vbguest']

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder "./", "/home/vagrant/project"

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 4
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
    sudo apt install -y ca-certificates gnupg curl git cmake tmux vim lsb-release 
    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt update
    sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
  SHELL
end
