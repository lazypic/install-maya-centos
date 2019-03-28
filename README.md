# Maya Install CentOS 7

## Info

- 명령어 앞에 '#'는 Root(루트) 계정을 뜻한다.

- Server & User PC OS: ```CentOS7```

## Autodesk Account

1. Autodesk Account 접속 - [https://manage.autodesk.com/home/](https://manage.autodesk.com/)


## Server

1. Download Autodesk Network License Manager

    - [Autodesk Network License Manager for Linux](https://knowledge.autodesk.com/search-result/caas/downloads/content/autodesk-network-license-manager-for-linux.html)
    
    - ```nlm11.16.2.0_ipv4_ipv6_linux64.tar.gz``` 파일 내려받기


1. Install the Autodesk Network License Manager

    ```
    # tar –zxvf nlm11.16.2.0_ipv4_ipv6_linux64.tar.gz

    # rpm -vhi nlm11.16.2.0_ipv4_ipv6_linux64.rpm
    ```

    - 위에 두줄을 입력하면 /opt/flexnetserver/ 디렉토리에 라이센스 서버가 설치된다

1. Find your license server ```Host Name``` and ```Host ID``` 

    - 

## User PC

1. Download Maya

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




---

## Useful Links

- [How to set up the Autodesk Network License Manager on Linux](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/How-to-set-up-a-Network-License-Server-Manager-on-Linux.html)

- [Lmutil error: lib64ld-lsb-x86-64.so.3: bad ELF interpreter](https://knowledge.autodesk.com/support/maya/learn-explore/caas/sfdcarticles/sfdcarticles/Lmutil-error-lib64ld-lsb-x86-64-so-3-bad-ELF-interpreter.html)

- [Maya 2018 Dependency Install Script (CentOS 7.x)](https://gitlab.com/snippets/1690538)
