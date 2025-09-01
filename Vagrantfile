Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
    vb.name = "python-devtest"
  end

  config.vm.provision "file", source: "input", destination: "/home/vagrant/input"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y python3 python3-pip
    apt-get install -y libpq-dev python3-dev
    pip3 install psycopg2-binary Django
    python3 --version
    pip3 --version
    python3 -c "import django; print('Django version:', django.get_version())"
    python3 -c "import psycopg2; print('Psycopg2 installed successfully')"
    echo "Файл 'input' копирован в /home/vagrant/input"
  SHELL
end
