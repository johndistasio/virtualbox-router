# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  domain = 'orbitalarchives.org'
  config.vm.box = 'bento/centos-7.2'

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'playbook.yaml'
  end 

  config.vm.define 'host01' do |host|
    host.vm.hostname = "host01.#{domain}" 
    host.vm.network 'private_network',
        type: 'static',
        ip: '10.0.0.2',
        virtualbox__intnet: 'intnet'
  end

  config.vm.define 'host02' do |host|
    host.vm.hostname = "host02.#{domain}" 
    host.vm.network 'private_network',
        type: 'static',
        ip: '172.16.0.2',
        virtualbox__intnet: 'intnet'
  end

  config.vm.define 'router' do |host|
    host.vm.hostname = "router.#{domain}" 
    host.vm.network 'private_network',
        type: 'static',
        ip: '10.0.0.1',
        virtualbox__intnet: 'intnet'
    host.vm.network 'private_network',
        type: 'static',
        ip: '172.16.0.1',
        virtualbox__intnet: 'intnet'
  end
end
