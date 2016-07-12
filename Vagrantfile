$prepare_docker_engine_script = <<SCRIPT
apt-get update;
apt-get install -y apt-transport-https ca-certificates;
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D;
echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' > /etc/apt/sources.list.d/docker.list;
apt-get update && apt-get install -y docker-engine=1.9.1-0~trusty;
service docker stop;
rm -rf /etc/docker/key.json
echo 'DOCKER_OPTS="-H 0.0.0.0:2375 -H unix:///var/run/docker.sock"' | tee -a /etc/default/docker;
service docker start;
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.define "docker_engine" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "docker-engine"
    config.vm.network "private_network", ip: "10.0.7.10"
    config.vm.provision "shell", inline: $prepare_docker_engine_script
    config.vm.synced_folder ".", "/vagrant", disabled: true
  end
end
