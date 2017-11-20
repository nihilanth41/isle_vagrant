# NOTE: 
# you need to install a couple of vagrant plugins:
#
# vagrant plugin install vagrant-docker-compose
# 
# vagrant plugin install vagrant-gatling-rsync
# 
# vagrant plugin install vagrant-vbguest
Vagrant.configure(2) do |config|
 config.vm.box = "ubuntu/trusty64"

 # Configure VM options: here 1 GB of ram to prevent npm install Killed error
 config.vm.provider "virtualbox" do |v|
   v.memory = 1024
   v.cpus = 1
 end

 config.vm.network "forwarded_port", guest: 3000, host: 3000

 # If errors occur, try running “vagrant provision” manually
 # after “vagrant up”
 config.vm.provision :docker

 # compose_version needs to be 1.6.0 if you want to use docker-compose file version 2
 config.vm.provision :docker_compose, compose_version:"1.6.0", rebuild: "true", run: "always", yml: "/vagrant/docker-compose.yml"
end
