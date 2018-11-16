# Vytvorenie docker file

* v zlozke s projektom vytvorime/upravime Dockerfile:

```
  FROM node:8

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copi$
# where available (npm@5+)
COPY package*.json ./
RUN npm install --only=production

# Bundle app source
COPY . .

EXPOSE 3000
CMD [ "npm", "start" ]
```

* prihlasime sa gitlab container registry

```
docker login gitlab.xxx.xxx:4567
```

* nasledne zbuildujeme a pushneme vytvoreny docker image:

```
docker build -t gitlab.xxx.xxx:4567/meno/nazovProjektu .
docker push gitlab.xxx.xxx:4567/meno/nazovProjektu
```

* teraz chceme vytvoreny a na gite ulozeny image deploynut na serveri:

```
docker login gitlab.xxx.xxx:4567
```

* pri problemoch s prihlasenim:

```
sudo mv /usr/bin/docker-credential-secretservice /usr/bin/docker-credential-secretservice_x
```
    * zdroj: 
    https://stackoverflow.com/questions/50151833/cannot-login-to-docker-account 

* zvysok - stiahnutie a spustenie(radsej docker-compose) je popisany tu: https://gitlab.science.upjs.sk/help/user/project/container_registry
