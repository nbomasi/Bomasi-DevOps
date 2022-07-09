# WEB SOLUTION WITH WORDPRESS #

sudo gdisk /dev/xvdf To create partion xvdf
sudo gdisk /dev/xvdg To create partion xvdg
sudo gdisk /dev/xvdh To create partion xvdh

Partitions created.PNG  Partition page

sudo pvcreate /dev/xvdf1 /dev/xvdg1 /dev/xvdh1 #To create physical volume (PV)

To create volume group named webdata-vg from the PVs
sudo vgcreate webdata-vg /dev/xvdf1 /dev/xvdg1 /dev/xvdh1

To create 2 logical volumes (apps-lv and logs-lv) from the  Vg
sudo lvcreate -n apps-lv -L 14G webdata-vg
sudo lvcreate -n logs-lv -L 14G webdata-vg
LVs created.PNG

To Create file system for the LV (ext4)
sudo mkfs -t ext4 /dev/webdata-vg/apps-lv
sudo mkfs -t ext4 /dev/webdata-vg/logs-lv

To create directories that will store website file data and log data That will be my mount point
sudo mkdir -p /var/www/html
sudo mkdir -p /home/recovery/logs

To store logs into the new mount points created created.
sudo rsync -av /var/log/. /home/recovery/logs/
sudo rsync -av /home/recovery/logs/. /var/log

To mount in /var/www/html and /var/log
UUID=32bddfa2-7f74-41b1-9a8f-53d0149661ce /var/www/html ext4 defaults 0 0
UUID=0c9dad11-6753-4bae-add6-277587253002 /var/log ext4 defaults 0 0 