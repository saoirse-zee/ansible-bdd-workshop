# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'.freeze

# system "vagrant plugin update"
# required_plugins = %w(vagrant-digitalocean)
# required_plugins.each do |plugin|
#   system "NOKOGIRI_USE_SYSTEM_LIBRARIES=1 vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
# end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.define 'ansible' do |ansible|
    ansible.vm.hostname = 'ansible'
    ansible.vm.network 'private_network', ip: '33.33.33.36'
#    ansible.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)"
    ansible.vm.provider 'virtualbox' do |provider|
      provider.name = 'ansible'
      provider.customize ['modifyvm', :id, '--memory', '512']
    end

    ansible.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yml'
      ansible.inventory_path = 'inventory'
      ansible.host_key_checking = false
      ansible.sudo = true
    end
  end

end
