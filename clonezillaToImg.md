## Vytvorenie mountovatelneho obrazu z obrazu Clonezilly

Potrebny program partclone

```
cat sda2.ext4-ptcl-img.gz.a* | gzip -d -c | partclone.restore -W -o sda2.img -L partclone.log
```

Prikaz vytvori img obraz `sda2.img` z obrazu `sda2.ext4-ptcl-img.gz.a*`. 
Do suboru `partclone.log` sa ulozi log z programu partclone.
!!!Vysledny obraz bude mat velkost povodnej particie/disku!!!

Potom uz staci len namontovat vytvoreny obraz:

```
sudo mount  -t ext4 sda2.img /mnt
```
