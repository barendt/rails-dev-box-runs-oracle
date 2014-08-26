Vagrant.configure('2') do |config|
  config.vm.box      = 'trusty64'
  config.vm.box_url  = 'https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box'
  config.vm.hostname = 'rails-dev-box'

  config.vm.network :forwarded_port, guest: 3000, host: 3000
  # Forward Oracle port
  config.vm.network :forwarded_port, guest: 1521, host: 1521

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = 'puppet/manifests'
    puppet.module_path    = 'puppet/modules'
  end

  # Provider-specific configuration so you can fine-tune various backing
  # providers for Vagrant. These expose provider-specific options.
  config.vm.provider :virtualbox do |vb|
    # Use VBoxManage to customize the VM
    vb.customize ["modifyvm", :id,
                  "--name", "oracle",
                  # Oracle claims to need 512MB of memory available minimum
                  "--memory", "512",
                  # Enable DNS behind NAT
                  "--natdnshostresolver1", "on"]
  end
end
