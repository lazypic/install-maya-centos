# Maya Install CentOS 7

## Server

1. Download Autodesk Network License Manager

1. Install the Autodesk Network License Manager

```
(# = Root 권한)

# tar –zxvf nlm11.16.2.0_ipv4_ipv6_linux64.tar.gz

# rpm -vhi nlm11.16.2.0_ipv4_ipv6_linux64.rpm
```

위에 두줄을 입력하면 /opt/flexnetserver/ 디렉토리에 라이센스 서버가 설치된다



## User PC

1. Install Dependencies (인터넷 필요)
    - [Download Script](https://gitlab.com/snippets/1690538)

```
(# = Root 권한)

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




---

## Useful Links

- [How to set up the Autodesk Network License Manager on Linux](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/How-to-set-up-a-Network-License-Server-Manager-on-Linux.html)

- [Lmutil error: lib64ld-lsb-x86-64.so.3: bad ELF interpreter](https://knowledge.autodesk.com/support/maya/learn-explore/caas/sfdcarticles/sfdcarticles/Lmutil-error-lib64ld-lsb-x86-64-so-3-bad-ELF-interpreter.html)

- [Maya 2018 Dependency Install Script (CentOS 7.x)](https://gitlab.com/snippets/1690538)
