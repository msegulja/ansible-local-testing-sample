Vagrant.configure(2) do |config|
  config.vm.box = 'centos/7'
  config.vm.hostname = 'ansible.local'
  config.vm.network :private_network, ip: '192.168.56.100'
  config.vm.provider :virtualbox do |v|
    v.gui = false
    v.memory = 2048
  end

  config.vm.provision 'ansible_local' do |ansible|
    ansible.limit = 'all'
    ansible.inventory_path = 'hosts'
    ansible.playbook = 'local.yml'
    ansible.compatibility_mode = '2.0'
  end

  config.vm.provision :serverspec do |spec|
    spec.pattern = 'test/*_spec.rb' # pattern for spec files
  end
end
