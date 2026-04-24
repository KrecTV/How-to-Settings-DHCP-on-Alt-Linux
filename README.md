# How-to-Settings-DHCP-on-Alt-Linux

apt-get install -y dhcp-server

cd /etc/dhcp

cp dhcpd.conf.sample dhcpd.conf

nano dhcpd.conf

ddns-update-style none;

subnet 192.168.200.0 netmask 255.255.255.0 {
        option routers                  192.168.200.1;
        option subnet-mask              255.255.255.0;

        option nis-domain               "au-team.irpo";
        option domain-name              "au-team.irpo";
        option domain-name-servers      192.168.100.2;

        range dynamic-bootp 192.168.200.2 192.168.200.2;
        default-lease-time 21600;
        max-lease-time 43200;
}

systemctl enable --now dhcpd
