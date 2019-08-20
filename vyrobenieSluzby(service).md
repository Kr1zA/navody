```
cd /etc/systemd/system
sudo vim NAZOV.service
```

Do tohoto vytvoreneho suboru vlozim nasledovne:

```
[Unit]
Description=POPIS SERVICE
[Service]
Type=simple
ExecStart=/umiestnenie/scriptu
Restart=always #ak chceme restartovanie v propacoch ... daju sa vygooglit
RestartSec=5s 
[Install]
WantedBy=multi-user.target
```

Nasledne:

```
sudo systemctl daemon-reload
sudo systemctl start citacka
sudo systemctl status citacka
sudo systemctl enable citacka

```
