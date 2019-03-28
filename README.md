# Maya Install CentOS 7

## Info

- 명령어 앞에 '#'는 Root(루트) 계정을 뜻한다.

- Server & User PC OS: ```CentOS7```

- Maya Version: ```2018```

- 내려받은 파일들은 ```~/Downloads``` 디렉토리에 저장

## Server

1. Download Autodesk Network License Manager

    - [Autodesk Network License Manager for Linux](https://knowledge.autodesk.com/search-result/caas/downloads/content/autodesk-network-license-manager-for-linux.html)
    
    - 위에 링크에서 ```nlm11.16.2.0_ipv4_ipv6_linux64.tar.gz``` 파일 내려받기


1. Install the Autodesk Network License Manager

    ```
    # cd ~/Downloads
    
    # tar –zxvf nlm11.16.2.0_ipv4_ipv6_linux64.tar.gz

    # rpm -vhi nlm11.16.2.0_ipv4_ipv6_linux64.rpm
    ```

    - 위에 두줄을 입력하면 ```/opt/flexnetserver/``` 디렉토리에 라이센스 서버가 설치된다

1. Find your license server ```Host Name``` and ```Host ID``` 
    
    - Find **Host Name**
    ```
    # cd /opt/flexnetserver
    
    # ./lmutil lmhostid hostname 
    
    <Result>
    lmutil - Copyright (c) 1989-2013 Flexera Software LLC. All Rights Reserved.
    The FlexNet host ID of this machine is "HOSTNAME=storage"
    
    !! Host Name: storage !!
    ```
    
    
    - Find **Host ID**
    ```
    # cd /opt/flexnetserver
    
    # ./lmutil lmhostid
    
    <Result>
    lmutil - Copyright (c) 1989-2013 Flexera Software LLC. All Rights Reserved.
    The FlexNet host ID of this machine is "6003089af239"
    
    !! Host ID: 6003089af239 !!
    ```
    
    ```
    <오류>
    '/lib64/ld-lsb-x86-64.so.3: bad ELF interpreter: No such file or directory'
    
    <해결 방법>
    # yum -y install redhat-lsb
    ```
1. Generate your Network License File in Autodesk Account

    - Autodesk Account 접속 - [https://manage.autodesk.com/home/](https://manage.autodesk.com/)
        - OTP | Google Authenticator

## User PC

1. Install Dependencies (인터넷 필요)
    
    ```
    Dependent OpenGL libraries
    # yum -y install mesa-libGLw mesa-libGLU libglvnd*64

    Dependent X Windows libraries
    # yum -y install libXp libXpm libXmu libXt libXi libXext libX11 libXinerama libXau libxcb libXcomposite

    Dependent System libraries
    # yum -y install gamin audiofile audiofile-devel e2fsprogs-libs glibc zlib libSM libICE openssl098e tcsh pulseaudio-libs libxslt alsa-lib

    Fonts
    # yum -y install xorg-x11-fonts-ISO8859-1-100dpi xorg-x11-fonts-ISO8859-1-75dpi liberation-mono-fonts liberation-fonts-common liberation-sans-fonts liberation-serif-fonts

    Extras for Setup and Launch
    # yum -y install libpng12 libtiff

    # cd /usr/lib64
    # ln -s libtiff.so.5 libtiff.so.3
    ```
    - [Download Script](https://gitlab.com/snippets/1690538)


1. Download Maya

1. Install Maya


---

## Useful Links

- [How to set up the Autodesk Network License Manager on Linux](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/How-to-set-up-a-Network-License-Server-Manager-on-Linux.html)

- [Network License Administration | Finding Your Host Name and Physical Address](https://knowledge.autodesk.com/customer-service/network-license-administration/get-ready-network-license/getting-network-license-file/finding-your-host-name-and-id)

- [Lmutil error: lib64ld-lsb-x86-64.so.3: bad ELF interpreter](https://knowledge.autodesk.com/support/maya/learn-explore/caas/sfdcarticles/sfdcarticles/Lmutil-error-lib64ld-lsb-x86-64-so-3-bad-ELF-interpreter.html)

- [Maya 2018 Dependency Install Script (CentOS 7.x)](https://gitlab.com/snippets/1690538)

- [Additional Linux notes](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/CloudHelp/cloudhelp/2018/ENU/Installation-Maya/files/GUID-D2B5433C-E0D2-421B-9BD8-24FED217FD7F-htm.html)
