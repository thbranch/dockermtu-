
This is for a centos 7 docker 1.12 install should work with other versions 

# Set mtu as a env varable
vi /etc/sysconfig/docker
OPTIONS="--mtu=1400"

# Add the "EnvironmentFile" option and "$OPTIONS" to init file
vi /lib/systemd/system/docker.service
EnvironmentFile=/etc/sysconfig/docker
ExecStart=/usr/bin/dockerd $OPTIONS


#If existing install run
systemctl daemon-reload

#Restart the docker service 
systemctl restart docker

#Check the mtu with
docker network inspect bridge