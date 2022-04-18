Simple step-by-step guide to set up a quick NFS server on Linux using Docker

# Run this command to install docker & docker-compose:latest
sh install-docker.sh

# build images
docker-compose build

# start running servers
docker-compose up -d

# debugging
docker ps
docker attach <id>
docker logs <id>

# --------------Mounting filesystems from a client------------
sudo apt install nfs-client -y
sudo mount -v -o vers=4,loud [SERVER_IP]:/ /mnt
df -h
