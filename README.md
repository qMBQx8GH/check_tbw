# check_tbw
 nagios nrpe plugin for ssd disks lifespan

# install

Clone repository and make a link
```ln -s /path/to/check_nrpe /usr/lib/nagios/plugins/check_nrpe```
```apt-get install smartmontools nvme```

# configure nrpe
```echo 'nagios ALL = NOPASSWD: /usr/sbin/smartctl' >> /etc/sudoers.d/nagios```
```echo 'nagios ALL = NOPASSWD: /usr/sbin/nrpe' >> /etc/sudoers.d/nagios```

Edit /etc/nagios/nrpe.cfg

sata ssd:
```command[check_tbw_sda]=/usr/lib/nagios/plugins/check_tbw -d /dev/sda -n 233 -s  1024 -w  79 -c 80```

nvme ssd:
```command[check_tbw_nvme0n1]=/usr/lib/nagios/plugins/check_tbw -d /dev/nvme0n1 -n nvme -w 3199 -c 3200```

