# juniper-srx
Sample Juniper SRX config

It is a working config file for Juniper SRX1500 under Junos 23.1R1.8

A basic config file to at least get your SRX1500 connects to the Internet, you may use it as template and further modify according to your needs

It includes below config

- NZ Auckland as system timezone, ntp server 162.159.200.1
- Connected top left 1000G RJ45 to fiber box (ge-7/0/0)
- Connected to LAN via top left 10G SFP+ (xe-7/0/16)
- Auto connect via FTTH fiber under New Zealand Voyager, with VLAN10 Tag disable opt in Please update [ISP_LOGIN] and [ISP_PASSWORD] provided by your ISP
- "user1" as the login, please update [USER_PASSWORD]
- Default root password, please update [ROOT_PASSWORD]
- Enabled services such as ssh, web management (J-Web), dhcp, read-only snmp
- Dynamic IP address for blacklist blocking, please update [LOCALWEBSERVER_IP] (Reference: https://www.reddit.com/r/Juniper/comments/i2t97y/srx_loading_custom_dynamiciplists_from_your_own/)
- Dynamic IP address for country blocking, please update [LOCALWEBSERVER_IP] (Reference: https://www.reddit.com/r/Juniper/comments/kmg1v8/region_blocking_on_srx_platform/)
- Opened inbound ports for
  1) Nginx - Please update [NGINX_IP] and [NGINX_PORT]
  2) OpenVPN - Please update [OPENVPN_IP] and [OPENVPN_PORT]
  Please update [SRX_EXTERNAL_IP] for your public IP, you may need to subscribe a fixed-ip as CG-NAT will not work
- Only allow ping, http and https traffic from untrust (Internet)
- Allow all traffics from zone trust to untrust
- DHCP pool
  For 192.168.1.1
    DHCP IP Range 192.168.1.100-192.168.1.253, (Reserved 192.168.1.2-192.168.1.99 for static IP)
- External DNS 1.1.1.1 (Cloudflare) and 8.8.8.8 (Google)
