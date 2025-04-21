# SonarQube Fundamentals

Created by: den
Created time: July 25, 2023 5:44 AM
Doc stage: New
Tags: Engineering

# SonarQube

## What’s SonarQube?

Menciptakan sebuah *software* secara efisien dengan sedikit atau bahkan tanpa *bug* memang menjadi sebuah pekerjaan menantang, dan hal ini justru seringkali dialami *developer.* Untuk bisa membangun *software* yang sempurna, *developer* tak cuma harus menerapkan cara terbaik, tetapi juga perlu diikuti oleh *code* Quality Assurance (QA) berkelanjutan yang optimal.

Karenanya, dalam memastikan *software* yang dibangun bisa bekerja efektif dan tetap aman, penting bagi *developer* untuk mengujinya secara menyeluruh di semua tahap pengembangan dan di setiap pembaruan *code* baru yang dirilis. Salah satunya adalah dengan menggunakan SonarQube, *tool* teknologi yang ada di dalam Static Application Security Testing atau SAST. Sesuai dengan namanya, SAST menjadi cara ideal untuk mengeliminasi *bug* yang bisa membantu *developer* aplikasi dalam melakukan *checking code* dan rilis.

SonarQube adalah *platform open-source* yang dikembangkan oleh SonarSource, digunakan untuk inspeksi berkelanjutan pada kualitas *code* aplikasi. Lebih dari itu, SonarQube juga dapat melakukan analisis *code* secara statis, yang mana menyediakan laporan lebih detail terkait *bug*, *code smells*, kerentanan hingga duplikasi *code*.

## Architecture SonarQube

![Screenshot 2023-07-25 at 05.49.35.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_05.49.35.png)

Arsitektur SonarQube dapat dilihat dari ilustrasi di atas. Komponennya terdiri dari Bahasa Pemrograman, SonarQube Scanner, SonarQube Server, serta SonarQube Database.

Bagian SonarQube Scanner akan digunakan dalam CI/CD *tools* untuk mengirim *report* ke dalam SonarQube Server, SonarQube scanner juga mendukung berbagai macam bahasa *framework* seperti MSBuild, Maven, Ant, dan Gradle.

Adapun SonarQube Server dapat diinstal di sistem operasi Windows, Linux, dan hingga *container*, sehingga SonarQube bisa dipasang via *microservices* di atas *container orchestration* seperti OpenShift dan Kubernetes.

Sejauh ini bahasa pemrograman yang didukung SonarQube cukup banyak, yaitu 17 untuk versi *community*, 24 untuk versi *developer*, 29 untuk versi *enterprise* dan *data center*. Bahasa pemrograman tersebut merupakan bahasa yang telah melalui *built-in rulesets* dan bisa diperpanjang dengan berbagai jenis *plugins*.

## Installation SonaQube

### Install Java

```bash
root@devops:/home/ubuntu# apt install openjdk-17-jdk openjdk-17-jre -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 libxmlb1
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  adwaita-icon-theme at-spi2-core ca-certificates-java fontconfig fontconfig-config fonts-dejavu-core
  fonts-dejavu-extra gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme java-common
  libatk-bridge2.0-0 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-data libatspi2.0-0
  libavahi-client3 libavahi-common-data libavahi-common3 libcairo-gobject2 libcairo2 libcups2 libdatrie1
  libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libfontconfig1 libfontenc1 libgail-common
  libgail18 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgif7 libgl1 libgl1-mesa-dri
  libglapi-mesa libglvnd0 libglx-mesa0 libglx0 libgraphite2-3 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libharfbuzz0b libice-dev libice6 libjbig0 libjpeg-turbo8 libjpeg8 liblcms2-2 libllvm12 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcsclite1 libpixman-1-0 libpthread-stubs0-dev
  librsvg2-2 librsvg2-common libsensors-config libsensors5 libsm-dev libsm6 libthai-data libthai0 libtiff5
  libvulkan1 libwayland-client0 libwebp6 libx11-dev libx11-xcb1 libxau-dev libxaw7 libxcb-dri2-0 libxcb-dri3-0
  libxcb-glx0 libxcb-present0 libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1
  libxcb-xfixes0 libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxfixes3 libxft2 libxi6
  libxinerama1 libxkbfile1 libxmu6 libxpm4 libxrandr2 libxrender1 libxshmfence1 libxt-dev libxt6 libxtst6
  libxv1 libxxf86dga1 libxxf86vm1 mesa-vulkan-drivers openjdk-17-jdk-headless openjdk-17-jre-headless
  ubuntu-mono x11-common x11-utils x11proto-core-dev x11proto-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  default-jre cups-common gvfs libice-doc liblcms2-utils pcscd librsvg2-bin lm-sensors libsm-doc libx11-doc
  libxcb-doc libxt-doc openjdk-17-demo openjdk-17-source visualvm libnss-mdns fonts-ipafont-gothic
  fonts-ipafont-mincho fonts-wqy-microhei | fonts-wqy-zenhei fonts-indic mesa-utils
The following NEW packages will be installed:
  adwaita-icon-theme at-spi2-core ca-certificates-java fontconfig fontconfig-config fonts-dejavu-core
  fonts-dejavu-extra gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme java-common
  libatk-bridge2.0-0 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-data libatspi2.0-0
  libavahi-client3 libavahi-common-data libavahi-common3 libcairo-gobject2 libcairo2 libcups2 libdatrie1
  libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libfontconfig1 libfontenc1 libgail-common
  libgail18 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgif7 libgl1 libgl1-mesa-dri
  libglapi-mesa libglvnd0 libglx-mesa0 libglx0 libgraphite2-3 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libharfbuzz0b libice-dev libice6 libjbig0 libjpeg-turbo8 libjpeg8 liblcms2-2 libllvm12 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcsclite1 libpixman-1-0 libpthread-stubs0-dev
  librsvg2-2 librsvg2-common libsensors-config libsensors5 libsm-dev libsm6 libthai-data libthai0 libtiff5
  libvulkan1 libwayland-client0 libwebp6 libx11-dev libx11-xcb1 libxau-dev libxaw7 libxcb-dri2-0 libxcb-dri3-0
  libxcb-glx0 libxcb-present0 libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1
  libxcb-xfixes0 libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxfixes3 libxft2 libxi6
  libxinerama1 libxkbfile1 libxmu6 libxpm4 libxrandr2 libxrender1 libxshmfence1 libxt-dev libxt6 libxtst6
  libxv1 libxxf86dga1 libxxf86vm1 mesa-vulkan-drivers openjdk-17-jdk openjdk-17-jdk-headless openjdk-17-jre
  openjdk-17-jre-headless ubuntu-mono x11-common x11-utils x11proto-core-dev x11proto-dev xorg-sgml-doctools
  xtrans-dev
0 upgraded, 120 newly installed, 0 to remove and 63 not upgraded.
Need to get 170 MB of archives.
After this operation, 878 MB of additional disk space will be used.
Get:1 http://id.archive.ubuntu.com/ubuntu focal/main amd64 hicolor-icon-theme all 0.17-2 [9,976 B]
Get:2 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1.20.04.3 [118 kB]
Get:3 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2,194 B]
Get:4 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libjbig0 amd64 2.1-3.1ubuntu0.20.04.1 [27.3 kB]
Get:5 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libwebp6 amd64 0.6.1-2ubuntu0.20.04.2 [185 kB]
Get:6 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libtiff5 amd64 4.1.0+git191117-2ubuntu0.20.04.8 [163 kB]
Get:7 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libgdk-pixbuf2.0-common all 2.40.0+dfsg-3ubuntu0.4 [4,592 B]
Get:8 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libgdk-pixbuf2.0-0 amd64 2.40.0+dfsg-3ubuntu0.4 [168 kB]
Get:9 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 gtk-update-icon-cache amd64 3.24.20-0ubuntu1.1 [28.8 kB]
Get:10 http://id.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1,041 kB]
Get:11 http://id.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
Get:12 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
Get:13 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libpixman-1-0 amd64 0.38.4-0ubuntu2.1 [227 kB]
Get:14 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-render0 amd64 1.14-2 [14.8 kB]
Get:15 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-shm0 amd64 1.14-2 [5,584 B]
Get:16 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxrender1 amd64 1:0.9.10-1 [18.7 kB]
Get:17 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libcairo2 amd64 1.16.0-4ubuntu1 [583 kB]
Get:18 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libcairo-gobject2 amd64 1.16.0-4ubuntu1 [17.2 kB]
Get:19 http://id.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig amd64 2.13.1-2ubuntu3 [171 kB]
Get:20 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgraphite2-3 amd64 1.3.13-11build1 [73.5 kB]
Get:21 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libharfbuzz0b amd64 2.6.4-1ubuntu4.2 [391 kB]
Get:22 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libthai-data all 0.1.28-3 [134 kB]
Get:23 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libdatrie1 amd64 0.2.12-3 [18.7 kB]
Get:24 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libthai0 amd64 0.1.28-3 [18.1 kB]
Get:25 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libpango-1.0-0 amd64 1.44.7-2ubuntu4 [162 kB]
Get:26 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libpangoft2-1.0-0 amd64 1.44.7-2ubuntu4 [34.9 kB]
Get:27 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libpangocairo-1.0-0 amd64 1.44.7-2ubuntu4 [24.8 kB]
Get:28 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 librsvg2-2 amd64 2.48.9-1ubuntu0.20.04.1 [2,253 kB]
Get:29 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 librsvg2-common amd64 2.48.9-1ubuntu0.20.04.1 [9,212 B]
Get:30 http://id.archive.ubuntu.com/ubuntu focal/main amd64 humanity-icon-theme all 0.6.15 [1,250 kB]
Get:31 http://id.archive.ubuntu.com/ubuntu focal/main amd64 ubuntu-mono all 19.04-0ubuntu3 [147 kB]
Get:32 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 adwaita-icon-theme all 3.36.1-2ubuntu0.20.04.2 [3,441 kB]
Get:33 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libatspi2.0-0 amd64 2.36.0-2 [64.2 kB]
Get:34 http://id.archive.ubuntu.com/ubuntu focal/main amd64 x11-common all 1:7.7+19ubuntu14 [22.3 kB]
Get:35 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxtst6 amd64 2:1.2.3-1 [12.8 kB]
Get:36 http://id.archive.ubuntu.com/ubuntu focal/main amd64 at-spi2-core amd64 2.36.0-2 [48.7 kB]
Get:37 http://id.archive.ubuntu.com/ubuntu focal/main amd64 java-common all 0.72 [6,816 B]
Get:38 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libavahi-common-data amd64 0.7-4ubuntu7.2 [21.4 kB]
Get:39 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libavahi-common3 amd64 0.7-4ubuntu7.2 [21.7 kB]
Get:40 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libavahi-client3 amd64 0.7-4ubuntu7.2 [25.5 kB]
Get:41 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libcups2 amd64 2.3.1-9ubuntu1.4 [233 kB]
Get:42 http://id.archive.ubuntu.com/ubuntu focal/main amd64 liblcms2-2 amd64 2.9-4 [140 kB]
Get:43 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libpcsclite1 amd64 1.8.26-3 [22.0 kB]
Get:44 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 openjdk-17-jre-headless amd64 17.0.7+7~us1-0ubuntu1~20.04 [43.7 MB]
Get:45 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 ca-certificates-java all 20190405ubuntu1.1 [12.4 kB]
Get:46 http://id.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-extra all 2.37-1 [1,953 kB]           
Get:47 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libatk1.0-data all 2.35.1-1ubuntu2 [2,964 B]       
Get:48 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libatk1.0-0 amd64 2.35.1-1ubuntu2 [45.5 kB]        
Get:49 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libatk-bridge2.0-0 amd64 2.34.2-0ubuntu2~20.04.1 [58.2 kB]
Get:50 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libfontenc1 amd64 1:1.1.4-0ubuntu1 [14.0 kB]       
Get:51 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libglvnd0 amd64 1.3.2-1~ubuntu0.20.04.2 [48.1 kB]
Get:52 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libglapi-mesa amd64 21.2.6-0ubuntu0.1~20.04.2 [27.4 kB]
Get:53 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libx11-xcb1 amd64 2:1.6.9-2ubuntu1.5 [9,256 B]
Get:54 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-dri2-0 amd64 1.14-2 [6,920 B]               
Get:55 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-dri3-0 amd64 1.14-2 [6,552 B]               
Get:56 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-glx0 amd64 1.14-2 [22.1 kB]                 
Get:57 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-present0 amd64 1.14-2 [5,560 B]             
Get:58 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-sync1 amd64 1.14-2 [8,884 B]                
Get:59 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-xfixes0 amd64 1.14-2 [9,296 B]              
Get:60 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxfixes3 amd64 1:5.0.3-2 [10.9 kB]               
Get:61 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxshmfence1 amd64 1.3-1 [5,028 B]                
Get:62 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxxf86vm1 amd64 1:1.1.4-1build1 [10.2 kB]        
Get:63 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libdrm-amdgpu1 amd64 2.4.107-8ubuntu1~20.04.2 [18.6 kB]
Get:64 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libpciaccess0 amd64 0.16-0ubuntu1 [17.9 kB]        
Get:65 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libdrm-intel1 amd64 2.4.107-8ubuntu1~20.04.2 [60.3 kB]
Get:66 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libdrm-nouveau2 amd64 2.4.107-8ubuntu1~20.04.2 [16.6 kB]
Get:67 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libdrm-radeon1 amd64 2.4.107-8ubuntu1~20.04.2 [19.7 kB]
Get:68 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libllvm12 amd64 1:12.0.0-3ubuntu1~20.04.5 [18.8 MB]
Get:69 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libsensors-config all 1:3.6.0-2ubuntu1.1 [6,052 B]
Get:70 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libsensors5 amd64 1:3.6.0-2ubuntu1.1 [27.2 kB]
Get:71 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libvulkan1 amd64 1.2.131.2-1 [93.3 kB]             
Get:72 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libgl1-mesa-dri amd64 21.2.6-0ubuntu0.1~20.04.2 [11.0 MB]
Get:73 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libglx-mesa0 amd64 21.2.6-0ubuntu0.1~20.04.2 [137 kB]
Get:74 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libglx0 amd64 1.3.2-1~ubuntu0.20.04.2 [32.5 kB]
Get:75 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libgl1 amd64 1.3.2-1~ubuntu0.20.04.2 [85.8 kB]
Get:76 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libice6 amd64 2:1.0.10-0ubuntu1 [41.0 kB]          
Get:77 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libsm6 amd64 2:1.2.3-1 [16.1 kB]                   
Get:78 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxt6 amd64 1:1.1.5-1 [160 kB]                    
Get:79 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxmu6 amd64 2:1.1.3-0ubuntu1 [45.8 kB]           
Get:80 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libxpm4 amd64 1:3.5.12-1ubuntu0.20.04.1 [34.6 kB]
Get:81 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxaw7 amd64 2:1.0.13-1 [173 kB]                  
Get:82 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-shape0 amd64 1.14-2 [5,928 B]               
Get:83 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcomposite1 amd64 1:0.4.5-1 [6,976 B]           
Get:84 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxft2 amd64 2.3.3-0ubuntu1 [39.2 kB]             
Get:85 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxi6 amd64 2:1.7.10-0ubuntu1 [29.9 kB]           
Get:86 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxinerama1 amd64 2:1.1.4-2 [6,904 B]             
Get:87 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxkbfile1 amd64 1:1.1.0-1 [65.3 kB]              
Get:88 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxrandr2 amd64 2:1.5.2-0ubuntu1 [18.5 kB]        
Get:89 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxv1 amd64 2:1.0.11-1 [10.7 kB]                  
Get:90 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxxf86dga1 amd64 2:1.1.5-0ubuntu1 [12.0 kB]      
Get:91 http://id.archive.ubuntu.com/ubuntu focal/main amd64 x11-utils amd64 7.7+5 [199 kB]                     
Get:92 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libatk-wrapper-java all 0.37.1-1 [53.0 kB]         
Get:93 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libatk-wrapper-java-jni amd64 0.37.1-1 [45.1 kB]   
Get:94 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgtk2.0-common all 2.24.32-4ubuntu4 [126 kB]     
Get:95 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcursor1 amd64 1:1.2.0-2 [20.1 kB]              
Get:96 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxdamage1 amd64 1:1.1.5-2 [6,996 B]              
Get:97 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgtk2.0-0 amd64 2.24.32-4ubuntu4 [1,791 kB]      
Get:98 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgail18 amd64 2.24.32-4ubuntu4 [14.7 kB]         
Get:99 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgail-common amd64 2.24.32-4ubuntu4 [116 kB]     
Get:100 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libgdk-pixbuf2.0-bin amd64 2.40.0+dfsg-3ubuntu0.4 [14.1 kB]
Get:101 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgif7 amd64 5.1.9-1 [32.2 kB]                   
Get:102 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libgtk2.0-bin amd64 2.24.32-4ubuntu4 [7,728 B]    
Get:103 http://id.archive.ubuntu.com/ubuntu focal/main amd64 xorg-sgml-doctools all 1:1.11-1 [12.9 kB]         
Get:104 http://id.archive.ubuntu.com/ubuntu focal/main amd64 x11proto-dev all 2019.2-1ubuntu1 [594 kB]         
Get:105 http://id.archive.ubuntu.com/ubuntu focal/main amd64 x11proto-core-dev all 2019.2-1ubuntu1 [2,620 B]   
Get:106 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libice-dev amd64 2:1.0.10-0ubuntu1 [47.8 kB]      
Get:107 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libpthread-stubs0-dev amd64 0.4-1 [5,384 B]       
Get:108 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libsm-dev amd64 2:1.2.3-1 [17.0 kB]               
Get:109 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libwayland-client0 amd64 1.18.0-1ubuntu0.1 [23.9 kB]
Get:110 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxau-dev amd64 1:1.0.9-0ubuntu1 [9,552 B]       
Get:111 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxdmcp-dev amd64 1:1.1.3-0ubuntu1 [25.3 kB]     
Get:112 http://id.archive.ubuntu.com/ubuntu focal/main amd64 xtrans-dev all 1.4.0-1 [68.9 kB]                  
Get:113 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb1-dev amd64 1.14-2 [80.5 kB]                
Get:114 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libx11-dev amd64 2:1.6.9-2ubuntu1.5 [647 kB]
Get:115 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxcb-randr0 amd64 1.14-2 [16.3 kB]              
Get:116 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libxt-dev amd64 1:1.1.5-1 [395 kB]                
Get:117 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 mesa-vulkan-drivers amd64 21.2.6-0ubuntu0.1~20.04.2 [5,788 kB]
Get:118 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 openjdk-17-jre amd64 17.0.7+7~us1-0ubuntu1~20.04 [183 kB]
Get:119 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 openjdk-17-jdk-headless amd64 17.0.7+7~us1-0ubuntu1~20.04 [71.2 MB]
Get:120 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 openjdk-17-jdk amd64 17.0.7+7~us1-0ubuntu1~20.04 [10.6 kB]
Fetched 170 MB in 30s (5,756 kB/s)                                                                             
Extracting templates from packages: 100%
Selecting previously unselected package hicolor-icon-theme.
(Reading database ... 115157 files and directories currently installed.)
Preparing to unpack .../000-hicolor-icon-theme_0.17-2_all.deb ...
Unpacking hicolor-icon-theme (0.17-2) ...
Selecting previously unselected package libjpeg-turbo8:amd64.
Preparing to unpack .../001-libjpeg-turbo8_2.0.3-0ubuntu1.20.04.3_amd64.deb ...
Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1.20.04.3) ...
Selecting previously unselected package libjpeg8:amd64.
Preparing to unpack .../002-libjpeg8_8c-2ubuntu8_amd64.deb ...
Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
Selecting previously unselected package libjbig0:amd64.
Preparing to unpack .../003-libjbig0_2.1-3.1ubuntu0.20.04.1_amd64.deb ...
Unpacking libjbig0:amd64 (2.1-3.1ubuntu0.20.04.1) ...
Selecting previously unselected package libwebp6:amd64.
Preparing to unpack .../004-libwebp6_0.6.1-2ubuntu0.20.04.2_amd64.deb ...
Unpacking libwebp6:amd64 (0.6.1-2ubuntu0.20.04.2) ...
Selecting previously unselected package libtiff5:amd64.
Preparing to unpack .../005-libtiff5_4.1.0+git191117-2ubuntu0.20.04.8_amd64.deb ...
Unpacking libtiff5:amd64 (4.1.0+git191117-2ubuntu0.20.04.8) ...
Selecting previously unselected package libgdk-pixbuf2.0-common.
Preparing to unpack .../006-libgdk-pixbuf2.0-common_2.40.0+dfsg-3ubuntu0.4_all.deb ...
Unpacking libgdk-pixbuf2.0-common (2.40.0+dfsg-3ubuntu0.4) ...
Selecting previously unselected package libgdk-pixbuf2.0-0:amd64.
Preparing to unpack .../007-libgdk-pixbuf2.0-0_2.40.0+dfsg-3ubuntu0.4_amd64.deb ...
Unpacking libgdk-pixbuf2.0-0:amd64 (2.40.0+dfsg-3ubuntu0.4) ...
Selecting previously unselected package gtk-update-icon-cache.
Preparing to unpack .../008-gtk-update-icon-cache_3.24.20-0ubuntu1.1_amd64.deb ...
No diversion 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin', none removed.
No diversion 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin', none removed.
Unpacking gtk-update-icon-cache (3.24.20-0ubuntu1.1) ...
Selecting previously unselected package fonts-dejavu-core.
Preparing to unpack .../009-fonts-dejavu-core_2.37-1_all.deb ...
Unpacking fonts-dejavu-core (2.37-1) ...
Selecting previously unselected package fontconfig-config.
Preparing to unpack .../010-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
Selecting previously unselected package libfontconfig1:amd64.
Preparing to unpack .../011-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
Selecting previously unselected package libpixman-1-0:amd64.
Preparing to unpack .../012-libpixman-1-0_0.38.4-0ubuntu2.1_amd64.deb ...
Unpacking libpixman-1-0:amd64 (0.38.4-0ubuntu2.1) ...
Selecting previously unselected package libxcb-render0:amd64.
Preparing to unpack .../013-libxcb-render0_1.14-2_amd64.deb ...
Unpacking libxcb-render0:amd64 (1.14-2) ...
Selecting previously unselected package libxcb-shm0:amd64.
Preparing to unpack .../014-libxcb-shm0_1.14-2_amd64.deb ...
Unpacking libxcb-shm0:amd64 (1.14-2) ...
Selecting previously unselected package libxrender1:amd64.
Preparing to unpack .../015-libxrender1_1%3a0.9.10-1_amd64.deb ...
Unpacking libxrender1:amd64 (1:0.9.10-1) ...
Selecting previously unselected package libcairo2:amd64.
Preparing to unpack .../016-libcairo2_1.16.0-4ubuntu1_amd64.deb ...
Unpacking libcairo2:amd64 (1.16.0-4ubuntu1) ...
Selecting previously unselected package libcairo-gobject2:amd64.
Preparing to unpack .../017-libcairo-gobject2_1.16.0-4ubuntu1_amd64.deb ...
Unpacking libcairo-gobject2:amd64 (1.16.0-4ubuntu1) ...
Selecting previously unselected package fontconfig.
Preparing to unpack .../018-fontconfig_2.13.1-2ubuntu3_amd64.deb ...
Unpacking fontconfig (2.13.1-2ubuntu3) ...
Selecting previously unselected package libgraphite2-3:amd64.
Preparing to unpack .../019-libgraphite2-3_1.3.13-11build1_amd64.deb ...
Unpacking libgraphite2-3:amd64 (1.3.13-11build1) ...
Selecting previously unselected package libharfbuzz0b:amd64.
Preparing to unpack .../020-libharfbuzz0b_2.6.4-1ubuntu4.2_amd64.deb ...
Unpacking libharfbuzz0b:amd64 (2.6.4-1ubuntu4.2) ...
Selecting previously unselected package libthai-data.
Preparing to unpack .../021-libthai-data_0.1.28-3_all.deb ...
Unpacking libthai-data (0.1.28-3) ...
Selecting previously unselected package libdatrie1:amd64.
Preparing to unpack .../022-libdatrie1_0.2.12-3_amd64.deb ...
Unpacking libdatrie1:amd64 (0.2.12-3) ...
Selecting previously unselected package libthai0:amd64.
Preparing to unpack .../023-libthai0_0.1.28-3_amd64.deb ...
Unpacking libthai0:amd64 (0.1.28-3) ...
Selecting previously unselected package libpango-1.0-0:amd64.
Preparing to unpack .../024-libpango-1.0-0_1.44.7-2ubuntu4_amd64.deb ...
Unpacking libpango-1.0-0:amd64 (1.44.7-2ubuntu4) ...
Selecting previously unselected package libpangoft2-1.0-0:amd64.
Preparing to unpack .../025-libpangoft2-1.0-0_1.44.7-2ubuntu4_amd64.deb ...
Unpacking libpangoft2-1.0-0:amd64 (1.44.7-2ubuntu4) ...
Selecting previously unselected package libpangocairo-1.0-0:amd64.
Preparing to unpack .../026-libpangocairo-1.0-0_1.44.7-2ubuntu4_amd64.deb ...
Unpacking libpangocairo-1.0-0:amd64 (1.44.7-2ubuntu4) ...
Selecting previously unselected package librsvg2-2:amd64.
Preparing to unpack .../027-librsvg2-2_2.48.9-1ubuntu0.20.04.1_amd64.deb ...
Unpacking librsvg2-2:amd64 (2.48.9-1ubuntu0.20.04.1) ...
Selecting previously unselected package librsvg2-common:amd64.
Preparing to unpack .../028-librsvg2-common_2.48.9-1ubuntu0.20.04.1_amd64.deb ...
Unpacking librsvg2-common:amd64 (2.48.9-1ubuntu0.20.04.1) ...
Selecting previously unselected package humanity-icon-theme.
Preparing to unpack .../029-humanity-icon-theme_0.6.15_all.deb ...
Unpacking humanity-icon-theme (0.6.15) ...
Selecting previously unselected package ubuntu-mono.
Preparing to unpack .../030-ubuntu-mono_19.04-0ubuntu3_all.deb ...
Unpacking ubuntu-mono (19.04-0ubuntu3) ...
Selecting previously unselected package adwaita-icon-theme.
Preparing to unpack .../031-adwaita-icon-theme_3.36.1-2ubuntu0.20.04.2_all.deb ...
Unpacking adwaita-icon-theme (3.36.1-2ubuntu0.20.04.2) ...
Selecting previously unselected package libatspi2.0-0:amd64.
Preparing to unpack .../032-libatspi2.0-0_2.36.0-2_amd64.deb ...
Unpacking libatspi2.0-0:amd64 (2.36.0-2) ...
Selecting previously unselected package x11-common.
Preparing to unpack .../033-x11-common_1%3a7.7+19ubuntu14_all.deb ...
dpkg-query: no packages found matching nux-tools
Unpacking x11-common (1:7.7+19ubuntu14) ...
Selecting previously unselected package libxtst6:amd64.
Preparing to unpack .../034-libxtst6_2%3a1.2.3-1_amd64.deb ...
Unpacking libxtst6:amd64 (2:1.2.3-1) ...
Selecting previously unselected package at-spi2-core.
Preparing to unpack .../035-at-spi2-core_2.36.0-2_amd64.deb ...
Unpacking at-spi2-core (2.36.0-2) ...
Selecting previously unselected package java-common.
Preparing to unpack .../036-java-common_0.72_all.deb ...
Unpacking java-common (0.72) ...
Selecting previously unselected package libavahi-common-data:amd64.
Preparing to unpack .../037-libavahi-common-data_0.7-4ubuntu7.2_amd64.deb ...
Unpacking libavahi-common-data:amd64 (0.7-4ubuntu7.2) ...
Selecting previously unselected package libavahi-common3:amd64.
Preparing to unpack .../038-libavahi-common3_0.7-4ubuntu7.2_amd64.deb ...
Unpacking libavahi-common3:amd64 (0.7-4ubuntu7.2) ...
Selecting previously unselected package libavahi-client3:amd64.
Preparing to unpack .../039-libavahi-client3_0.7-4ubuntu7.2_amd64.deb ...
Unpacking libavahi-client3:amd64 (0.7-4ubuntu7.2) ...
Selecting previously unselected package libcups2:amd64.
Preparing to unpack .../040-libcups2_2.3.1-9ubuntu1.4_amd64.deb ...
Unpacking libcups2:amd64 (2.3.1-9ubuntu1.4) ...
Selecting previously unselected package liblcms2-2:amd64.
Preparing to unpack .../041-liblcms2-2_2.9-4_amd64.deb ...
Unpacking liblcms2-2:amd64 (2.9-4) ...
Selecting previously unselected package libpcsclite1:amd64.
Preparing to unpack .../042-libpcsclite1_1.8.26-3_amd64.deb ...
Unpacking libpcsclite1:amd64 (1.8.26-3) ...
Selecting previously unselected package openjdk-17-jre-headless:amd64.
Preparing to unpack .../043-openjdk-17-jre-headless_17.0.7+7~us1-0ubuntu1~20.04_amd64.deb ...
Unpacking openjdk-17-jre-headless:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
Selecting previously unselected package ca-certificates-java.
Preparing to unpack .../044-ca-certificates-java_20190405ubuntu1.1_all.deb ...
Unpacking ca-certificates-java (20190405ubuntu1.1) ...
Selecting previously unselected package fonts-dejavu-extra.
Preparing to unpack .../045-fonts-dejavu-extra_2.37-1_all.deb ...
Unpacking fonts-dejavu-extra (2.37-1) ...
Selecting previously unselected package libatk1.0-data.
Preparing to unpack .../046-libatk1.0-data_2.35.1-1ubuntu2_all.deb ...
Unpacking libatk1.0-data (2.35.1-1ubuntu2) ...
Selecting previously unselected package libatk1.0-0:amd64.
Preparing to unpack .../047-libatk1.0-0_2.35.1-1ubuntu2_amd64.deb ...
Unpacking libatk1.0-0:amd64 (2.35.1-1ubuntu2) ...
Selecting previously unselected package libatk-bridge2.0-0:amd64.
Preparing to unpack .../048-libatk-bridge2.0-0_2.34.2-0ubuntu2~20.04.1_amd64.deb ...
Unpacking libatk-bridge2.0-0:amd64 (2.34.2-0ubuntu2~20.04.1) ...
Selecting previously unselected package libfontenc1:amd64.
Preparing to unpack .../049-libfontenc1_1%3a1.1.4-0ubuntu1_amd64.deb ...
Unpacking libfontenc1:amd64 (1:1.1.4-0ubuntu1) ...
Selecting previously unselected package libglvnd0:amd64.
Preparing to unpack .../050-libglvnd0_1.3.2-1~ubuntu0.20.04.2_amd64.deb ...
Unpacking libglvnd0:amd64 (1.3.2-1~ubuntu0.20.04.2) ...
Selecting previously unselected package libglapi-mesa:amd64.
Preparing to unpack .../051-libglapi-mesa_21.2.6-0ubuntu0.1~20.04.2_amd64.deb ...
Unpacking libglapi-mesa:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Selecting previously unselected package libx11-xcb1:amd64.
Preparing to unpack .../052-libx11-xcb1_2%3a1.6.9-2ubuntu1.5_amd64.deb ...
Unpacking libx11-xcb1:amd64 (2:1.6.9-2ubuntu1.5) ...
Selecting previously unselected package libxcb-dri2-0:amd64.
Preparing to unpack .../053-libxcb-dri2-0_1.14-2_amd64.deb ...
Unpacking libxcb-dri2-0:amd64 (1.14-2) ...
Selecting previously unselected package libxcb-dri3-0:amd64.
Preparing to unpack .../054-libxcb-dri3-0_1.14-2_amd64.deb ...
Unpacking libxcb-dri3-0:amd64 (1.14-2) ...
Selecting previously unselected package libxcb-glx0:amd64.
Preparing to unpack .../055-libxcb-glx0_1.14-2_amd64.deb ...
Unpacking libxcb-glx0:amd64 (1.14-2) ...
Selecting previously unselected package libxcb-present0:amd64.
Preparing to unpack .../056-libxcb-present0_1.14-2_amd64.deb ...
Unpacking libxcb-present0:amd64 (1.14-2) ...
Selecting previously unselected package libxcb-sync1:amd64.
Preparing to unpack .../057-libxcb-sync1_1.14-2_amd64.deb ...
Unpacking libxcb-sync1:amd64 (1.14-2) ...
Selecting previously unselected package libxcb-xfixes0:amd64.
Preparing to unpack .../058-libxcb-xfixes0_1.14-2_amd64.deb ...
Unpacking libxcb-xfixes0:amd64 (1.14-2) ...
Selecting previously unselected package libxfixes3:amd64.
Preparing to unpack .../059-libxfixes3_1%3a5.0.3-2_amd64.deb ...
Unpacking libxfixes3:amd64 (1:5.0.3-2) ...
Selecting previously unselected package libxshmfence1:amd64.
Preparing to unpack .../060-libxshmfence1_1.3-1_amd64.deb ...
Unpacking libxshmfence1:amd64 (1.3-1) ...
Selecting previously unselected package libxxf86vm1:amd64.
Preparing to unpack .../061-libxxf86vm1_1%3a1.1.4-1build1_amd64.deb ...
Unpacking libxxf86vm1:amd64 (1:1.1.4-1build1) ...
Selecting previously unselected package libdrm-amdgpu1:amd64.
Preparing to unpack .../062-libdrm-amdgpu1_2.4.107-8ubuntu1~20.04.2_amd64.deb ...
Unpacking libdrm-amdgpu1:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Selecting previously unselected package libpciaccess0:amd64.
Preparing to unpack .../063-libpciaccess0_0.16-0ubuntu1_amd64.deb ...
Unpacking libpciaccess0:amd64 (0.16-0ubuntu1) ...
Selecting previously unselected package libdrm-intel1:amd64.
Preparing to unpack .../064-libdrm-intel1_2.4.107-8ubuntu1~20.04.2_amd64.deb ...
Unpacking libdrm-intel1:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Selecting previously unselected package libdrm-nouveau2:amd64.
Preparing to unpack .../065-libdrm-nouveau2_2.4.107-8ubuntu1~20.04.2_amd64.deb ...
Unpacking libdrm-nouveau2:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Selecting previously unselected package libdrm-radeon1:amd64.
Preparing to unpack .../066-libdrm-radeon1_2.4.107-8ubuntu1~20.04.2_amd64.deb ...
Unpacking libdrm-radeon1:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Selecting previously unselected package libllvm12:amd64.
Preparing to unpack .../067-libllvm12_1%3a12.0.0-3ubuntu1~20.04.5_amd64.deb ...
Unpacking libllvm12:amd64 (1:12.0.0-3ubuntu1~20.04.5) ...
Selecting previously unselected package libsensors-config.
Preparing to unpack .../068-libsensors-config_1%3a3.6.0-2ubuntu1.1_all.deb ...
Unpacking libsensors-config (1:3.6.0-2ubuntu1.1) ...
Selecting previously unselected package libsensors5:amd64.
Preparing to unpack .../069-libsensors5_1%3a3.6.0-2ubuntu1.1_amd64.deb ...
Unpacking libsensors5:amd64 (1:3.6.0-2ubuntu1.1) ...
Selecting previously unselected package libvulkan1:amd64.
Preparing to unpack .../070-libvulkan1_1.2.131.2-1_amd64.deb ...
Unpacking libvulkan1:amd64 (1.2.131.2-1) ...
Selecting previously unselected package libgl1-mesa-dri:amd64.
Preparing to unpack .../071-libgl1-mesa-dri_21.2.6-0ubuntu0.1~20.04.2_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Selecting previously unselected package libglx-mesa0:amd64.
Preparing to unpack .../072-libglx-mesa0_21.2.6-0ubuntu0.1~20.04.2_amd64.deb ...
Unpacking libglx-mesa0:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Selecting previously unselected package libglx0:amd64.
Preparing to unpack .../073-libglx0_1.3.2-1~ubuntu0.20.04.2_amd64.deb ...
Unpacking libglx0:amd64 (1.3.2-1~ubuntu0.20.04.2) ...
Selecting previously unselected package libgl1:amd64.
Preparing to unpack .../074-libgl1_1.3.2-1~ubuntu0.20.04.2_amd64.deb ...
Unpacking libgl1:amd64 (1.3.2-1~ubuntu0.20.04.2) ...
Selecting previously unselected package libice6:amd64.
Preparing to unpack .../075-libice6_2%3a1.0.10-0ubuntu1_amd64.deb ...
Unpacking libice6:amd64 (2:1.0.10-0ubuntu1) ...
Selecting previously unselected package libsm6:amd64.
Preparing to unpack .../076-libsm6_2%3a1.2.3-1_amd64.deb ...
Unpacking libsm6:amd64 (2:1.2.3-1) ...
Selecting previously unselected package libxt6:amd64.
Preparing to unpack .../077-libxt6_1%3a1.1.5-1_amd64.deb ...
Unpacking libxt6:amd64 (1:1.1.5-1) ...
Selecting previously unselected package libxmu6:amd64.
Preparing to unpack .../078-libxmu6_2%3a1.1.3-0ubuntu1_amd64.deb ...
Unpacking libxmu6:amd64 (2:1.1.3-0ubuntu1) ...
Selecting previously unselected package libxpm4:amd64.
Preparing to unpack .../079-libxpm4_1%3a3.5.12-1ubuntu0.20.04.1_amd64.deb ...
Unpacking libxpm4:amd64 (1:3.5.12-1ubuntu0.20.04.1) ...
Selecting previously unselected package libxaw7:amd64.
Preparing to unpack .../080-libxaw7_2%3a1.0.13-1_amd64.deb ...
Unpacking libxaw7:amd64 (2:1.0.13-1) ...
Selecting previously unselected package libxcb-shape0:amd64.
Preparing to unpack .../081-libxcb-shape0_1.14-2_amd64.deb ...
Unpacking libxcb-shape0:amd64 (1.14-2) ...
Selecting previously unselected package libxcomposite1:amd64.
Preparing to unpack .../082-libxcomposite1_1%3a0.4.5-1_amd64.deb ...
Unpacking libxcomposite1:amd64 (1:0.4.5-1) ...
Selecting previously unselected package libxft2:amd64.
Preparing to unpack .../083-libxft2_2.3.3-0ubuntu1_amd64.deb ...
Unpacking libxft2:amd64 (2.3.3-0ubuntu1) ...
Selecting previously unselected package libxi6:amd64.
Preparing to unpack .../084-libxi6_2%3a1.7.10-0ubuntu1_amd64.deb ...
Unpacking libxi6:amd64 (2:1.7.10-0ubuntu1) ...
Selecting previously unselected package libxinerama1:amd64.
Preparing to unpack .../085-libxinerama1_2%3a1.1.4-2_amd64.deb ...
Unpacking libxinerama1:amd64 (2:1.1.4-2) ...
Selecting previously unselected package libxkbfile1:amd64.
Preparing to unpack .../086-libxkbfile1_1%3a1.1.0-1_amd64.deb ...
Unpacking libxkbfile1:amd64 (1:1.1.0-1) ...
Selecting previously unselected package libxrandr2:amd64.
Preparing to unpack .../087-libxrandr2_2%3a1.5.2-0ubuntu1_amd64.deb ...
Unpacking libxrandr2:amd64 (2:1.5.2-0ubuntu1) ...
Selecting previously unselected package libxv1:amd64.
Preparing to unpack .../088-libxv1_2%3a1.0.11-1_amd64.deb ...
Unpacking libxv1:amd64 (2:1.0.11-1) ...
Selecting previously unselected package libxxf86dga1:amd64.
Preparing to unpack .../089-libxxf86dga1_2%3a1.1.5-0ubuntu1_amd64.deb ...
Unpacking libxxf86dga1:amd64 (2:1.1.5-0ubuntu1) ...
Selecting previously unselected package x11-utils.
Preparing to unpack .../090-x11-utils_7.7+5_amd64.deb ...
Unpacking x11-utils (7.7+5) ...
Selecting previously unselected package libatk-wrapper-java.
Preparing to unpack .../091-libatk-wrapper-java_0.37.1-1_all.deb ...
Unpacking libatk-wrapper-java (0.37.1-1) ...
Selecting previously unselected package libatk-wrapper-java-jni:amd64.
Preparing to unpack .../092-libatk-wrapper-java-jni_0.37.1-1_amd64.deb ...
Unpacking libatk-wrapper-java-jni:amd64 (0.37.1-1) ...
Selecting previously unselected package libgtk2.0-common.
Preparing to unpack .../093-libgtk2.0-common_2.24.32-4ubuntu4_all.deb ...
Unpacking libgtk2.0-common (2.24.32-4ubuntu4) ...
Selecting previously unselected package libxcursor1:amd64.
Preparing to unpack .../094-libxcursor1_1%3a1.2.0-2_amd64.deb ...
Unpacking libxcursor1:amd64 (1:1.2.0-2) ...
Selecting previously unselected package libxdamage1:amd64.
Preparing to unpack .../095-libxdamage1_1%3a1.1.5-2_amd64.deb ...
Unpacking libxdamage1:amd64 (1:1.1.5-2) ...
Selecting previously unselected package libgtk2.0-0:amd64.
Preparing to unpack .../096-libgtk2.0-0_2.24.32-4ubuntu4_amd64.deb ...
Unpacking libgtk2.0-0:amd64 (2.24.32-4ubuntu4) ...
Selecting previously unselected package libgail18:amd64.
Preparing to unpack .../097-libgail18_2.24.32-4ubuntu4_amd64.deb ...
Unpacking libgail18:amd64 (2.24.32-4ubuntu4) ...
Selecting previously unselected package libgail-common:amd64.
Preparing to unpack .../098-libgail-common_2.24.32-4ubuntu4_amd64.deb ...
Unpacking libgail-common:amd64 (2.24.32-4ubuntu4) ...
Selecting previously unselected package libgdk-pixbuf2.0-bin.
Preparing to unpack .../099-libgdk-pixbuf2.0-bin_2.40.0+dfsg-3ubuntu0.4_amd64.deb ...
Unpacking libgdk-pixbuf2.0-bin (2.40.0+dfsg-3ubuntu0.4) ...
Selecting previously unselected package libgif7:amd64.
Preparing to unpack .../100-libgif7_5.1.9-1_amd64.deb ...
Unpacking libgif7:amd64 (5.1.9-1) ...
Selecting previously unselected package libgtk2.0-bin.
Preparing to unpack .../101-libgtk2.0-bin_2.24.32-4ubuntu4_amd64.deb ...
Unpacking libgtk2.0-bin (2.24.32-4ubuntu4) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../102-xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-dev.
Preparing to unpack .../103-x11proto-dev_2019.2-1ubuntu1_all.deb ...
Unpacking x11proto-dev (2019.2-1ubuntu1) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../104-x11proto-core-dev_2019.2-1ubuntu1_all.deb ...
Unpacking x11proto-core-dev (2019.2-1ubuntu1) ...
Selecting previously unselected package libice-dev:amd64.
Preparing to unpack .../105-libice-dev_2%3a1.0.10-0ubuntu1_amd64.deb ...
Unpacking libice-dev:amd64 (2:1.0.10-0ubuntu1) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Preparing to unpack .../106-libpthread-stubs0-dev_0.4-1_amd64.deb ...
Unpacking libpthread-stubs0-dev:amd64 (0.4-1) ...
Selecting previously unselected package libsm-dev:amd64.
Preparing to unpack .../107-libsm-dev_2%3a1.2.3-1_amd64.deb ...
Unpacking libsm-dev:amd64 (2:1.2.3-1) ...
Selecting previously unselected package libwayland-client0:amd64.
Preparing to unpack .../108-libwayland-client0_1.18.0-1ubuntu0.1_amd64.deb ...
Unpacking libwayland-client0:amd64 (1.18.0-1ubuntu0.1) ...
Selecting previously unselected package libxau-dev:amd64.
Preparing to unpack .../109-libxau-dev_1%3a1.0.9-0ubuntu1_amd64.deb ...
Unpacking libxau-dev:amd64 (1:1.0.9-0ubuntu1) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Preparing to unpack .../110-libxdmcp-dev_1%3a1.1.3-0ubuntu1_amd64.deb ...
Unpacking libxdmcp-dev:amd64 (1:1.1.3-0ubuntu1) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../111-xtrans-dev_1.4.0-1_all.deb ...
Unpacking xtrans-dev (1.4.0-1) ...
Selecting previously unselected package libxcb1-dev:amd64.
Preparing to unpack .../112-libxcb1-dev_1.14-2_amd64.deb ...
Unpacking libxcb1-dev:amd64 (1.14-2) ...
Selecting previously unselected package libx11-dev:amd64.
Preparing to unpack .../113-libx11-dev_2%3a1.6.9-2ubuntu1.5_amd64.deb ...
Unpacking libx11-dev:amd64 (2:1.6.9-2ubuntu1.5) ...
Selecting previously unselected package libxcb-randr0:amd64.
Preparing to unpack .../114-libxcb-randr0_1.14-2_amd64.deb ...
Unpacking libxcb-randr0:amd64 (1.14-2) ...
Selecting previously unselected package libxt-dev:amd64.
Preparing to unpack .../115-libxt-dev_1%3a1.1.5-1_amd64.deb ...
Unpacking libxt-dev:amd64 (1:1.1.5-1) ...
Selecting previously unselected package mesa-vulkan-drivers:amd64.
Preparing to unpack .../116-mesa-vulkan-drivers_21.2.6-0ubuntu0.1~20.04.2_amd64.deb ...
Unpacking mesa-vulkan-drivers:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Selecting previously unselected package openjdk-17-jre:amd64.
Preparing to unpack .../117-openjdk-17-jre_17.0.7+7~us1-0ubuntu1~20.04_amd64.deb ...
Unpacking openjdk-17-jre:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
Selecting previously unselected package openjdk-17-jdk-headless:amd64.
Preparing to unpack .../118-openjdk-17-jdk-headless_17.0.7+7~us1-0ubuntu1~20.04_amd64.deb ...
Unpacking openjdk-17-jdk-headless:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
Selecting previously unselected package openjdk-17-jdk:amd64.
Preparing to unpack .../119-openjdk-17-jdk_17.0.7+7~us1-0ubuntu1~20.04_amd64.deb ...
Unpacking openjdk-17-jdk:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
Setting up libgraphite2-3:amd64 (1.3.13-11build1) ...
Setting up libxcb-dri3-0:amd64 (1.14-2) ...
Setting up liblcms2-2:amd64 (2.9-4) ...
Setting up libpixman-1-0:amd64 (0.38.4-0ubuntu2.1) ...
Setting up libx11-xcb1:amd64 (2:1.6.9-2ubuntu1.5) ...
Setting up libpciaccess0:amd64 (0.16-0ubuntu1) ...
Setting up libdrm-nouveau2:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Setting up libxdamage1:amd64 (1:1.1.5-2) ...
Setting up libxcb-xfixes0:amd64 (1.14-2) ...
Setting up libxpm4:amd64 (1:3.5.12-1ubuntu0.20.04.1) ...
Setting up hicolor-icon-theme (0.17-2) ...
Setting up libxi6:amd64 (2:1.7.10-0ubuntu1) ...
Setting up java-common (0.72) ...
Setting up libxrender1:amd64 (1:0.9.10-1) ...
Setting up libdatrie1:amd64 (0.2.12-3) ...
Setting up libxcb-render0:amd64 (1.14-2) ...
Setting up libdrm-radeon1:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Setting up libglvnd0:amd64 (1.3.2-1~ubuntu0.20.04.2) ...
Setting up libxcb-glx0:amd64 (1.14-2) ...
Setting up libdrm-intel1:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Setting up libgdk-pixbuf2.0-common (2.40.0+dfsg-3ubuntu0.4) ...
Setting up libxcb-shape0:amd64 (1.14-2) ...
Setting up x11-common (1:7.7+19ubuntu14) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up libsensors-config (1:3.6.0-2ubuntu1.1) ...
Setting up libxxf86dga1:amd64 (2:1.1.5-0ubuntu1) ...
Setting up libxcb-shm0:amd64 (1.14-2) ...
Setting up libatspi2.0-0:amd64 (2.36.0-2) ...
Setting up libpthread-stubs0-dev:amd64 (0.4-1) ...
Setting up libjbig0:amd64 (2.1-3.1ubuntu0.20.04.1) ...
Setting up libxxf86vm1:amd64 (1:1.1.4-1build1) ...
Setting up libxcb-present0:amd64 (1.14-2) ...
Setting up xtrans-dev (1.4.0-1) ...
Setting up libfontenc1:amd64 (1:1.1.4-0ubuntu1) ...
Setting up libxfixes3:amd64 (1:5.0.3-2) ...
Setting up libxcb-sync1:amd64 (1.14-2) ...
Setting up libavahi-common-data:amd64 (0.7-4ubuntu7.2) ...
Setting up libllvm12:amd64 (1:12.0.0-3ubuntu1~20.04.5) ...
Setting up libxinerama1:amd64 (2:1.1.4-2) ...
Setting up libxv1:amd64 (2:1.0.11-1) ...
Setting up libxrandr2:amd64 (2:1.5.2-0ubuntu1) ...
Setting up libwebp6:amd64 (0.6.1-2ubuntu0.20.04.2) ...
Setting up fonts-dejavu-core (2.37-1) ...
Setting up libpcsclite1:amd64 (1.8.26-3) ...
Setting up libsensors5:amd64 (1:3.6.0-2ubuntu1.1) ...
Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1.20.04.3) ...
Setting up libglapi-mesa:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Setting up libvulkan1:amd64 (1.2.131.2-1) ...
Setting up libxcb-dri2-0:amd64 (1.14-2) ...
Setting up libgif7:amd64 (5.1.9-1) ...
Setting up libatk1.0-data (2.35.1-1ubuntu2) ...
Setting up fonts-dejavu-extra (2.37-1) ...
Setting up libxshmfence1:amd64 (1.3-1) ...
Setting up libxcb-randr0:amd64 (1.14-2) ...
Setting up libharfbuzz0b:amd64 (2.6.4-1ubuntu4.2) ...
Setting up libthai-data (0.1.28-3) ...
Setting up xorg-sgml-doctools (1:1.11-1) ...
Setting up libgtk2.0-common (2.24.32-4ubuntu4) ...
Setting up libatk1.0-0:amd64 (2.35.1-1ubuntu2) ...
Setting up libxkbfile1:amd64 (1:1.1.0-1) ...
Setting up libxcomposite1:amd64 (1:0.4.5-1) ...
Setting up libdrm-amdgpu1:amd64 (2.4.107-8ubuntu1~20.04.2) ...
Setting up libwayland-client0:amd64 (1.18.0-1ubuntu0.1) ...
Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
Setting up x11proto-dev (2019.2-1ubuntu1) ...
Setting up mesa-vulkan-drivers:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Setting up libice6:amd64 (2:1.0.10-0ubuntu1) ...
Setting up libxau-dev:amd64 (1:1.0.9-0ubuntu1) ...
Setting up libice-dev:amd64 (2:1.0.10-0ubuntu1) ...
Setting up fontconfig-config (2.13.1-2ubuntu3) ...
Setting up libxtst6:amd64 (2:1.2.3-1) ...
Setting up libxcursor1:amd64 (1:1.2.0-2) ...
Setting up libgl1-mesa-dri:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Setting up libavahi-common3:amd64 (0.7-4ubuntu7.2) ...
Setting up libatk-bridge2.0-0:amd64 (2.34.2-0ubuntu2~20.04.1) ...
Setting up libthai0:amd64 (0.1.28-3) ...
Setting up libxdmcp-dev:amd64 (1:1.1.3-0ubuntu1) ...
Setting up x11proto-core-dev (2019.2-1ubuntu1) ...
Setting up at-spi2-core (2.36.0-2) ...
Setting up libtiff5:amd64 (4.1.0+git191117-2ubuntu0.20.04.8) ...
Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
Setting up libsm6:amd64 (2:1.2.3-1) ...
Setting up libavahi-client3:amd64 (0.7-4ubuntu7.2) ...
Setting up fontconfig (2.13.1-2ubuntu3) ...
Regenerating fonts cache... done.
Setting up libxft2:amd64 (2.3.3-0ubuntu1) ...
Setting up libglx-mesa0:amd64 (21.2.6-0ubuntu0.1~20.04.2) ...
Setting up libxcb1-dev:amd64 (1.14-2) ...
Setting up libglx0:amd64 (1.3.2-1~ubuntu0.20.04.2) ...
Setting up libsm-dev:amd64 (2:1.2.3-1) ...
Setting up libpango-1.0-0:amd64 (1.44.7-2ubuntu4) ...
Setting up libx11-dev:amd64 (2:1.6.9-2ubuntu1.5) ...
Setting up libcairo2:amd64 (1.16.0-4ubuntu1) ...
Setting up libgl1:amd64 (1.3.2-1~ubuntu0.20.04.2) ...
Setting up libgdk-pixbuf2.0-0:amd64 (2.40.0+dfsg-3ubuntu0.4) ...
Setting up libxt6:amd64 (1:1.1.5-1) ...
Setting up libcups2:amd64 (2.3.1-9ubuntu1.4) ...
Setting up libgdk-pixbuf2.0-bin (2.40.0+dfsg-3ubuntu0.4) ...
Setting up libcairo-gobject2:amd64 (1.16.0-4ubuntu1) ...
Setting up libpangoft2-1.0-0:amd64 (1.44.7-2ubuntu4) ...
Setting up libpangocairo-1.0-0:amd64 (1.44.7-2ubuntu4) ...
Setting up gtk-update-icon-cache (3.24.20-0ubuntu1.1) ...
Setting up libxmu6:amd64 (2:1.1.3-0ubuntu1) ...
Setting up libxaw7:amd64 (2:1.0.13-1) ...
Setting up librsvg2-2:amd64 (2.48.9-1ubuntu0.20.04.1) ...
Setting up libxt-dev:amd64 (1:1.1.5-1) ...
Setting up librsvg2-common:amd64 (2.48.9-1ubuntu0.20.04.1) ...
Setting up x11-utils (7.7+5) ...
Setting up libatk-wrapper-java (0.37.1-1) ...
Setting up libatk-wrapper-java-jni:amd64 (0.37.1-1) ...
Setting up openjdk-17-jre-headless:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jpackage to provide /usr/bin/jpackage (jpackage) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
Setting up ca-certificates-java (20190405ubuntu1.1) ...
head: cannot open '/etc/ssl/certs/java/cacerts' for reading: No such file or directory
Adding debian:AffirmTrust_Networking.pem
Adding debian:DigiCert_Global_Root_G3.pem
Adding debian:E-Tugra_Certification_Authority.pem
Adding debian:ANF_Secure_Server_Root_CA.pem
Adding debian:SZAFIR_ROOT_CA2.pem
Adding debian:GDCA_TrustAUTH_R5_ROOT.pem
Adding debian:AC_RAIZ_FNMT-RCM.pem
Adding debian:SSL.com_Root_Certification_Authority_ECC.pem
Adding debian:Entrust_Root_Certification_Authority_-_G4.pem
Adding debian:ISRG_Root_X1.pem
Adding debian:AffirmTrust_Premium_ECC.pem
Adding debian:Baltimore_CyberTrust_Root.pem
Adding debian:E-Tugra_Global_Root_CA_RSA_v3.pem
Adding debian:QuoVadis_Root_CA_3.pem
Adding debian:Buypass_Class_3_Root_CA.pem
Adding debian:XRamp_Global_CA_Root.pem
Adding debian:HiPKI_Root_CA_-_G1.pem
Adding debian:SecureTrust_CA.pem
Adding debian:Comodo_AAA_Services_root.pem
Adding debian:UCA_Extended_Validation_Root.pem
Adding debian:Buypass_Class_2_Root_CA.pem
Adding debian:T-TeleSec_GlobalRoot_Class_2.pem
Adding debian:vTrus_ECC_Root_CA.pem
Adding debian:emSign_ECC_Root_CA_-_C3.pem
Adding debian:Amazon_Root_CA_2.pem
Adding debian:vTrus_Root_CA.pem
Adding debian:CFCA_EV_ROOT.pem
Adding debian:Entrust.net_Premium_2048_Secure_Server_CA.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068.pem
Adding debian:QuoVadis_Root_CA_3_G3.pem
Adding debian:Secure_Global_CA.pem
Adding debian:Security_Communication_Root_CA.pem
Adding debian:Trustwave_Global_ECC_P256_Certification_Authority.pem
Adding debian:TunTrust_Root_CA.pem
Adding debian:Hongkong_Post_Root_CA_1.pem
Adding debian:GlobalSign_Root_E46.pem
Adding debian:Certum_EC-384_CA.pem
Adding debian:TeliaSonera_Root_CA_v1.pem
Adding debian:T-TeleSec_GlobalRoot_Class_3.pem
Adding debian:DigiCert_TLS_ECC_P384_Root_G5.pem
Adding debian:GlobalSign_ECC_Root_CA_-_R4.pem
Adding debian:GlobalSign_Root_CA.pem
Adding debian:SecureSign_RootCA11.pem
Adding debian:Hongkong_Post_Root_CA_3.pem
Adding debian:DigiCert_Global_Root_G2.pem
Adding debian:GTS_Root_R2.pem
Adding debian:Security_Communication_RootCA2.pem
Adding debian:COMODO_Certification_Authority.pem
Adding debian:GlobalSign_Root_R46.pem
Adding debian:DigiCert_High_Assurance_EV_Root_CA.pem
Adding debian:AffirmTrust_Commercial.pem
Adding debian:Go_Daddy_Root_Certificate_Authority_-_G2.pem
Adding debian:Certum_Trusted_Network_CA.pem
Adding debian:OISTE_WISeKey_Global_Root_GC_CA.pem
Adding debian:GTS_Root_R1.pem
Adding debian:Amazon_Root_CA_4.pem
Adding debian:CA_Disig_Root_R2.pem
Adding debian:DigiCert_Assured_ID_Root_G2.pem
Adding debian:Telia_Root_CA_v2.pem
Adding debian:DigiCert_Global_Root_CA.pem
Adding debian:Certum_Trusted_Network_CA_2.pem
Adding debian:UCA_Global_G2_Root.pem
Adding debian:emSign_ECC_Root_CA_-_G3.pem
Adding debian:Entrust_Root_Certification_Authority_-_G2.pem
Adding debian:Actalis_Authentication_Root_CA.pem
Adding debian:E-Tugra_Global_Root_CA_ECC_v3.pem
Adding debian:Starfield_Root_Certificate_Authority_-_G2.pem
Adding debian:USERTrust_RSA_Certification_Authority.pem
Adding debian:Microsoft_RSA_Root_Certificate_Authority_2017.pem
Adding debian:Go_Daddy_Class_2_CA.pem
Adding debian:Trustwave_Global_ECC_P384_Certification_Authority.pem
Adding debian:Certigna_Root_CA.pem
Adding debian:ISRG_Root_X2.pem
Adding debian:ACCVRAIZ1.pem
Adding debian:SSL.com_Root_Certification_Authority_RSA.pem
Adding debian:Trustwave_Global_Certification_Authority.pem
Adding debian:GlobalSign_Root_CA_-_R3.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068_2.pem
Adding debian:TUBITAK_Kamu_SM_SSL_Kok_Sertifikasi_-_Surum_1.pem
Adding debian:D-TRUST_BR_Root_CA_1_2020.pem
Adding debian:QuoVadis_Root_CA_2_G3.pem
Adding debian:NetLock_Arany_=Class_Gold=_Főtanúsítvány.pem
Adding debian:SwissSign_Silver_CA_-_G2.pem
Adding debian:Hellenic_Academic_and_Research_Institutions_ECC_RootCA_2015.pem
Adding debian:ePKI_Root_Certification_Authority.pem
Adding debian:Microsec_e-Szigno_Root_CA_2009.pem
Adding debian:Security_Communication_RootCA3.pem
Adding debian:AC_RAIZ_FNMT-RCM_SERVIDORES_SEGUROS.pem
Adding debian:emSign_Root_CA_-_C1.pem
Adding debian:COMODO_ECC_Certification_Authority.pem
Adding debian:certSIGN_Root_CA_G2.pem
Adding debian:D-TRUST_EV_Root_CA_1_2020.pem
Adding debian:Atos_TrustedRoot_2011.pem
Adding debian:GTS_Root_R3.pem
Adding debian:emSign_Root_CA_-_G1.pem
Adding debian:DigiCert_Assured_ID_Root_CA.pem
Adding debian:DigiCert_TLS_RSA4096_Root_G5.pem
Adding debian:e-Szigno_Root_CA_2017.pem
Adding debian:DigiCert_Trusted_Root_G4.pem
Adding debian:QuoVadis_Root_CA_1_G3.pem
Adding debian:GTS_Root_R4.pem
Adding debian:D-TRUST_Root_Class_3_CA_2_EV_2009.pem
Adding debian:Izenpe.com.pem
Adding debian:Entrust_Root_Certification_Authority_-_EC1.pem
Adding debian:HARICA_TLS_ECC_Root_CA_2021.pem
Adding debian:GlobalSign_ECC_Root_CA_-_R5.pem
Adding debian:Entrust_Root_Certification_Authority.pem
Adding debian:Certum_Trusted_Root_CA.pem
Adding debian:Starfield_Class_2_CA.pem
Adding debian:IdenTrust_Commercial_Root_CA_1.pem
Adding debian:COMODO_RSA_Certification_Authority.pem
Adding debian:OISTE_WISeKey_Global_Root_GB_CA.pem
Adding debian:SwissSign_Gold_CA_-_G2.pem
Adding debian:Certainly_Root_R1.pem
Adding debian:Security_Communication_ECC_RootCA1.pem
Adding debian:certSIGN_ROOT_CA.pem
Adding debian:Certainly_Root_E1.pem
Adding debian:D-TRUST_Root_Class_3_CA_2_2009.pem
Adding debian:TWCA_Root_Certification_Authority.pem
Adding debian:IdenTrust_Public_Sector_Root_CA_1.pem
Adding debian:NAVER_Global_Root_Certification_Authority.pem
Adding debian:HARICA_TLS_RSA_Root_CA_2021.pem
Adding debian:Amazon_Root_CA_1.pem
Adding debian:Amazon_Root_CA_3.pem
Adding debian:Starfield_Services_Root_Certificate_Authority_-_G2.pem
Adding debian:AffirmTrust_Premium.pem
Adding debian:GLOBALTRUST_2020.pem
Adding debian:SSL.com_EV_Root_Certification_Authority_ECC.pem
Adding debian:USERTrust_ECC_Certification_Authority.pem
Adding debian:Microsoft_ECC_Root_Certificate_Authority_2017.pem
Adding debian:SSL.com_EV_Root_Certification_Authority_RSA_R2.pem
Adding debian:QuoVadis_Root_CA_2.pem
Adding debian:DigiCert_Assured_ID_Root_G3.pem
Adding debian:TWCA_Global_Root_CA.pem
Adding debian:Hellenic_Academic_and_Research_Institutions_RootCA_2015.pem
Adding debian:GlobalSign_Root_CA_-_R6.pem
Adding debian:Certigna.pem
done.
Setting up adwaita-icon-theme (3.36.1-2ubuntu0.20.04.2) ...
update-alternatives: using /usr/share/icons/Adwaita/cursor.theme to provide /usr/share/icons/default/index.theme (x-cursor-theme) in auto mode
Setting up openjdk-17-jdk-headless:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jar to provide /usr/bin/jar (jar) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/javap to provide /usr/bin/javap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jdeprscan to provide /usr/bin/jdeprscan (jdeprscan) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jdeps to provide /usr/bin/jdeps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jfr to provide /usr/bin/jfr (jfr) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jimage to provide /usr/bin/jimage (jimage) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jlink to provide /usr/bin/jlink (jlink) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jmod to provide /usr/bin/jmod (jmod) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jps to provide /usr/bin/jps (jps) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jshell to provide /usr/bin/jshell (jshell) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jhsdb to provide /usr/bin/jhsdb (jhsdb) in auto mode
Setting up libgtk2.0-0:amd64 (2.24.32-4ubuntu4) ...
Setting up humanity-icon-theme (0.6.15) ...
Setting up libgail18:amd64 (2.24.32-4ubuntu4) ...
Setting up libgtk2.0-bin (2.24.32-4ubuntu4) ...
Setting up libgail-common:amd64 (2.24.32-4ubuntu4) ...
Setting up openjdk-17-jre:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
Setting up ubuntu-mono (19.04-0ubuntu3) ...
Setting up openjdk-17-jdk:amd64 (17.0.7+7~us1-0ubuntu1~20.04) ...
update-alternatives: using /usr/lib/jvm/java-17-openjdk-amd64/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
Processing triggers for ca-certificates (20230311ubuntu0.20.04.1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

done.
done.
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
Processing triggers for systemd (245.4-4ubuntu3.20) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libgdk-pixbuf2.0-0:amd64 (2.40.0+dfsg-3ubuntu0.4) ...
root@devops:/home/ubuntu# cd
root@devops:~# sudo update-alternatives --config java
There is only one alternative in link group java (providing /usr/bin/java): /usr/lib/jvm/java-17-openjdk-amd64/bin/java
Nothing to configure.
root@devops:~#
```

masukan repo postgres

```bash
root@devops:~# sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
root@devops:~# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
OK
root@devops:~# sudo apt-get update
Hit:1 https://deb.nodesource.com/node_18.x focal InRelease
Get:2 http://apt.postgresql.org/pub/repos/apt focal-pgdg InRelease [123 kB]
Hit:3 http://id.archive.ubuntu.com/ubuntu focal InRelease
Get:4 http://id.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:5 http://id.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:6 http://id.archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:7 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [2,718 kB]
Get:8 http://id.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [452 kB]
Get:9 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [16.9 kB]
Get:10 http://id.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [2,140 kB]
Get:11 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 Packages [273 kB]
Get:12 http://id.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [299 kB]          
Get:13 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1,091 kB]             
Get:14 http://id.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [260 kB]          
Get:15 http://id.archive.ubuntu.com/ubuntu focal-security/main amd64 Packages [2,304 kB]
Get:16 http://id.archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages [859 kB]
Get:17 http://id.archive.ubuntu.com/ubuntu focal-security/universe Translation-en [179 kB]
Fetched 11.1 MB in 4s (2,721 kB/s)                                     
Reading package lists... Done
root@devops:~# sudo apt-get -y install postgresql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 libxmlb1
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libcommon-sense-perl libjson-perl libjson-xs-perl libllvm10 libpq5 libtypes-serialiser-perl postgresql-15
  postgresql-client-15 postgresql-client-common postgresql-common ssl-cert sysstat
Suggested packages:
  postgresql-doc postgresql-doc-15 openssl-blacklist isag
The following NEW packages will be installed:
  libcommon-sense-perl libjson-perl libjson-xs-perl libllvm10 libpq5 libtypes-serialiser-perl postgresql
  postgresql-15 postgresql-client-15 postgresql-client-common postgresql-common ssl-cert sysstat
0 upgraded, 13 newly installed, 0 to remove and 66 not upgraded.
Need to get 34.5 MB of archives.
After this operation, 139 MB of additional disk space will be used.
Get:1 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libjson-perl all 4.02000-2 [80.9 kB]
Get:2 http://id.archive.ubuntu.com/ubuntu focal/main amd64 ssl-cert all 1.0.39 [17.0 kB]   
Get:3 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libcommon-sense-perl amd64 3.74-2build6 [20.1 kB]
Get:4 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libtypes-serialiser-perl all 1.0-1 [12.1 kB]
Get:5 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libjson-xs-perl amd64 4.020-1build1 [83.7 kB]
Get:6 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libllvm10 amd64 1:10.0.0-4ubuntu1 [15.3 MB]
Get:7 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 postgresql-client-common all 250.pgdg20.04+1 [93.3 kB]
Get:8 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 postgresql-common all 250.pgdg20.04+1 [239 kB]
Get:9 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 sysstat amd64 12.2.0-2ubuntu0.3 [448 kB]
Get:10 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 libpq5 amd64 15.3-1.pgdg20.04+1 [184 kB]
Get:11 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 postgresql-client-15 amd64 15.3-1.pgdg20.04+1 [1,680 kB]
Get:12 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 postgresql-15 amd64 15.3-1.pgdg20.04+1 [16.3 MB]
Get:13 http://apt.postgresql.org/pub/repos/apt focal-pgdg/main amd64 postgresql all 15+250.pgdg20.04+1 [68.2 kB]
Fetched 34.5 MB in 17s (2,061 kB/s)                                                                            
Preconfiguring packages ...
Selecting previously unselected package libjson-perl.
(Reading database ... 130815 files and directories currently installed.)
Preparing to unpack .../00-libjson-perl_4.02000-2_all.deb ...
Unpacking libjson-perl (4.02000-2) ...
Selecting previously unselected package postgresql-client-common.
Preparing to unpack .../01-postgresql-client-common_250.pgdg20.04+1_all.deb ...
Unpacking postgresql-client-common (250.pgdg20.04+1) ...
Selecting previously unselected package ssl-cert.
Preparing to unpack .../02-ssl-cert_1.0.39_all.deb ...
Unpacking ssl-cert (1.0.39) ...
Selecting previously unselected package postgresql-common.
Preparing to unpack .../03-postgresql-common_250.pgdg20.04+1_all.deb ...
Adding 'diversion of /usr/bin/pg_config to /usr/bin/pg_config.libpq-dev by postgresql-common'
Unpacking postgresql-common (250.pgdg20.04+1) ...
Selecting previously unselected package libcommon-sense-perl.
Preparing to unpack .../04-libcommon-sense-perl_3.74-2build6_amd64.deb ...
Unpacking libcommon-sense-perl (3.74-2build6) ...
Selecting previously unselected package libtypes-serialiser-perl.
Preparing to unpack .../05-libtypes-serialiser-perl_1.0-1_all.deb ...
Unpacking libtypes-serialiser-perl (1.0-1) ...
Selecting previously unselected package libjson-xs-perl.
Preparing to unpack .../06-libjson-xs-perl_4.020-1build1_amd64.deb ...
Unpacking libjson-xs-perl (4.020-1build1) ...
Selecting previously unselected package libllvm10:amd64.
Preparing to unpack .../07-libllvm10_1%3a10.0.0-4ubuntu1_amd64.deb ...
Unpacking libllvm10:amd64 (1:10.0.0-4ubuntu1) ...
Selecting previously unselected package libpq5:amd64.
Preparing to unpack .../08-libpq5_15.3-1.pgdg20.04+1_amd64.deb ...
Unpacking libpq5:amd64 (15.3-1.pgdg20.04+1) ...
Selecting previously unselected package postgresql-client-15.
Preparing to unpack .../09-postgresql-client-15_15.3-1.pgdg20.04+1_amd64.deb ...
Unpacking postgresql-client-15 (15.3-1.pgdg20.04+1) ...
Selecting previously unselected package postgresql-15.
Preparing to unpack .../10-postgresql-15_15.3-1.pgdg20.04+1_amd64.deb ...
Unpacking postgresql-15 (15.3-1.pgdg20.04+1) ...
Selecting previously unselected package postgresql.
Preparing to unpack .../11-postgresql_15+250.pgdg20.04+1_all.deb ...
Unpacking postgresql (15+250.pgdg20.04+1) ...
Selecting previously unselected package sysstat.
Preparing to unpack .../12-sysstat_12.2.0-2ubuntu0.3_amd64.deb ...
Unpacking sysstat (12.2.0-2ubuntu0.3) ...
Setting up postgresql-client-common (250.pgdg20.04+1) ...
Setting up libpq5:amd64 (15.3-1.pgdg20.04+1) ...
Setting up libcommon-sense-perl (3.74-2build6) ...
Setting up postgresql-client-15 (15.3-1.pgdg20.04+1) ...
update-alternatives: using /usr/share/postgresql/15/man/man1/psql.1.gz to provide /usr/share/man/man1/psql.1.gz (psql.1.gz) in auto mode
Setting up libllvm10:amd64 (1:10.0.0-4ubuntu1) ...
Setting up ssl-cert (1.0.39) ...
Setting up libtypes-serialiser-perl (1.0-1) ...
Setting up libjson-perl (4.02000-2) ...
Setting up sysstat (12.2.0-2ubuntu0.3) ...

Creating config file /etc/default/sysstat with new version
update-alternatives: using /usr/bin/sar.sysstat to provide /usr/bin/sar (sar) in auto mode
Created symlink /etc/systemd/system/multi-user.target.wants/sysstat.service → /lib/systemd/system/sysstat.service.
Setting up libjson-xs-perl (4.020-1build1) ...
Setting up postgresql-common (250.pgdg20.04+1) ...
Adding user postgres to group ssl-cert

Creating config file /etc/postgresql-common/createcluster.conf with new version
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
Removing obsolete dictionary files:
'/etc/apt/trusted.gpg.d/apt.postgresql.org.gpg' -> '/usr/share/postgresql-common/pgdg/apt.postgresql.org.gpg'
Created symlink /etc/systemd/system/multi-user.target.wants/postgresql.service → /lib/systemd/system/postgresql.service.
Setting up postgresql-15 (15.3-1.pgdg20.04+1) ...
Creating new PostgreSQL cluster 15/main ...
/usr/lib/postgresql/15/bin/initdb -D /var/lib/postgresql/15/main --auth-local peer --auth-host scram-sha-256 --no-instructions
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.UTF-8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/15/main ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... Asia/Jakarta
creating configuration files ... ok
running bootstrap script ... ok
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
Setting up postgresql (15+250.pgdg20.04+1) ...
Processing triggers for systemd (245.4-4ubuntu3.20) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
root@devops:~#
```

Tuning Performance Sonarqube

<aside>
💡 root@devops:~# vim /etc/sysctl.d/99-sonarqube.conf

</aside>

```bash
vm.max_map_count=524288
*fs.file-max=131*072
```

atur penggunaan sumber daya

```bash
root@devops:~# ulimit -n 131072
root@devops:~# ulimit -u 8192
root@devops:~# vim /etc/security/limits.d/99-sonarqube.conf
sonarqube   -   nofile   131072
sonarqube   -   nproc    8192

```

```bash
root@devops:~# sysctl --system
* Applying /etc/sysctl.d/10-console-messages.conf ...
kernel.printk = 4 4 1 7
* Applying /etc/sysctl.d/10-ipv6-privacy.conf ...
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.use_tempaddr = 2
* Applying /etc/sysctl.d/10-kernel-hardening.conf ...
kernel.kptr_restrict = 1
* Applying /etc/sysctl.d/10-link-restrictions.conf ...
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
* Applying /etc/sysctl.d/10-magic-sysrq.conf ...
kernel.sysrq = 176
* Applying /etc/sysctl.d/10-network-security.conf ...
net.ipv4.conf.default.rp_filter = 2
net.ipv4.conf.all.rp_filter = 2
* Applying /etc/sysctl.d/10-ptrace.conf ...
kernel.yama.ptrace_scope = 1
* Applying /etc/sysctl.d/10-zeropage.conf ...
vm.mmap_min_addr = 65536
* Applying /usr/lib/sysctl.d/50-default.conf ...
net.ipv4.conf.default.promote_secondaries = 1
sysctl: setting key "net.ipv4.conf.all.promote_secondaries": Invalid argument
net.ipv4.ping_group_range = 0 2147483647
net.core.default_qdisc = fq_codel
fs.protected_regular = 1
fs.protected_fifos = 1
* Applying /usr/lib/sysctl.d/50-pid-max.conf ...
kernel.pid_max = 4194304
* Applying /etc/sysctl.d/99-sonarqube.conf ...
vm.max_map_count = 524288
fs.file-max = 131072
* Applying /etc/sysctl.d/99-sysctl.conf ...
* Applying /usr/lib/sysctl.d/protect-links.conf ...
fs.protected_fifos = 1
fs.protected_hardlinks = 1
fs.protected_regular = 2
fs.protected_symlinks = 1
* Applying /etc/sysctl.conf ...
root@devops:~#
```

Setup Database Postgresql

```bash
root@devops:~# su - postgres
postgres@devops:~$ createuser sonar
postgres@devops:~$ psql
psql (15.3 (Ubuntu 15.3-1.pgdg20.04+1))
Type "help" for help.

postgres=# ALTER USER sonar WITH ENCRYPTED password 'sonar';
ALTER ROLE
postgres=# CREATE DATABASE sonarqube OWNER sonar;
CREATE DATABASE
postgres=# grant all privileges on DATABASE sonarqube to sonar;
GRANT
postgres=# \l
postgres=# \du
                                   List of roles
 Role name |                         Attributes                         | Member of 
-----------+------------------------------------------------------------+-----------
 postgres  | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
 sonar     |                                                            | {}

postgres=# exit
postgres@devops:~$
```

Setup User Sonar

<aside>
💡 $ groupadd sonar

</aside>

<aside>
💡 $ `useradd -s /bin/bash -d /opt/sonarqube -g sonar sonar`

</aside>

```bash
root@devops:/# **cd /tmp/**
root@devops:/tmp# **wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.9.1.69595.zip**
--2023-07-25 06:14:53--  https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.9.1.69595.zip
Resolving binaries.sonarsource.com (binaries.sonarsource.com)... 13.33.33.110, 13.33.33.117, 13.33.33.80, ...
Connecting to binaries.sonarsource.com (binaries.sonarsource.com)|13.33.33.110|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293875683 (280M) [binary/octet-stream]
Saving to: ‘sonarqube-9.9.1.69595.zip’

sonarqube-9.9.1.69595.zip   100%[===========================================>] 280.26M  4.69MB/s    in 60s     

2023-07-25 06:15:54 (4.67 MB/s) - ‘sonarqube-9.9.1.69595.zip’ saved [293875683/293875683]

root@devops:/tmp# unzip sonarqube-9.9.1.69595.zip

Command 'unzip' not found, but can be installed with:

apt install unzip

root@devops:/tmp# **apt install unzip**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 libxmlb1
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  zip
The following NEW packages will be installed:
  unzip
0 upgraded, 1 newly installed, 0 to remove and 66 not upgraded.
Need to get 168 kB of archives.
After this operation, 593 kB of additional disk space will be used.
Get:1 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 unzip amd64 6.0-25ubuntu1.1 [168 kB]
Fetched 168 kB in 0s (564 kB/s)
Selecting previously unselected package unzip.
(Reading database ... 133096 files and directories currently installed.)
Preparing to unpack .../unzip_6.0-25ubuntu1.1_amd64.deb ...
Unpacking unzip (6.0-25ubuntu1.1) ...
Setting up unzip (6.0-25ubuntu1.1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
root@devops:/tmp# **unzip sonarqube-9.9.1.69595.zip** 
Archive:  sonarqube-9.9.1.69595.zip
   creating: sonarqube-9.9.1.69595/
  inflating: sonarqube-9.9.1.69595/dependency-license.json  
  inflating: sonarqube-9.9.1.69595/COPYING  
   creating: sonarqube-9.9.1.69595/bin/
   creating: sonarqube-9.9.1.69595/bin/windows-x86-64/
  inflating: sonarqube-9.9.1.69595/bin/windows-x86-64/SonarService.bat  
   creating: sonarqube-9.9.1.69595/bin/windows-x86-64/lib/
  inflating: sonarqube-9.9.1.69595/bin/windows-x86-64/lib/SonarServiceWrapper.exe  
  inflating: sonarqube-9.9.1.69595/bin/windows-x86-64/lib/find_java.bat  
   creating: sonarqube-9.9.1.69595/bin/winsw-license/
  inflating: sonarqube-9.9.1.69595/bin/winsw-license/LICENSE.txt  
   creating: sonarqube-9.9.1.69595/data/
  inflating: sonarqube-9.9.1.69595/data/README.txt  
   creating: sonarqube-9.9.1.69595/extensions/
   creating: sonarqube-9.9.1.69595/extensions/jdbc-driver/
   creating: sonarqube-9.9.1.69595/extensions/jdbc-driver/oracle/
  inflating: sonarqube-9.9.1.69595/extensions/jdbc-driver/oracle/README.txt  
   creating: sonarqube-9.9.1.69595/extensions/plugins/
  inflating: sonarqube-9.9.1.69595/extensions/plugins/README.txt  
   creating: sonarqube-9.9.1.69595/logs/
  inflating: sonarqube-9.9.1.69595/logs/README.txt  
   creating: sonarqube-9.9.1.69595/temp/
  inflating: sonarqube-9.9.1.69595/temp/README.txt  
   creating: sonarqube-9.9.1.69595/elasticsearch/
   creating: sonarqube-9.9.1.69595/elasticsearch/lib/
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/java-version-checker-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-launchers-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-x-content-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-lz4-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-cli-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-core-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-secure-sm-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-geo-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-core-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-analyzers-common-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-backward-codecs-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-grouping-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-highlighter-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-join-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-memory-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-misc-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-queries-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-queryparser-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-sandbox-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-spatial3d-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lucene-suggest-8.11.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/hppc-0.8.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/joda-time-2.10.10.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/t-digest-3.2.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/HdrHistogram-2.1.9.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/log4j-api-2.17.1.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-log4j-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/jna-5.10.0.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/elasticsearch-plugin-classloader-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/snakeyaml-1.33.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/jackson-core-2.10.4.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/jackson-dataformat-smile-2.10.4.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/jackson-dataformat-yaml-2.10.4.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/jackson-dataformat-cbor-2.10.4.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/lz4-java-1.8.0.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/lib/jopt-simple-5.0.2.jar  
   creating: sonarqube-9.9.1.69595/elasticsearch/config/
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/log4j2.properties  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/users_roles  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/users  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/roles.yml  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/role_mapping.yml  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/jvm.options  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/elasticsearch.yml  
  inflating: sonarqube-9.9.1.69595/elasticsearch/config/elasticsearch-plugins.example.yml  
   creating: sonarqube-9.9.1.69595/elasticsearch/bin/
  inflating: sonarqube-9.9.1.69595/elasticsearch/bin/elasticsearch-env-from-file  
  inflating: sonarqube-9.9.1.69595/elasticsearch/bin/elasticsearch-env  
  inflating: sonarqube-9.9.1.69595/elasticsearch/README.asciidoc  
  inflating: sonarqube-9.9.1.69595/elasticsearch/LICENSE.txt  
  inflating: sonarqube-9.9.1.69595/elasticsearch/NOTICE.txt  
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/transport-netty4-client-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/plugin-security.policy  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/plugin-descriptor.properties  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-transport-4.1.66.Final.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-resolver-4.1.66.Final.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-handler-4.1.66.Final.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-common-4.1.66.Final.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-codec-http-4.1.66.Final.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-codec-4.1.66.Final.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/transport-netty4/netty-buffer-4.1.66.Final.jar  
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/reindex-client-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/plugin-security.policy  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/plugin-descriptor.properties  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/httpcore-nio-4.4.12.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/httpcore-4.4.12.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/httpclient-4.5.10.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/httpasyncclient-4.1.4.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/elasticsearch-ssl-config-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/elasticsearch-rest-client-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/commons-logging-1.1.3.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/reindex/commons-codec-1.11.jar  
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/parent-join/
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/parent-join/plugin-descriptor.properties  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/parent-join/parent-join-client-7.17.8.jar  
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/spi/
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/spi/elasticsearch-scripting-painless-spi-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/plugin-security.policy  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/plugin-descriptor.properties  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/lang-painless-7.17.8.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/asm-util-7.2.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/asm-tree-7.2.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/asm-commons-7.2.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/asm-analysis-7.2.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/asm-7.2.jar  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/lang-painless/antlr4-runtime-4.5.3.jar  
   creating: sonarqube-9.9.1.69595/elasticsearch/modules/analysis-common/
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/analysis-common/plugin-descriptor.properties  
  inflating: sonarqube-9.9.1.69595/elasticsearch/modules/analysis-common/analysis-common-7.17.8.jar  
   creating: sonarqube-9.9.1.69595/conf/
  inflating: sonarqube-9.9.1.69595/conf/sonar.properties  
   creating: sonarqube-9.9.1.69595/bin/linux-x86-64/
  inflating: sonarqube-9.9.1.69595/bin/linux-x86-64/sonar.sh  
   creating: sonarqube-9.9.1.69595/bin/macosx-universal-64/
  inflating: sonarqube-9.9.1.69595/bin/macosx-universal-64/sonar.sh  
  inflating: sonarqube-9.9.1.69595/bin/windows-x86-64/StartSonar.bat  
  inflating: sonarqube-9.9.1.69595/bin/windows-x86-64/lib/SonarServiceWrapperTemplate.xml  
  inflating: sonarqube-9.9.1.69595/elasticsearch/bin/elasticsearch  
   creating: sonarqube-9.9.1.69595/lib/
   creating: sonarqube-9.9.1.69595/lib/extensions/
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-csharp-plugin-8.51.0.59060.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-vbnet-plugin-8.51.0.59060.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-flex-plugin-2.8.0.3166.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-html-plugin-3.7.1.3306.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-java-plugin-7.16.0.30901.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-jacoco-plugin-1.3.0.1538.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-javascript-plugin-9.13.0.20537.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-php-plugin-3.27.1.9352.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-python-plugin-3.24.0.10784.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-go-plugin-1.11.0.3905.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-kotlin-plugin-2.12.0.1956.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-ruby-plugin-1.11.0.3905.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-scala-plugin-1.11.0.3905.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-xml-plugin-2.7.0.3820.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-config-plugin-1.2.0.267.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-iac-plugin-1.11.0.2847.jar  
  inflating: sonarqube-9.9.1.69595/lib/extensions/sonar-text-plugin-2.0.2.1090.jar  
   creating: sonarqube-9.9.1.69595/lib/scanner/
  inflating: sonarqube-9.9.1.69595/lib/scanner/sonar-scanner-engine-shaded-9.9.1.69595-all.jar  
  inflating: sonarqube-9.9.1.69595/lib/sonar-application-9.9.1.69595.jar  
   creating: sonarqube-9.9.1.69595/web/
   creating: sonarqube-9.9.1.69595/web/WEB-INF/
   creating: sonarqube-9.9.1.69595/web/WEB-INF/classes/
   creating: sonarqube-9.9.1.69595/web/WEB-INF/classes/com/
   creating: sonarqube-9.9.1.69595/web/WEB-INF/classes/com/sonarsource/
  inflating: sonarqube-9.9.1.69595/web/WEB-INF/classes/com/sonarsource/branding  
   creating: sonarqube-9.9.1.69595/web/images/
  inflating: sonarqube-9.9.1.69595/web/images/logo.svg  
   creating: sonarqube-9.9.1.69595/web/js/
  inflating: sonarqube-9.9.1.69595/web/js/outYFLVXB5G.css  
  inflating: sonarqube-9.9.1.69595/web/js/outL2Z6DMVA.js  
  inflating: sonarqube-9.9.1.69595/web/js/outYFLVXB5G.css.map  
  inflating: sonarqube-9.9.1.69595/web/js/outL2Z6DMVA.js.map  
  inflating: sonarqube-9.9.1.69595/web/index.html  
  inflating: sonarqube-9.9.1.69595/web/.htaccess  
  inflating: sonarqube-9.9.1.69595/web/WEB-INF/web.xml  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-114x114.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-120x120.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-144x144.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-152x152.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-180x180.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-57x57.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-60x60.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-72x72.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-76x76.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon-precomposed.png  
  inflating: sonarqube-9.9.1.69595/web/apple-touch-icon.png  
  inflating: sonarqube-9.9.1.69595/web/favicon.ico  
  inflating: sonarqube-9.9.1.69595/web/images/SonarLint-connection-ok.png  
  inflating: sonarqube-9.9.1.69595/web/images/SonarLint-connection-request.png  
  inflating: sonarqube-9.9.1.69595/web/images/activity-chart.svg  
   creating: sonarqube-9.9.1.69595/web/images/alm/
  inflating: sonarqube-9.9.1.69595/web/images/alm/azure.svg  
  inflating: sonarqube-9.9.1.69595/web/images/alm/bitbucket-white.svg  
  inflating: sonarqube-9.9.1.69595/web/images/alm/bitbucket.svg  
  inflating: sonarqube-9.9.1.69595/web/images/alm/github-white.svg  
  inflating: sonarqube-9.9.1.69595/web/images/alm/github.svg  
  inflating: sonarqube-9.9.1.69595/web/images/alm/gitlab.svg  
  inflating: sonarqube-9.9.1.69595/web/images/check.svg  
  inflating: sonarqube-9.9.1.69595/web/images/cross.svg  
   creating: sonarqube-9.9.1.69595/web/images/embed-doc/
  inflating: sonarqube-9.9.1.69595/web/images/embed-doc/sq-icon.svg  
  inflating: sonarqube-9.9.1.69595/web/images/embed-doc/twitter-icon.svg  
  inflating: sonarqube-9.9.1.69595/web/images/filter-large.svg  
  inflating: sonarqube-9.9.1.69595/web/images/hotspot-large.svg  
  inflating: sonarqube-9.9.1.69595/web/images/loading.gif  
  inflating: sonarqube-9.9.1.69595/web/images/saml.png  
  inflating: sonarqube-9.9.1.69595/web/images/source-code.svg  
  inflating: sonarqube-9.9.1.69595/web/images/sq-sl.svg  
   creating: sonarqube-9.9.1.69595/web/images/tutorials/
  inflating: sonarqube-9.9.1.69595/web/images/tutorials/azure-pipelines.svg  
  inflating: sonarqube-9.9.1.69595/web/images/tutorials/commit.svg  
  inflating: sonarqube-9.9.1.69595/web/images/tutorials/github-actions.svg  
  inflating: sonarqube-9.9.1.69595/web/images/tutorials/jenkins.svg  
  inflating: sonarqube-9.9.1.69595/web/images/tutorials/manual.svg  
  inflating: sonarqube-9.9.1.69595/web/images/tutorials/refresh.svg  
  inflating: sonarqube-9.9.1.69595/web/mstile-512x512.png  
  inflating: sonarqube-9.9.1.69595/web/robots.txt  
   creating: sonarqube-9.9.1.69595/lib/jdbc/
   creating: sonarqube-9.9.1.69595/lib/jdbc/mssql/
  inflating: sonarqube-9.9.1.69595/lib/jdbc/mssql/mssql-jdbc-11.2.2.jre17.jar  
   creating: sonarqube-9.9.1.69595/lib/jdbc/postgresql/
  inflating: sonarqube-9.9.1.69595/lib/jdbc/postgresql/postgresql-42.5.1.jar  
   creating: sonarqube-9.9.1.69595/lib/jdbc/h2/
  inflating: sonarqube-9.9.1.69595/lib/jdbc/h2/h2-2.1.214.jar  
  inflating: sonarqube-9.9.1.69595/lib/sonar-shutdowner-9.9.1.69595.jar  
   creating: sonarqube-9.9.1.69595/elasticsearch/plugins/
root@devops:/tmp#
```

Change Owner SonarQube 

```bash
root@devops:/tmp# mv sonarqube-9.9.1.69595 /opt/sonarqube
root@devops:/tmp# chown -R sonar:sonar /opt/sonarqube
```

Create link sonarqube server

```bash
	root@devops:/tmp# ln -s /opt/sonarqube/bin/linux-x86-64/sonar.sh /usr/bin/
```

### Config Sonarqube

Config sonar properties to use database and specific user

```bash
root@devops:/tmp# vim /opt/sonarqube/conf/sonar.properties
# User credentials.
# Permissions to create tables, indices and triggers must be granted to JDBC user.
# The schema must be created first.
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar

#----- Embedded Database (default)
# H2 embedded database server listening port, defaults to 9092
#sonar.embeddedDatabase.port=9092

#----- Oracle 19c/21c
# The Oracle JDBC driver must be copied into the directory extensions/jdbc-driver/oracle/.
# Only the thin client is supported, and we recommend using the latest Oracle JDBC driver. See
# https://jira.sonarsource.com/browse/SONAR-9758 for more details.
# If you need to set the schema, please refer to http://jira.sonarsource.com/browse/SONAR-5000
#sonar.jdbc.url=jdbc:oracle:thin:@localhost:1521/XE

#----- PostgreSQL 11 or greater
# By default the schema named "public" is used. It can be overridden with the parameter "currentSchema".
sonar.jdbc.url=jdbc:postgresql://localhost/sonarqube
```

Config sonar shell script to spesific user

```bash
root@devops:/tmp# vim /opt/sonarqube/bin/linux-x86-64/sonar.sh
#! /bin/sh
  
APP_NAME="SonarQube"
RUN_AS_USER=sonar
# By default, java from the PATH is used, except if SONAR_JAVA_PATH env variable is set
findjava() {
  if [ -z "${SONAR_JAVA_PATH}" ]; then
    if ! command -v java 2>&1; then
      echo "Java not found. Please make sure that the environmental variable SONAR_JAVA_PATH points to a Java executable"
      exit 1
    fi
    JAVA_CMD=java
  else
    if ! [ -x "${SONAR_JAVA_PATH}" ] || ! [ -f "${SONAR_JAVA_PATH}" ]; then
      echo "File '${SONAR_JAVA_PATH}' is not executable. Please make sure that the environmental variable SONAR_JAVA_PATH points to a Java executable"
      exit 1
    fi
    JAVA_CMD="${SONAR_JAVA_PATH}"
  fi
}

findjava
```

### Start Sonarqube

Login to user sonar

```bash
root@devops:~# su - sonar
sonar@devops:~$ cd /opt/sonarqube/bin/linux-x86-64/
sonar@devops:~/bin/linux-x86-64$ ./sonar.sh start
/usr/bin/java
Starting SonarQube...
Started SonarQube.
sonar@devops:~/bin/linux-x86-64$ ./sonar.sh status
/usr/bin/java
SonarQube is running (93728).
sonar@devops:~/bin/linux-x86-64$ tail -f /opt/sonarqube/logs/sonar.log
2023.07.25 06:34:57 INFO  app[][o.s.a.SchedulerImpl] Waiting for Elasticsearch to be up and running
2023.07.25 06:35:07 INFO  app[][o.s.a.SchedulerImpl] Process[es] is up
2023.07.25 06:35:07 INFO  app[][o.s.a.ProcessLauncherImpl] Launch process[WEB_SERVER] from [/opt/sonarqube]: /usr/lib/jvm/java-17-openjdk-amd64/bin/java -Djava.awt.headless=true -Dfile.encoding=UTF-8 -Djava.io.tmpdir=/opt/sonarqube/temp -XX:-OmitStackTraceInFastThrow --add-opens=java.base/java.util=ALL-UNNAMED --add-opens=java.base/java.lang=ALL-UNNAMED --add-opens=java.base/java.io=ALL-UNNAMED --add-opens=java.rmi/sun.rmi.transport=ALL-UNNAMED --add-exports=java.base/jdk.internal.ref=ALL-UNNAMED --add-opens=java.base/java.nio=ALL-UNNAMED --add-opens=java.base/sun.nio.ch=ALL-UNNAMED --add-opens=java.management/sun.management=ALL-UNNAMED --add-opens=jdk.management/com.sun.management.internal=ALL-UNNAMED -Dcom.redhat.fips=false -Xmx512m -Xms128m -XX:+HeapDumpOnOutOfMemoryError -Dhttp.nonProxyHosts=localhost|127.*|[::1] -cp ./lib/sonar-application-9.9.1.69595.jar:/opt/sonarqube/lib/jdbc/postgresql/postgresql-42.5.1.jar org.sonar.server.app.WebServer /opt/sonarqube/temp/sq-process16912377295537841572properties
2023.07.25 06:35:56 INFO  app[][o.s.a.SchedulerImpl] Process[web] is up
2023.07.25 06:35:56 INFO  app[][o.s.a.ProcessLauncherImpl] Launch process[COMPUTE_ENGINE] from [/opt/sonarqube]: /usr/lib/jvm/java-17-openjdk-amd64/bin/java -Djava.awt.headless=true -Dfile.encoding=UTF-8 -Djava.io.tmpdir=/opt/sonarqube/temp -XX:-OmitStackTraceInFastThrow --add-opens=java.base/java.util=ALL-UNNAMED --add-exports=java.base/jdk.internal.ref=ALL-UNNAMED --add-opens=java.base/java.lang=ALL-UNNAMED --add-opens=java.base/java.nio=ALL-UNNAMED --add-opens=java.base/sun.nio.ch=ALL-UNNAMED --add-opens=java.management/sun.management=ALL-UNNAMED --add-opens=jdk.management/com.sun.management.internal=ALL-UNNAMED -Dcom.redhat.fips=false -Xmx512m -Xms128m -XX:+HeapDumpOnOutOfMemoryError -Dhttp.nonProxyHosts=localhost|127.*|[::1] -cp ./lib/sonar-application-9.9.1.69595.jar:/opt/sonarqube/lib/jdbc/postgresql/postgresql-42.5.1.jar org.sonar.ce.app.CeServer /opt/sonarqube/temp/sq-process1551503789833946147properties
2023.07.25 06:35:56 WARN  app[][startup] ####################################################################################################################
2023.07.25 06:35:56 WARN  app[][startup] Default Administrator credentials are still being used. Make sure to change the password or deactivate the account.
2023.07.25 06:35:56 WARN  app[][startup] ####################################################################################################################
2023.07.25 06:36:02 INFO  app[][o.s.a.SchedulerImpl] Process[ce] is up
2023.07.25 06:36:02 INFO  app[][o.s.a.SchedulerImpl] SonarQube is operational

sonar@devops:~/bin/linux-x86-64$ ./sonar.sh stop
/usr/bin/java
Gracefully stopping SonarQube...
Stopped SonarQube.
sonar@devops:~/bin/linux-x86-64$
```

### Configure systemd service

Configure systemd to manage automatic sonar service

```bash
sonar@devops:~/bin/linux-x86-64$ exit
logout
There are stopped jobs.
sonar@devops:~/bin/linux-x86-64$ exit
logout
root@devops:/opt/sonarqube/bin/linux-x86-64# cd
root@devops:~# vim /etc/systemd/system/sonar.service
[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking

ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop

User=sonar
Group=sonar
Restart=always

LimitNOFILE=65536
LimitNPROC=4096

[Install]
WantedBy=multi-user.target

root@devops:~# systemctl daemon-reload
root@devops:~# systemctl start sonar
root@devops:~# systemctl status sonar
● sonar.service - SonarQube service
     Loaded: loaded (/etc/systemd/system/sonar.service; disabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-07-25 06:42:06 WIB; 5s ago
    Process: 94400 ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start (code=exited, status=0/SUCCESS)
   Main PID: 94443 (java)
      Tasks: 58 (limit: 9442)
     Memory: 709.2M
     CGroup: /system.slice/sonar.service
             ├─94443 java -Xms8m -Xmx32m --add-exports=java.base/jdk.internal.ref=ALL-UNNAMED --add-opens=java.>
             └─94471 /usr/lib/jvm/java-17-openjdk-amd64/bin/java -XX:+UseG1GC -Djava.io.tmpdir=/opt/sonarqube/t>

Jul 25 06:42:06 devops systemd[1]: Starting SonarQube service...
Jul 25 06:42:06 devops sonar.sh[94400]: /usr/bin/java
Jul 25 06:42:06 devops sonar.sh[94400]: Starting SonarQube...
Jul 25 06:42:06 devops sonar.sh[94400]: Started SonarQube.
Jul 25 06:42:06 devops systemd[1]: Started SonarQube service.
root@devops:~#
```

Setup Password admin sonar

admin:admin

![Screenshot 2023-07-25 at 06.43.06.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.43.06.png)

![Screenshot 2023-07-25 at 06.43.19.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.43.19.png)

# Install SonarScanner

Download and extract sonar-scanner package

```bash
root@devops:/tmp# wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.8.0.2856-linux.zip
--2023-07-25 06:44:53--  https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.8.0.2856-linux.zip
Resolving binaries.sonarsource.com (binaries.sonarsource.com)... 18.64.37.63, 18.64.37.68, 18.64.37.40, ...
Connecting to binaries.sonarsource.com (binaries.sonarsource.com)|18.64.37.63|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 43565694 (42M) [binary/octet-stream]
Saving to: ‘sonar-scanner-cli-4.8.0.2856-linux.zip’

sonar-scanner-cli-4.8.0.285 100%[===========================================>]  41.55M  5.75MB/s    in 7.9s    

2023-07-25 06:45:02 (5.28 MB/s) - ‘sonar-scanner-cli-4.8.0.2856-linux.zip’ saved [43565694/43565694]

root@devops:/tmp# unzip sonar-scanner-cli-4.8.0.2856-linux.zip
Archive:  sonar-scanner-cli-4.8.0.2856-linux.zip
   creating: sonar-scanner-4.8.0.2856-linux/
   creating: sonar-scanner-4.8.0.2856-linux/jre/
   creating: sonar-scanner-4.8.0.2856-linux/jre/conf/
   creating: sonar-scanner-4.8.0.2856-linux/jre/conf/management/
   creating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/
   creating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/
   creating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/limited/
   creating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/unlimited/
   creating: sonar-scanner-4.8.0.2856-linux/jre/lib/
   creating: sonar-scanner-4.8.0.2856-linux/jre/lib/jli/
   creating: sonar-scanner-4.8.0.2856-linux/jre/lib/server/
   creating: sonar-scanner-4.8.0.2856-linux/jre/lib/security/
   creating: sonar-scanner-4.8.0.2856-linux/jre/lib/jfr/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/
   creating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/
   creating: sonar-scanner-4.8.0.2856-linux/jre/bin/
   creating: sonar-scanner-4.8.0.2856-linux/lib/
   creating: sonar-scanner-4.8.0.2856-linux/conf/
   creating: sonar-scanner-4.8.0.2856-linux/bin/
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/net.properties  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/management/management.properties  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/management/jmxremote.access  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/management/jmxremote.password.template  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/limited/default_local.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/limited/default_US_export.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/limited/exempt_local.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/unlimited/default_local.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/unlimited/default_US_export.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/policy/README.txt  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/java.security  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/security/java.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/logging.properties  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/conf/sound.properties  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libzip.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/psfontj2d.properties  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjimage.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jrt-fs.jar  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libj2pcsc.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libsunec.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libunpack.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/librmi.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libawt_headless.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libfontmanager.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjavajpeg.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libj2gss.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libmanagement_ext.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libsplashscreen.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjsound.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/liblcms.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/psfont.properties.ja  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libsctp.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/tzdb.dat  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libmanagement_agent.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jexec  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jli/libjli.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libverify.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjawt.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libdt_socket.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libnio.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjsig.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/classlist  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/server/libjvm.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/server/libjsig.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/server/Xusage.txt  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/security/blocked.certs  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/security/cacerts  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/security/public_suffix_list.dat  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/security/default.policy  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jvm.cfg  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libawt.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jspawnhelper  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libj2pkcs11.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/modules  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libnet.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libextnet.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libprefs.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjdwp.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjaas.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libmanagement.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jfr/default.jfc  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/jfr/profile.jfc  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libjava.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libinstrument.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libmlib_image.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/lib/libawt_xawt.so  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/NOTICE  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/release  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/ecc.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/dynalink.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/double-conversion.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/joni.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/santuario.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/unicode.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/aes.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/c-libutl.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/LICENSE  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/public_suffix.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/asm.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/ASSEMBLY_EXCEPTION  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/icu.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/cldr.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.base/ADDITIONAL_LICENSE_INFO  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/pcsclite.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/jline.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/pkcs11wrapper.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/pkcs11cryptotoken.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/thaidict.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/cldr.md  -> ../java.base/cldr.md 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/colorimaging.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/mesa3d.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/giflib.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/harfbuzz.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/lcms.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/jpeg.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/xwd.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/libpng.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/xerces.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/jcup.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/dom.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/xalan.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/bcel.md  
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/LICENSE  -> ../java.base/LICENSE 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/ASSEMBLY_EXCEPTION  -> ../java.base/ASSEMBLY_EXCEPTION 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/ADDITIONAL_LICENSE_INFO  -> ../java.base/ADDITIONAL_LICENSE_INFO 
  inflating: sonar-scanner-4.8.0.2856-linux/jre/bin/java  
  inflating: sonar-scanner-4.8.0.2856-linux/lib/sonar-scanner-cli-4.8.0.2856.jar  
  inflating: sonar-scanner-4.8.0.2856-linux/conf/sonar-scanner.properties  
  inflating: sonar-scanner-4.8.0.2856-linux/bin/sonar-scanner  
  inflating: sonar-scanner-4.8.0.2856-linux/bin/sonar-scanner-debug  
finishing deferred symbolic links:
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.ec/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.dynalink/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jfr/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.management.rmi/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.transaction.xa/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.management/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.dns/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler.management/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.compiler/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.rmi/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml.crypto/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.agent/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.prefs/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.ci/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.smartcardio/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.le/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.net.http/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.sasl/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.crypto.cryptoki/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.scripting.nashorn.shell/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.security.jgss/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.vm.compiler/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.scripting/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.naming.ldap/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.httpserver/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.logging/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.auth/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.naming/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/cldr.md -> ../java.base/cldr.md
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.localedata/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.instrument/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.xml.dom/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.accessibility/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.desktop/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jsobject/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.zipfs/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management.jfr/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.se/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.xml/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.internal.ed/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.security.jgss/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.net/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.jdwp.agent/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.datatransfer/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.aot/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.sctp/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.rmi/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.pack/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.unsupported/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/java.sql.rowset/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.charsets/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/LICENSE -> ../java.base/LICENSE
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/ASSEMBLY_EXCEPTION -> ../java.base/ASSEMBLY_EXCEPTION
  sonar-scanner-4.8.0.2856-linux/jre/legal/jdk.management/ADDITIONAL_LICENSE_INFO -> ../java.base/ADDITIONAL_LICENSE_INFO
root@devops:/tmp#
```

Move sonar-scanner package and change ownership

```bash
root@devops:/tmp# mv -v /tmp/sonar-scanner-4.8.0.2856-linux/ /opt/sonar-scanner/
renamed '/tmp/sonar-scanner-4.8.0.2856-linux/' -> '/opt/sonar-scanner/'
root@devops:/tmp# chown -R sonar:sonar /opt/sonar-scanner 
root@devops:/tmp# ln -s /opt/sonar-scanner/bin/sonar-scanner /usr/bin/
```

## Analyze Source Code Use SonarQube

Click Manually

![Screenshot 2023-07-25 at 06.58.04.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.58.04.png)

create name project & project key

![Screenshot 2023-07-25 at 06.58.18.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.58.18.png)

Click Locally

![Screenshot 2023-07-25 at 06.58.29.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.58.29.png)

create token

![Screenshot 2023-07-25 at 06.58.54.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.58.54.png)

Save Token

![Screenshot 2023-07-25 at 06.59.00.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.59.00.png)

Choose Programming Languege your code & operating system 

![Screenshot 2023-07-25 at 06.59.29.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_06.59.29.png)

### Scanning

Config project in source code

![Screenshot 2023-07-25 at 07.09.02.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.09.02.png)

sonar-project.properties

```bash
# must be unique in a given SonarQube instance
sonar.projectKey=simple-apps

# --- optional properties ---

# defaults to project key
sonar.projectName=Simple Apps
# defaults to 'not provided'
sonar.projectVersion=1.0
 
# Path is relative to the sonar-project.properties file. Defaults to .
sonar.sources=.
 
# Encoding of the source code. Default is default system encoding
sonar.sourceEncoding=UTF-8
```

and push to github

on linux pull repository

```bash
root@devops:~/simple-apps# git pull
remote: Enumerating objects: 2, done.
remote: Counting objects: 100% (2/2), done.
remote: Total 2 (delta 1), reused 2 (delta 1), pack-reused 0
Unpacking objects: 100% (2/2), 280 bytes | 280.00 KiB/s, done.
From github.com:dbyna/simple-apps
   128c81c..eb9ee5d  main       -> origin/main
Updating 128c81c..eb9ee5d
Fast-forward
 sonar-project.properties | 15 +++++++++++++++
 1 file changed, 15 insertions(+)
 create mode 100644 sonar-project.properties
root@devops:~/simple-apps# ls -l
total 268
-rw-r--r--   1 root root    881 Jul 24 23:03 app.js
drwxr-xr-x   3 root root   4096 Jul 24 23:22 coverage
drwxr-xr-x   2 root root   4096 Jul 24 23:03 database
drwxr-xr-x   2 root root   4096 Jul 24 23:03 middleware
drwxr-xr-x 296 root root  12288 Jul 24 23:10 node_modules
-rw-r--r--   1 root root    621 Jul 24 23:22 package.json
-rw-r--r--   1 root root 223200 Jul 24 23:10 package-lock.json
drwxr-xr-x   4 root root   4096 Jul 24 23:03 public
-rw-r--r--   1 root root    121 Jul 24 23:03 README.md
-rw-r--r--   1 root root    401 Jul 25 07:09 sonar-project.properties
drwxr-xr-x   2 root root   4096 Jul 24 23:03 testing
root@devops:~/simple-apps#
```

Running Analyze

```bash
sonar-scanner \
  -Dsonar.projectKey=simple-apps \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://10.23.0.113:9000 \
  -Dsonar.login=sqp_73ff98e18a53cc350850ac560b6a98e33cccdc8e
```

```bash
root@devops:~/simple-apps# sonar-scanner \
>   -Dsonar.projectKey=simple-apps \
>   -Dsonar.sources=. \
>   -Dsonar.host.url=http://10.23.0.113:9000 \
>   -Dsonar.login=sqp_73ff98e18a53cc350850ac560b6a98e33cccdc8e
INFO: Scanner configuration file: /opt/sonar-scanner/conf/sonar-scanner.properties
INFO: Project root configuration file: /root/simple-apps/sonar-project.properties
INFO: SonarScanner 4.8.0.2856
INFO: Java 11.0.17 Eclipse Adoptium (64-bit)
INFO: Linux 5.4.0-135-generic amd64
INFO: User cache: /root/.sonar/cache
INFO: Analyzing on SonarQube server 9.9.1.69595
INFO: Default locale: "en_US", source code encoding: "UTF-8"
INFO: Load global settings
INFO: Load global settings (done) | time=166ms
INFO: Server id: 86E1FA4D-AYmKQdG4nEVTUjMjkjV2
INFO: User cache: /root/.sonar/cache
INFO: Load/download plugins
INFO: Load plugins index
INFO: Load plugins index (done) | time=120ms
INFO: Load/download plugins (done) | time=2550ms
INFO: Process project properties
INFO: Process project properties (done) | time=12ms
INFO: Execute project builders
INFO: Execute project builders (done) | time=2ms
INFO: Project key: simple-apps
INFO: Base dir: /root/simple-apps
INFO: Working dir: /root/simple-apps/.scannerwork
INFO: Load project settings for component key: 'simple-apps'
INFO: Load project settings for component key: 'simple-apps' (done) | time=49ms
INFO: Load quality profiles
INFO: Load quality profiles (done) | time=170ms
INFO: Load active rules
INFO: Load active rules (done) | time=3477ms
INFO: Load analysis cache
INFO: Load analysis cache (404) | time=11ms
INFO: Load project repositories
INFO: Load project repositories (done) | time=30ms
INFO: Indexing files...
INFO: Project configuration:
INFO: 2137 files indexed
INFO: 0 files ignored because of scm ignore settings
INFO: Quality profile for css: Sonar way
INFO: Quality profile for js: Sonar way
INFO: Quality profile for json: Sonar way
INFO: Quality profile for web: Sonar way
INFO: Quality profile for xml: Sonar way
INFO: ------------- Run sensors on module Simple Apps
INFO: Load metrics repository
INFO: Load metrics repository (done) | time=48ms
INFO: Sensor JaCoCo XML Report Importer [jacoco]
INFO: 'sonar.coverage.jacoco.xmlReportPaths' is not defined. Using default locations: target/site/jacoco/jacoco.xml,target/site/jacoco-it/jacoco.xml,build/reports/jacoco/test/jacocoTestReport.xml
INFO: No report imported, no coverage information will be imported by JaCoCo XML Report Importer
INFO: Sensor JaCoCo XML Report Importer [jacoco] (done) | time=6ms
INFO: Sensor IaC CloudFormation Sensor [iac]
INFO: 0 source files to be analyzed
INFO: 0/0 source files have been analyzed
INFO: Sensor IaC CloudFormation Sensor [iac] (done) | time=1153ms
INFO: Sensor IaC Kubernetes Sensor [iac]
INFO: 0 source files to be analyzed
INFO: 0/0 source files have been analyzed
INFO: Sensor IaC Kubernetes Sensor [iac] (done) | time=501ms
INFO: Sensor JavaScript analysis [javascript]
INFO: 6 source files to be analyzed
INFO: 6/6 source files have been analyzed
INFO: Hit the cache for 0 out of 6
INFO: Miss the cache for 6 out of 6: ANALYSIS_MODE_INELIGIBLE [6/6]
INFO: Sensor JavaScript analysis [javascript] (done) | time=11658ms
INFO: Sensor TypeScript analysis [javascript]
INFO: No input files found for analysis
INFO: Hit the cache for 0 out of 0
INFO: Miss the cache for 0 out of 0
INFO: Sensor TypeScript analysis [javascript] (done) | time=3ms
INFO: Sensor CSS Rules [javascript]
INFO: 11 source files to be analyzed
INFO: 11/11 source files have been analyzed
INFO: Hit the cache for 0 out of 0
INFO: Miss the cache for 0 out of 0
INFO: Sensor CSS Rules [javascript] (done) | time=547ms
INFO: Sensor CSS Metrics [javascript]
INFO: Sensor CSS Metrics [javascript] (done) | time=64ms
INFO: Sensor C# Project Type Information [csharp]
INFO: Sensor C# Project Type Information [csharp] (done) | time=1ms
INFO: Sensor C# Analysis Log [csharp]
INFO: Sensor C# Analysis Log [csharp] (done) | time=20ms
INFO: Sensor C# Properties [csharp]
INFO: Sensor C# Properties [csharp] (done) | time=0ms
INFO: Sensor HTML [web]
INFO: Sensor HTML [web] (done) | time=582ms
INFO: Sensor XML Sensor [xml]
INFO: 1 source file to be analyzed
INFO: 1/1 source file has been analyzed
INFO: Sensor XML Sensor [xml] (done) | time=235ms
INFO: Sensor TextAndSecretsSensor [text]
INFO: 622 source files to be analyzed
INFO: 622/622 source files have been analyzed
INFO: Sensor TextAndSecretsSensor [text] (done) | time=1334ms
INFO: Sensor VB.NET Project Type Information [vbnet]
INFO: Sensor VB.NET Project Type Information [vbnet] (done) | time=2ms
INFO: Sensor VB.NET Analysis Log [vbnet]
INFO: Sensor VB.NET Analysis Log [vbnet] (done) | time=23ms
INFO: Sensor VB.NET Properties [vbnet]
INFO: Sensor VB.NET Properties [vbnet] (done) | time=0ms
INFO: Sensor IaC Docker Sensor [iac]
INFO: 0 source files to be analyzed
INFO: 0/0 source files have been analyzed
INFO: Sensor IaC Docker Sensor [iac] (done) | time=148ms
INFO: ------------- Run sensors on project
INFO: Sensor Analysis Warnings import [csharp]
INFO: Sensor Analysis Warnings import [csharp] (done) | time=2ms
INFO: Sensor Zero Coverage Sensor
INFO: Sensor Zero Coverage Sensor (done) | time=39ms
INFO: SCM Publisher SCM provider for this project is: git
INFO: SCM Publisher 18 source files to be analyzed
INFO: SCM Publisher 6/18 source files have been analyzed (done) | time=235ms
WARN: Missing blame information for the following files:
WARN:   * coverage/lcov-report/base.css
WARN:   * coverage/lcov-report/simple-apps/middleware/index.html
WARN:   * coverage/lcov-report/index.html
WARN:   * coverage/lcov-report/simple-apps/app.js.html
WARN:   * coverage/lcov-report/simple-apps/middleware/logger.js.html
WARN:   * coverage/lcov-report/sorter.js
WARN:   * coverage/lcov-report/simple-apps/middleware/db_connect.js.html
WARN:   * node_modules/bignumber.js/doc/API.html
WARN:   * coverage/lcov-report/block-navigation.js
WARN:   * node_modules/sprintf-js/demo/angular.html
WARN:   * coverage/lcov-report/simple-apps/index.html
WARN:   * coverage/clover.xml
WARN: This may lead to missing/broken features in SonarQube
INFO: CPD Executor 2 files had no CPD blocks
INFO: CPD Executor Calculating CPD for 13 files
INFO: CPD Executor CPD calculation finished (done) | time=43ms
INFO: Analysis report generated in 111ms, dir size=419.3 kB
INFO: Analysis report compressed in 128ms, zip size=122.6 kB
INFO: Analysis report uploaded in 77ms
INFO: ANALYSIS SUCCESSFUL, you can find the results at: http://10.23.0.113:9000/dashboard?id=simple-apps
INFO: Note that you will be able to access the updated dashboard once the server has processed the submitted analysis report
INFO: More about the report processing at http://10.23.0.113:9000/api/ce/task?id=AYmKZGixB1hL-C3OOIwI
INFO: Analysis total time: 33.581 s
INFO: ------------------------------------------------------------------------
INFO: EXECUTION SUCCESS
INFO: ------------------------------------------------------------------------
INFO: Total time: 38.821s
INFO: Final Memory: 18M/70M
INFO: ------------------------------------------------------------------------
root@devops:~/simple-apps#
```

REVIEW

![Screenshot 2023-07-25 at 07.13.55.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.13.55.png)

On The Security Hotspot Review “E”, for checking problem code, we can go to security hotspot menu 

![Screenshot 2023-07-25 at 07.16.57.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.16.57.png)

You copy x powered by to sourcecode app.js

![Screenshot 2023-07-25 at 07.17.06.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.17.06.png)

![Screenshot 2023-07-25 at 07.17.54.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.17.54.png)

![Screenshot 2023-07-25 at 07.18.16.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.18.16.png)

push and pull 

```bash
root@devops:~/simple-apps# git pull
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 3 (delta 2), pack-reused 0
Unpacking objects: 100% (3/3), 314 bytes | 314.00 KiB/s, done.
From github.com:dbyna/simple-apps
   eb9ee5d..fff4b08  main       -> origin/main
Updating eb9ee5d..fff4b08
Fast-forward
 app.js | 2 ++
 1 file changed, 2 insertions(+)
root@devops:~/simple-apps#
```

running again sonarscanner

```bash
root@devops:~/simple-apps# sonar-scanner   -Dsonar.projectKey=simple-apps   -Dsonar.sources=.   -Dsonar.host.url=http://10.23.0.113:9000   -Dsonar.login=sqp_73ff98e18a53cc350850ac560b6a98e33cccdc8e
```

Checking

![Screenshot 2023-07-25 at 07.22.57.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.22.57.png)

Exclusion, folder atau file yang tidak boleh di scan

sonar.scanner, file atau folder yang ingin di scan

test coverage : mengambil report coverage

![Screenshot 2023-07-25 at 07.36.43.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.36.43.png)

running again sonar scanner

```bash
root@devops:~/simple-apps# sonar-scanner   -Dsonar.projectKey=simple-apps   -Dsonar.sources=.   -Dsonar.host.url=http://10.23.0.113:9000   -Dsonar.login=sqp_73ff98e18a53cc350850ac560b6a98e33cccdc8e
```

checking

![Screenshot 2023-07-25 at 07.40.30.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.40.30.png)

![Screenshot 2023-07-25 at 07.40.38.png](SonarQube%20Fundamentals%201145aef1e485443faed19c685ccdc216/Screenshot_2023-07-25_at_07.40.38.png)