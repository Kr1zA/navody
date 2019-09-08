## Nastavenie firewallu ako whitelist

* najprv vsetko zakazem

```
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
```

* povolenie DNS

```
iptables -A OUTPUT -p udp --dport 53  -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53  -j ACCEPT
iptables -A INPUT -p tcp --sport 53  -j ACCEPT
iptables -A INPUT -p udp --sport 53  -j ACCEPT
```

* povolenie HTTP
```
iptables -A INPUT -p tcp  --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp  --sport 22 -j ACCEPT

```
