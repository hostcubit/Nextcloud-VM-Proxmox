# Nextcloud-VM-Proxmox
Nextcloud VM template for Proxmox

This image is ready to import as a template to create nextcloud instances in proxmox

Instructions:
1. Upload the packaging in / var / lib / vz / dump (if you use it as copies)
2. From the interface of proxmox >> the storage backups >> restore the packaging (you can configure it according to your needs)


Nextcloud VM for PROXMOX 
- First setup instructions

1. Macke a full clone

2. Boot up your vm and login with 
user: ncadmin
pass: nextcloud

3. Before putting the vm machine into production make sure to configure the network (in / etc / netplan / yourconfig.yaml) and the public IP of the host in / etc / hosts


Dependencies:

(Ubuntu Server 20.04 LTS 64-bit)
(Linux Kernel: 5.14)

    Apache 2.4
    PostgreSQL 12
    PHP-FPM 7.4
    Redis Memcache (latest stable version from PECL)
    APCu local cache (latest stable version from PECL)
    PHP-igbinary (latest stable version from PECL
    PHP-smbclient (latest stable version from PECL)
    Nextcloud Server Latest
    
    
    
##################################################################


Another alternative is to create a VM with ubuntu 20.04 and follow the instructions from the original repo


NEXTCLOUD INSTALL

STEP 1 — Download and execute the latest Nextcloud VM installer script using super user do (sudo):

    wget https://raw.githubusercontent.com/nextcloud/vm/master/nextcloud_install_production.sh
    
    sudo bash nextcloud_install_production.sh
    
    After the first script completes …
    
STEP 2 — The VM automatically reboots.

STEP 3 — Login with your new user name locally or remotely (via CLI: ssh <user>@IP-ADDRESS). The second script executes and completes installation.


IMPORTANT NOTE

*If the VM automatically runs as root after rebooting, press CTRL+C to abort nextcloud-startup-script.sh. Then manually run the startup script as your newly-created user:* sudo -u <user> sudo bash /var/scripts/nextcloud-startup-script.sh — Setup is not finished after running the first script. Both must execute consecutively.


TIPS & TRICKS:

1. Publish your server online: https://goo.gl/iUGE2U
2. To login to PostgreSQL just type: sudo -u postgres psql nextcloud_db 
3. To update this server just type: sudo bash /var/scripts/update.sh
4. Install apps, configure Nextcloud, and server: sudo bash /var/scripts/menu.sh


EXTRAS

ADD ADITIONAL DISK:

zpool create -f archivos /dev/sdb

sudo chown -Rfv www-data:www-data /archivos

chmod -R 0750 /archivos


