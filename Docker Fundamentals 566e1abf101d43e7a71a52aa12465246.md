# Docker Fundamentals

Created by: den
Created time: July 25, 2023 5:31 PM
Doc stage: New

# Setup Docker

### Set up the repository

Update Package index & install packages to alllow apt use a repository over https

```bash
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl gnupg
```

Add Docker’s official GPG key

```bash
$ sudo install -m 0755 -d /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

set up the repository

```bash
$ echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Update the apt package index

```bash
$ sudo apt-get update
```

Install Docker Engine, containerd, and Docker Compose

```bash
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

# Docker Command

Show Docker CLI Command

```bash
$ docker --help
```

Show container images

```bash
$ docker image ls
$ docker images
```

Show Container running

```bash
$ docker container ls
$ docker ps
```

Show Container Not Running & Running

```bash

$ docker ps -a
```

Docker information

```bash
$ docker info
```

# **Docker practices**

pull image docker

```bash
$ docker pull nama-image
$ docker images
```

pull image with version

```bash
$ docker pull nama-image:versi
$ docker images
```

create container 

```bash
$ docker run -it nama-image
$ ps -aux
```

rename container 

```bash
$ docker rename nama-lama nama-baru
```

create container with name

```bash
$ docker run -it —name nama-container nama-image:versi
```

start container 

```bash
$ docker start nama-container
```

enter container

```bash
$ docker exec -it nama-contianer /bin/bash
```

install package on container

```bash
$ apt update -y
$ apt install nginx -y
```

running service nginx

```bash
$ nginx -g “daemon off;”
```

Supaya container bisa diakses oleh user dari luar, harus konfigurasi DNAT (Destination NAT), port forwarding

create image from existing container

```bash
$ docker commit -p nama-container nama-image-yang-mau-dibuat
$ docker images
```

create container use my image

```bash
$ docker run -dit -p 80:80 —name ct-nama-container nama-images
```

Untuk bekerja dibelakang layer & edit default page

```bash
$ docker exec -it nama-container nginx -g “daemon off;” &
$ find / -name index.html
```

copy file from host to container

```bash
$ docker cp file-yang-mau-dicopy nama-container:lokasi
```

create image use Dockerfile

```bash
$ vim Dockerfile
FROM ubuntu:16.04
RUN apt update -y && apt install nginx -y
CMD nginx -g “daemon off”
$ docker build -t test-image .
```

create image simple-apps use Dockerfile

```bash
FROM node:18.16.0
WORKDIR /app
ADD . /app
RUN npm install
CMD npm start
EXPOSE 3000
```

pull image from local to registry github

```bash
$ docker login
$ docker tag nama-image namaregistry/nama-image
$ docker push registry/nama-image
```

buat volume supaya container tidak menghapus datanya/persistant volume dan bisa sync file antar container

```bash
$ docker volume create data-web
$ docker volume ls
$ docker run -dit -p 91:80 -v data-web:/var/www/html --name ct-web21 ubuntu/apache2
$ docker run -dit -p 92:80 -v data-web:/var/www/html --name ct-web22 ubuntu/apache2
$ docker ps
$ docker volume inspect data-web
$ cd /var/lib/docker/volumes/data-web/_data/
$ ls

```

buat network docker (custom)

```bash
$ docker network ls
$ docker network inspect bridge
$ iptables -t nat -L
$ docker network create -d bridge --subnet 10.10.10.0/24 Net-Dev
$ docker network ls
$ ip a
$ iptables -t nat -L
```

buat container menggunakan custom network

```bash
$ docker run -dit -p 881ls
:80 --network Net-Dev --name ct-net ubuntu/apache2
$ docker inspect ct-net
```

by default, container tidak akan jalan secara otomatis jika host nya dimatikan lalu dinayalakan (rebbot) kembali, jika ingin melakukan autostart container, bisa di konfig di restart policy

ada 

- no = autostart container tidak menyala
- on-failure = container akan autostart/restart jika terjadi kesalahan pada container / bug aplikasi, tetapi restartnya akan dibatasi menggunakan parameter “max-retries”
- always = container akan autostart bila hostnya dimatikan atau jika dockernya di restart
- unless-stopped = container akan autostart bila hostnya matikan, tapi kalo dockernya dimatikan, container harus dijalankan secara manual

```bash
$ docker update --restart always nama-container
```

## Docker Compose

Docker compose adalah tool yang digunakan untuk membangun aplikasi yang kompleks. Cara kerjanya cukup simple. Kita membutuhkan berbagai Dockerfile seperti front-end, back-end, database, dll untuk banyak container.

Semakin banyak Dockerfile, kita semakin bingung jika tidak ada cara untuk manajemennya.

Dengan Docker compose, kita bisa menjadikan berbagai macam Dockerfile menjadi satu file saja.

Kalau satu file saja, eksekusi command pun akan berpengaruh terhadap seluruh file tersebut.

Nah, ini menunjukkan satu file yang powerful akan digunakan untuk container block, network block, front-end block, back-end block, dll.

Docker compose sangat baik, jika digunakan untuk membuat atau management mutiple container secara bersamaan

```bash
$ mkdir lab-compose
$ cd lab-compose
$ vim docker-compose.yml

```

open docker compose documentation

```bash
services:
  web-nginx:
    ports:
      - "1010:80"
		image: "nginx"
 
```

jalankan

```bash
$ docker compose up -d
$ docker compose ls
$ docker ps

testing akses via browser
```

run mutiple container

```bash
services:
  web-nginx:
    ports:
      - "1011:80"
		image: "nginx"
  web-apache:
    ports:
      - "1012:80"
		image: "ubuntu/apache2"
  web-httpd:
    ports:
      - "1013:80"
		image: "httpd"
```

run mutiple container = always restart

```bash
services:
  web-nginx:
    ports:
      - "1011:80"
		image: "nginx"
    restart: always
  web-apache:
    ports:
      - "1012:80"
		image: "ubuntu/apache2"
    restart: always
  web-httpd:
    ports:
      - "1013:80"
		image: "httpd"
    restart: always

```

note: jika ada perubahan konfigurasi file compose, maka akan dicreate ulang

pindahkan source code simple apps ke satu folde yang sama

buat compose file untuk simple apps

```bash
services:
  apps:
    build: ./apps
    ports:
      - "10000:3000"
    restart: always
    env_file: ./apps/.env
```

```bash
$ docker compose build
$ docker compose up -d
```

## Install Pontainer CE

untuk dashboarding container

[https://docs.portainer.io/start/install-ce/server/docker/linux](https://docs.portainer.io/start/install-ce/server/docker/linux)

```bash
$ docker volume create portainer_data
$ docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
$ docker ps
```

akses via browser menggunakan https dan port 9443

![Screenshot 2023-07-26 at 20.30.33.png](Docker%20Fundamentals%20566e1abf101d43e7a71a52aa12465246/Screenshot_2023-07-26_at_20.30.33.png)

## backup main container

```bash
$ docker ps
$ docker tag simple-apps-apps username-docker-hub/simple-apps-backup-deni:v1.0.0
$ docker login
$ docker push username-docker-github/simple-apps-backup-deni:v1.0.0

```