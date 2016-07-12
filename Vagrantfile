$prepare_docker_engine_script = <<SCRIPT
apt-get update;
apt-get install -y apt-transport-https ca-certificates;
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D;
echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' > /etc/apt/sources.list.d/docker.list;
apt-get update && apt-get install -y docker-engine=1.9.1-0~trusty;
mkdir /etc/ssl/docker && cd /etc/ssl/docker;
openssl genrsa -aes256 -out ca-key.pem -passout pass:unsecure 4096;
openssl req -new -x509 -days 365 -key ca-key.pem -subj "/CN=docker-engine.vagrant" -passin pass:unsecure -sha256 -out ca.pem;
openssl genrsa -out server-key.pem 4096;
openssl req -subj "/CN=docker-engine.vagrant" -sha256 -new -key server-key.pem -out server.csr;
echo 'subjectAltName = IP:10.0.7.10,IP:127.0.0.1' > extfile.cnf;
openssl x509 -req -days 365 -sha256 -in server.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem -extfile extfile.cnf -passin pass:unsecure;
openssl genrsa -out key.pem 4096;
openssl req -subj '/CN=client' -new -key key.pem -out client.csr;
echo 'extendedKeyUsage = clientAuth' > extfile.cnf;
openssl x509 -req -days 365 -sha256 -in client.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out cert.pem -extfile extfile.cnf -passin pass:unsecure;
cp ca.pem cert.pem key.pem /vagrant;
service docker stop;
rm -rf /etc/docker/key.json
echo 'DOCKER_OPTS="-H 0.0.0.0:2376 -H unix:///var/run/docker.sock --tlsverify --tlscacert=/etc/ssl/docker/ca.pem --tlscert=/etc/ssl/docker/server-cert.pem --tlskey=/etc/ssl/docker/server-key.pem"' | tee -a /etc/default/docker;
service docker start;
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.define "docker_engine" do |config|
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "docker-engine"
    config.vm.network "private_network", ip: "10.0.7.10"
    config.vm.provision "shell", inline: $prepare_docker_engine_script
  end
end
