Simple docker-compose.yaml for running Home Assistiant as an unprivileged user on any linux distro

#Fedora

You need to use the docker-packages from the Docer-CE-repo:

Installation-instrucitions here:
https://computingforgeeks.com/how-to-install-docker-on-fedora/

## TL;DR

As root:

	dnf config-manager --add-repo=https://download.docker.com/linux/fedora/docker-ce.repo
	dnf install docker-compose
	dnf remove moby-engine
	dnf install docker-ce
	systemctl enable --now containerd
	systemctl enable --now docker

	cp docker-cleanup.* /etc/systemd/system/
	cp docker-compose@.service /etc/systemd/system/

	cp -r home-assistant/ /etc/docker/

... or modify the path for WorkingDirectory in docker-compose@.service to reflect the dir where the home-assistant/docker-compose.yaml-file is located

	systemctl enable --now docker-cleanup.timer
	systemctl enable --now docker-compose@home-assistant




## Certbot
	certbot renew  --no-self-upgrade --standalone --preferred-challenges http-01

