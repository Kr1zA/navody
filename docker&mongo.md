# Ako rozbehat docker a mongo?

* nainstalujeme docker a spustime docker - standardne ho mam na manjare zasteveny - napr

```
sudo pacman -S docker
sudo systemctl start docker
```
Pre ubuntu: https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository

* vytvorime skupinu docker a pridame sa tam:

```
sudo groupadd docker
sudo usermod -aG docker kriza # kriza je nazov mojho konta/pouzivatela
```

* spravnost vieme otestovat:

```
docker run hello-world
```

* nainstalovany image/constainer vieme zmazat:

```
docker stop cisloProcesu # zastavime container ci image ci co to je
docker rmi hello-world
```

* na beziaci kontainer sa vieme pripojit:

```
ID=`docker ps | grep mongo | cut --characters=1-12` # finta ktora ziska idcko kontainera s nazvom mongo
docker exec -it $ID bash # samotne pripojenie
```

* nainstalujeme docker compose - aplikacia na spravu a vytvaraniekontainerov:
  
  ```
  sudo pacman -S docker-compose
  ```
 
  * pomocou docker compose vytvorime containery, najprv vytvorime zlozku s konfigurakmi:

  ```
  mkdir docker
  mkdir docker
  mkdir mongo
  cd mongo/
  vim docker-compose.yml # alebo iny oblubeny editor
  ```
  
  * do otvoreneho suboru vlozime nasledovne: 
  
  ```
  version: "3.4"
  services:
          mongo:
                  image: mongo # nainstalujeme mongodb
                  # restart: always # po klaknuti by sa restartovat
                  ports:
                          - 27017:27017
                  environment: # prihlasovanie udaje
                          MONGO_INITDB_ROOT_USERNAME: root
                          MONGO_INITDB_ROOT_PASSWORD: zleHeslo

          mongo-express:
                  image: mongo-express # nainstalujeme mongodb veboveho klienta - nieco ako phpmyadmin
                  # restart: always # po klaknuti by sa restartovat
                  ports:
                          - 8081:8081
                  environment: # prihlasovanie udaje
                          ME_CONFIG_MONGODB_ADMINUSERNAME: root
                          ME_CONFIG_MONGODB_ADMINPASSWORD: zleHeslo
                          ME_CONFIG_BASICAUTH_USERNAME: root
                          ME_CONFIG_BASICAUTH_PASSWORD: zleHeslo
  ```

  * ked sa nachadzame vzlozke s konfigurakom spustime nasledovny prikaz:
  
  ```
  docker-compose up -d
  ```

  * nasledovnymi prikazmi vieme pozriet co bezi, stopnut co sme spustili:
  
```
docker ps
docker-compose stop
```
