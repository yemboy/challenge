# -*- mode: ruby -*-
# vi: ft=ruby :

#
#

require 'rbconfig'
require 'yaml'

DEFAULT_BASE_BOX = "bento/ubuntu-16.04"
cpuCap = 10																		# Limit to 10% of the cpu
inventory = YAML.load_file("inventory.yml")		# Get the names & ip addresses for the guest hosts
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vbguest.auto_update = false
  inventory.each do |group, groupHosts|
		next if (group == "justLocal")
  	groupHosts['hosts'].each do |hostName, hostInfo|
    	config.vm.define hostName do |node|
     		node.vm.box = hostInfo['box'] ||= DEFAULT_BASE_BOX
     		node.vm.hostname = hostName																				#	Set the hostname
     		node.vm.network :private_network, ip: hostInfo['ansible_host']		# Set the IP address
				ram = hostInfo['memory']																					#	Set the memory
     		node.vm.provider :virtualbox do |vb|
       		vb.name = hostName
					vb.customize ["modifyvm", :id, "--cpuexecutioncap", cpuCap, "--memory", ram.to_s]
					vb.gui = true
     		end
     	end
    end
	end
end

