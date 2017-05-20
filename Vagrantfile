Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/xenial64'

  config.vm.network 'forwarded_port', guest: 80, host: 8080

  config.vm.provider 'virtualbox' do |vb|
    vb.gui = false
    vb.memory = '512'
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'hookii-wordpress.yml'
    # ansible.ask_vault_pass = true
    ansible.host_vars = {
      'default' => {
        'ansible_python_interpreter' => 'python3'
      }
    }
    ansible.groups = {
      'development' => ['default'],
    }
  end
end
