# Docker on Vagrant

Docker on Vagrant to experiment with different versions/settings of Docker.

That's all folks !

This version creates a Docker engine 1.9 with TLS enabled.

Certs will be available in the root of this directory after first boot.

Use the following commands to access the Docker host:

```
$ docker run -it --privileged --name docker19 -v ${PWD}:/certs docker:1.9-dind sh
# docker --tlsverify --tlscacert=/certs/ca.pem --tlscert=/certs/cert.pem --tlskey=/certs/key.pem -H=10.0.7.10:2376 info
```
