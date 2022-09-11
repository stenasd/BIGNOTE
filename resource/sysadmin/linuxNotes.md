# patrion mount and unmount disk
## view mounts patrions and drives
> fdisk -l
> lsblk
> df -h show diskspace
## commands to creat patrion and drive
unmount if its mounted to creat patrion
> sudo umount -l /dev/sda
creat patrion that whipes all data
> sudo mkfs.ext4 /dev/sda
creat mount at path
>  sudo mount -t auto /dev/sdb ./path



Learn more about ansible and teraform

teraform cloud service orcistration while ansible is on server only

learn/test grafana ansible teraform
