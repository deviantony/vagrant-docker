$prepare_docker_engine_script_19 = <<SCRIPT
apt-get update;
apt-get install -y apt-transport-https ca-certificates;
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D;
echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' > /etc/apt/sources.list.d/docker.list;
apt-get update && apt-get install -y docker-engine=1.9.1-0~trusty;
service docker stop;
rm -rf /etc/docker/key.json
echo 'DOCKER_OPTS="-H 0.0.0.0:2375 -H unix:///var/run/docker.sock --ip 10.0.7.9"' | tee -a /etc/default/docker;
service docker start;
SCRIPT
$prepare_docker_engine_script_110 = <<SCRIPT
apt-get update;
apt-get install -y apt-transport-https ca-certificates;
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D;
echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' > /etc/apt/sources.list.d/docker.list;
apt-get update && apt-get install -y docker-engine=1.10.3-0~trusty;
service docker stop;
rm -rf /etc/docker/key.json
echo 'DOCKER_OPTS="-H 0.0.0.0:2375 -H unix:///var/run/docker.sock --ip 10.0.7.10"' | tee -a /etc/default/docker;
service docker start;
SCRIPT
$prepare_docker_engine_script_111 = <<SCRIPT
apt-get update;
apt-get install -y apt-transport-https ca-certificates;
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D;
echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' > /etc/apt/sources.list.d/docker.list;
apt-get update && apt-get install -y docker-engine=1.11.2-0~trusty;
service docker stop;
rm -rf /etc/docker/key.json
echo 'DOCKER_OPTS="-H 0.0.0.0:2375 -H unix:///var/run/docker.sock --ip 10.0.7.11"' | tee -a /etc/default/docker;
service docker start;
SCRIPT
$prepare_docker_engine_script_112 = <<SCRIPT
apt-get update;
apt-get install -y apt-transport-https ca-certificates;
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D;
echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' > /etc/apt/sources.list.d/docker.list;
apt-get update && apt-get install -y docker-engine;
service docker stop;
rm -rf /etc/docker/key.json
echo 'DOCKER_OPTS="-H 0.0.0.0:2375 -H unix:///var/run/docker.sock --ip 10.0.7.12"' | tee -a /etc/default/docker;
service docker start;
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.define "docker_19" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "docker-19"
    config.vm.network "private_network", ip: "10.0.7.9"
    config.vm.provision "shell", inline: $prepare_docker_engine_script_19
    config.vm.synced_folder ".", "/vagrant", disabled: true
  end
  config.vm.define "docker_110" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "docker-110"
    config.vm.network "private_network", ip: "10.0.7.10"
    config.vm.provision "shell", inline: $prepare_docker_engine_script_110
    config.vm.synced_folder ".", "/vagrant", disabled: true
  end
  config.vm.define "docker_111" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "docker-111"
    config.vm.network "private_network", ip: "10.0.7.11"
    config.vm.provision "shell", inline: $prepare_docker_engine_script_111
    config.vm.synced_folder ".", "/vagrant", disabled: true
  end
  config.vm.define "docker_112" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "docker-112"
    config.vm.network "private_network", ip: "10.0.7.12"
    config.vm.provision "shell", inline: $prepare_docker_engine_script_112
    config.vm.synced_folder ".", "/vagrant", disabled: true
  end
end
