## Ako vyrobit balicek pre manjaro/Arch z deb balicka a nemat problem so zavislostami?

Zazracny program debtap.

* nainstalujeme debtap:

```
yaourt -S deptab
```

* nasledne prerobime deb balicek na manjaro/Arch balicek:
```
sudo debtab palicek.deb
```

* na konci zvolime jednu z moznosti upravy, nasledne zavrieme a mal by sa vytvorit subor balicek.pkg.tar.xz

* nainstalujeme vytvoreny balicek pomocou:

```
sudo pacman -U balicek.pkg.tar.xz # s -U som si nie isty - mne to blblo takze standardne asi -S
```
