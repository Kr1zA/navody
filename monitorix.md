# Instalacia a pouzivanie programu Monitorix

Monitorix is a free, open source, lightweight system monitoring tool designed to monitor as many services and system resources as possible. It has been created to be used under production Linux/UNIX servers, but due to its simplicity and small size can be used on embedded devices as well.

## Instalacia na Raspberry Pi

``` 
wget https://www.monitorix.org/monitorix_3.10.1-izzy1_all.deb #potrebne skontrolovat aktualnost
sudo dpkg -i monitorix_3.10.1-izzy1_all.deb
sudo apt --fix-broken install
``` 

## Pouzivanie na Raspberry Pi

Po uspesnej instalacii by mal monitorix bezat. Skontrolovat to vieme pomocou:
``` 
systemctl status monitorix #zobrazi stav servisu
systemctl stop monitorix #zastavi servis
systemctl start monitorix #nastartuje servis
systemctl enable monitorix #zapne servis aby sa spustal po starte automaticky
``` 

Uz len staci ist na stranku http://XXX.XXX.XXX.XXX:8080/monitorix kde XXX.XXX.XXX.XXX je ip adresa stroja na ktorom mame spusteny monitorix.

Konfigurak `/etc/monitorix/monitorix.conf`

Ak chceme monitorovat z jednej stranky viac zariadeni pouzijeme jedno zo zariadeni ako "hlavne" a upravime v konfiguraku nasledujuce riadky:

``` 
# Multihost
# -----------------------------------------------------------------------------
<multihost>
        enabled = y #zapnutie daneho zariadenia ako hlavneho
        footer_url = n #z bezpecnostnych dovodov nebudeme na stranke zobrazovat linky na ostatne zariadenia
        graphs_per_row = 3 #kolko grafov chcem vidiet v jednom riacku
        remotehost_list = device 0, device 1, device 2 #zvolime si lubovolne nazvy zariadeni ktore chceme monitorovat
        <remotehost_desc> #nastavime adresy jednotlivych zariadeni, ktore chceme monitorovat
                0 = http://XXX.XXX.XXX.XXX:8080
                1 = http://YYY.YYY.YYY.YYY:8080
                2 = http://ZZZ.ZZZ.ZZZ.ZZZ:8080
        </remotehost_desc>
        groups = n #grupy zatial pouzivat nebudeme
        remotegroup_list = My Group
        <remotegroup_desc>
                0 = server 2, server 3
        </remotegroup_desc>
</multihost>
``` 

