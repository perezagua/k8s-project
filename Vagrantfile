# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder ".", "/vagrant", disable: true
  config.vm.provider :virtualbox do |v|
    v.memory = 1024
    v.cpus = 1
    v.linked_clone = true
  end

  config.vm.define "master" do |m|
    m.vm.hostname = "master.example.com"
    m.vm.network "private_network", ip: "192.168.56.100", hostname: true
    m.vm.provider "virtualbox" do |v|
      v.name = "k8s-master"
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "worker1" do |w|
    w.vm.hostname = "worker1.example.com"
    w.vm.network "private_network", ip: "192.168.56.101", hostname: true
    w.vm.provider "virtualbox" do |v|
      v.name = "k8s-worker1"
    end    
  end

  config.vm.define "worker2" do |w|
    w.vm.hostname = "worker2.example.com"
    w.vm.network "private_network", ip: "192.168.56.102", hostname: true
    w.vm.provider "virtualbox" do |v|
      v.name = "k8s-worker2"
    end    
  end
end
