## Instalacia konkretnej verzie balika

```
sudo pacman -U urlBalika
```
Url napr (odtialto)[https://archive.archlinux.org/]

## Neaktualizovanie balika

Pre neupdatovanie niektoreho balika treba v subore `/etc/pacman.conf` upravit riadok:

```
#IgnorePkg =
```

odkomentovanim a dopisanim balika:

```
IgnorePkg = zabbix-agent
```
