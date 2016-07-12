# Docker on Vagrant

Docker on Vagrant to experiment with different versions/settings of Docker.

That's all folks !

This version creates a Docker engine using the latest version with TLS enabled.

Certs will be available in the root of this directory after first boot.

Use the following command to access the Docker host:

```
$ docker --tlsverify --tlscacert=ca.pem --tlscert=cert.pem --tlskey=key.pem -H=10.0.7.10:2376 info
```
