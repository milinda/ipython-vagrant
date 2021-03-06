# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 8888, host: 8888

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
     vb.gui = false
     # Customize the amount of memory on the VM:
     vb.memory = "1536"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y python3-pip
     sudo pip3 install "ipython[notebook]"
     sudo apt-get install -y build-essential python3-dev python3-setuptools python3-numexpr python3-scipy libatlas-dev libatlas3gf-base
     sudo update-alternatives --set libblas.so.3 /usr/lib/atlas-base/atlas/libblas.so.3
     sudo update-alternatives --set liblapack.so.3 /usr/lib/atlas-base/atlas/liblapack.so.3
     sudo apt-get install -y python-matplotlib
     sudo apt-get install -y python3-matplotlib
     sudo apt-get install -y python3-pandas
     sudo apt-get install -y python3-jinja2
     sudo apt-get install -y
     sudo pip3 install numpy
     sudo pip3 install textblob
     sudo pip3 install nltk
     sudo python -m nltk.downloader all
     sudo pip3 install --user --install-option="--prefix=" -U scikit-learn
     sudo apt-get install -y libzmq3-dev libcurl4-openssl-dev
     sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
     sudo add-apt-repository ppa:marutter/rrutter
     sudo apt-get update
     sudo apt-get install -y r-base r-base-dev
     cp /vagrant/Rprofile.site /etc/R/Rprofile.site
     sudo Rscript /vagrant/rkernel-install
     cp /vagrant/bashrc /home/vagrant/.bashrc
     cp /vagrant/pg1342.txt /home/vagrant/pg.txt
  SHELL
end
