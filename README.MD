### Wazuh Interface Config
1. Open `/etc/sysconfig/network-scripts/ifcfg-eth0` for editing.
2. Add/modify the following values:
```ini
BOOTPROTO=none
PREFIX=24
IPADDR=10.77.10.4
GATEWAY=10.77.10.254
DNS1=10.77.10.1
```
3. Reboot the server

### Wazuh Syslog Listener Config
1. Add the following lines to `/var/ossec/etc/ossec.conf`
```xml
<remote>
  <connection>syslog</connection>
  <port>514</port>
  <protocol>tcp</protocol>
  <allowed-ips>10.77.10.0/24</allowed-ips>
  <local_ip>10.77.10.4</local_ip>
</remote>
```
2. Restart the Wazuh Manager by running the following commands:
```bash
systemctl restart wazuh-manager
````