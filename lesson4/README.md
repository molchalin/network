## Урок 4

```bash
sudo sysctl -w 'net.ipv4.ip_forward = 1'
sudo ufw allow 5022
sudo sed -i 's/DEFAULT_FORWARD_POLICY="DROP"/DEFAULT_FORWARD_POLICY="ACCEPT"/' /etc/default/ufw
sudo systemctl restart ufw
```

```bash
sudo iptables -t nat -A PREROUTING -p tcp --dport 5022 -j DNAT --to-destination <IP>:22
sudo iptables -t nat -A POSTROUTING -p tcp --dport 22 -d <IP> -j MASQUERADE
```
