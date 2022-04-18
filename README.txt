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
sudo mount -v -o vers=4,loud 10.124.16.7:/ /mnt
df -h

# -----------------Mounting DO Block Storages-----------------
# Create a mount point for your volume:
mkdir -p /mnt/om

# Mount your volume at the newly-created mount point:
mount -o discard,defaults,noatime /dev/disk/by-id/scsi-0DO_Volume_om-core-nfs1 /mnt/om

# Change fstab so the volume will be mounted after a reboot
echo '/dev/disk/by-id/scsi-0DO_Volume_om-core-nfs1 /mnt/om ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab

# Remember to reboot droplet for changes to take effect
