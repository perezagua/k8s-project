NUM_WORKER_NODES=2
IP_NW="172.31.0."
IP_START=100

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "yum -y update"

  config.vm.box = "geerlingguy/centos7"
  config.vm.box_check_update = true

  config.vm.define "master" do |master|
    master.vm.hostname = "master-node"
    master.vm.network "private_network", ip: IP_NW + "#{IP_START}"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = 4048
      vb.cpus = 2
    end
  end

  (1..NUM_WORKER_NODES).each do |i|
    config.vm.define "node0#{i}" do |node|
      node.vm.hostname = "worker-node0#{i}"
      node.vm.network "private_network", ip: IP_NW + "#{IP_START + i}"
      node.vm.provider "virtualbox" do |vb|
        vb.memory = 2048
        vb.cpus = 1
      end
    end
  end
end