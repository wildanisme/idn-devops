# Jenkins Fundamentals””

Created by: den
Created time: July 26, 2023 9:28 PM
Doc stage: New

## Install Jenkins on Centos

visit [https://www.jenkins.io/download/](https://www.jenkins.io/download/)

- set static ip server
- ubah hostname
- update && upgrade
- ubah mode selinux, setenforce 0
- download jenkins
- allow firewalld, firewall-cmd —add-port=8080/tcp —permanent

```bash
$ yum install wget -y
$ yum install ca-certificates -y
$ sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
$ yum install fontconfig java-11-openjdk
$ yum install jenkins -y
$ setenforce 0
$ firewall-cmd --add-port=8080/tcp --permanent
$ firewall-cmd --reload
$ systemctl enable --now jenkins
$ systemctl status jenkins

```

login

![Screenshot 2023-07-26 at 21.57.37.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_21.57.37.png)

get password jenkins on linux

```bash
$ cat /var/lib/jenkins/secrets/initialAdminPassword
```

paste password on jenkins

![Screenshot 2023-07-26 at 21.59.24.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_21.59.24.png)

![Screenshot 2023-07-26 at 22.00.29.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.00.29.png)

![Screenshot 2023-07-26 at 22.00.36.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.00.36.png)

![Screenshot 2023-07-26 at 22.09.30.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.09.30.png)

![Screenshot 2023-07-26 at 22.09.37.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.09.37.png)

![Screenshot 2023-07-26 at 22.09.44.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.09.44.png)

![Screenshot 2023-07-26 at 22.09.53.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.09.53.png)

# Configure Jenkins

jenkins bisa membuat job diservernya sendiri & juga bisa meremot job dari server lain, kebanyakan kasus, job jenkins harus diremote, jadi job jenkins gak ditumpuk di satu tempat jenkins saja 

Click Manage Jenkins

![Screenshot 2023-07-26 at 22.16.39.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.16.39.png)

Click New Node

![Screenshot 2023-07-26 at 22.17.49.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.17.49.png)

masukan node name (server yang ingin diremote job) & click permanent agent

![Screenshot 2023-07-26 at 22.18.10.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.18.10.png)

di bagian remote root directory, masukan directory yang berisi kumpulan job-job remote server. pastikan di server tujuan sudah ada directorynya

![Screenshot 2023-07-26 at 22.20.09.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.20.09.png)

usagenya disesuaikan dengan gambar, launch metode pilih via ssh. lalu masukan ip host yang ingin diremote jobnya,

![Screenshot 2023-07-26 at 22.23.59.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.23.59.png)

pilih credential jenkins

![Screenshot 2023-07-26 at 22.24.08.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.24.08.png)

masukan username & password yang terdaftar di host yang ingin diremote

![Screenshot 2023-07-26 at 22.24.28.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.24.28.png)

![Screenshot 2023-07-26 at 22.24.36.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.24.36.png)

pilih credential yang barusan dibuat

![Screenshot 2023-07-26 at 22.25.06.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.25.06.png)

pastikan ada node yang tadi ditambah, dan coba clik name nya

![Screenshot 2023-07-26 at 22.26.23.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.26.23.png)

jika ada keterangan “agent succesfully connected and online” maka sudah berhasil terkoneksi 

![Screenshot 2023-07-26 at 22.26.50.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.26.50.png)

informasi storage tidak lagi N/A

![Screenshot 2023-07-26 at 22.27.39.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.27.39.png)

## Create JOB in Jenkins

### Create file to remote server use jenkins

Create a JOB

![Screenshot 2023-07-26 at 22.42.25.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.42.25.png)

Create Folder

![Screenshot 2023-07-26 at 22.42.37.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.42.37.png)

Save

![Screenshot 2023-07-26 at 22.42.54.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.42.54.png)

Create a Job in folder

![Screenshot 2023-07-26 at 22.43.19.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.43.19.png)

Job freestylep → Freestyle Project

![Screenshot 2023-07-26 at 22.49.51.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.49.51.png)

masukan lebel lalu save

![Screenshot 2023-07-26 at 22.50.27.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.50.27.png)

click build environment, ketikan perintah execute shell, goalnya disini akan membuat file dan filenya akn disimpan di remote host

![Screenshot 2023-07-26 at 22.50.51.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.50.51.png)

click build now

![Screenshot 2023-07-26 at 22.51.04.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.51.04.png)

build history menandakan telah sukses

![Screenshot 2023-07-26 at 22.51.11.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.51.11.png)

checking file on remote host

![Screenshot 2023-07-26 at 22.54.46.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.54.46.png)

jenkins pipeline 

![Screenshot 2023-07-26 at 22.55.04.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.55.04.png)

klik pipeline syntaks & pilih shell script → shellscript, masukan perintah yang mau di eksekusi di remote host → generate pipeline script

![Screenshot 2023-07-26 at 22.57.58.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.57.58.png)

![Screenshot 2023-07-26 at 22.58.38.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_22.58.38.png)

![Screenshot 2023-07-26 at 23.02.28.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_23.02.28.png)

![Screenshot 2023-07-26 at 23.15.22.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_23.15.22.png)

click build now untuk menjalankan job

![Screenshot 2023-07-26 at 23.30.24.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-26_at_23.30.24.png)

## Integrasi jenkins dengan github

jenkins bisa pull source code dari github

jika repo github bersifat public repository maka tidak perlu kredensial

di server jenkins harus diinstall git 

```bash
$ yum install git
```

![Screenshot 2023-07-27 at 05.51.28.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_05.51.28.png)

remote repository public gtihub, sesuaikan branchnya

![Screenshot 2023-07-27 at 05.54.55.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_05.54.55.png)

![Screenshot 2023-07-27 at 05.55.29.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_05.55.29.png)

![Screenshot 2023-07-27 at 05.55.39.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_05.55.39.png)

remote repository private gtihub, sesuaikan branchnya, new item

masukan label & private repository github

![Screenshot 2023-07-27 at 06.09.31.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.09.31.png)

add user 

![Screenshot 2023-07-27 at 06.09.44.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.09.44.png)

username → username github, password → token github

![Screenshot 2023-07-27 at 06.11.20.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.11.20.png)

build now

![Screenshot 2023-07-27 at 06.11.55.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.11.55.png)

![Screenshot 2023-07-27 at 06.12.07.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.12.07.png)

## Deploying Simple-Apps NodeJS

Click Manage Jenkins

![Screenshot 2023-07-27 at 06.21.09.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.21.09.png)

Click plugins

![Screenshot 2023-07-27 at 06.21.21.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.21.21.png)

click available pugins → NodeJS → Install without restart

![Screenshot 2023-07-27 at 06.21.32.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.21.32.png)

Back → Tools → NodeJS → Version Node JS → Save

![Screenshot 2023-07-27 at 06.25.23.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.25.23.png)

Back to job jenkins simple-apps → configure

![Screenshot 2023-07-27 at 06.27.49.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.27.49.png)

Build Environment → Provide Node & NPM → ceklis

![Screenshot 2023-07-27 at 06.28.07.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.28.07.png)

build steps → execute shell → npm install → save

![Screenshot 2023-07-27 at 06.28.20.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.28.20.png)

sukses

![Screenshot 2023-07-27 at 06.28.30.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.28.30.png)

![Screenshot 2023-07-27 at 06.35.30.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.35.30.png)

jika tes connection database gagal, maka file .env harus di pindahkan dulu kedalam folder app nya

## Integrate Sonar Dengan Jenkins

manage jenkins → plugins → available plugin → install sonarqube scanner

![Screenshot 2023-07-27 at 06.49.25.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.49.25.png)

![Screenshot 2023-07-27 at 06.50.01.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.50.01.png)

click tools

![Screenshot 2023-07-27 at 06.49.25.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.49.25%201.png)

![Screenshot 2023-11-02 at 08.04.43.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-11-02_at_08.04.43.png)

![Screenshot 2023-11-01 at 22.52.31.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-11-01_at_22.52.31.png)

click system

buat token di sonarqube

![Screenshot 2023-07-27 at 20.09.48.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_20.09.48.png)

setting credential

![Screenshot 2023-07-27 at 06.55.56.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_06.55.56.png)

![Screenshot 2023-07-27 at 20.20.35.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_20.20.35.png)

![Screenshot 2023-07-27 at 20.11.21.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_20.11.21.png)

## Integrate docker dengan jenkins

docker harus open rest API terlebih dahulu (ip & port nya)

di docker server

```bash
$ vim /usr/lib/systemd/system/docker.service
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://10.23.1.5:2379 --containerd=/run/containerd/containerd.sock
$ systemctl daemon-reload
$ systemctl restart docker
```

di jenkins server harus diinstall plugin docker, setelah itu klik dasboard → manage jenkins → nodes → clouds

![Screenshot 2023-07-27 at 07.17.30.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_07.17.30.png)

![Screenshot 2023-07-27 at 07.17.38.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_07.17.38.png)

![Screenshot 2023-07-27 at 07.19.32.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_07.19.32.png)

save

hapus terlebih dahulu container docker compose yang sudah dibuat

 

```bash
$ cd simple-apps
$ ls
apps  docker-compose.yml
$ docker compose down
[+] Running 2/2
 ✔ Container simple-apps-apps-1  Removed                                                          10.3s 
 ✔ Network simple-apps_default   Removed                                                           0.1s 
```

back to job simple-apps

![Screenshot 2023-07-27 at 07.39.40.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_07.39.40.png)

check container di docker

![Screenshot 2023-07-27 at 07.41.02.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_07.41.02.png)

## Push Image use Jenkins

install docker di server jenkins, kebetulan pakai centos 7

```bash
$ sudo yum install -y yum-utils
$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
$ sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
$ sudo systemctl start docker
```

![Screenshot 2023-07-27 at 19.43.12.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_19.43.12.png)

disample apps job

![Screenshot 2023-07-27 at 19.43.18.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_19.43.18.png)

automatic checking update, build, deploying

![Screenshot 2023-07-27 at 19.55.46.png](Jenkins%20Fundamentals%E2%80%9D%E2%80%9D%208879d1ae56bb46af819375bf16a3321f/Screenshot_2023-07-27_at_19.55.46.png)

```jsx
pipeline {
    agent { label 'docker-server' }
    
    tools {nodejs "nodejs-simpleapps"}

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/dbynarie/simple-apps.git'
            }
        }
        stage('Build') {
            steps {
                sh '''cd apps
                npm install'''
            }
        }
        stage('Testing') {
            steps {
                sh '''cd apps
                npm test
                npm run test:coverage'''
            }
        }
        stage('Code Review') {
            steps {
                sh '''cd apps
                sonar-scanner \
                -Dsonar.projectKey=simple-apps \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://172.23.1.26:9000 \
                -Dsonar.login=sqp_98da4588442e35da671892708579dc6cfa69a578'''
            }
        }
        stage('Deploy compose') {
            steps {
                sh '''
                docker compose build
                docker compose up -d
                '''
            }
        }
    }
}
```