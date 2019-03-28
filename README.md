# Maya Install CentOS 7

## Info

- 명령어 앞에 '#'는 Root(루트) 계정을 뜻한다.

- License Server & Client Computer OS: ```CentOS7```

- Maya Version: ```2018```

- 내려받은 파일들은 ```~/Downloads``` 디렉토리에 저장

- yum 명령어는 인터넷을 사용한다.

## License Server

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

1. 라이센스 서버의 ```Host Name``` 과 ```Host ID``` 
    
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
    
    <참고>
    Host ID 가 여러개 출력되면 첫번째 주소를 사용한다.
    ```
    
    ```
    <오류>
    '/lib64/ld-lsb-x86-64.so.3: bad ELF interpreter: No such file or directory'
    
    <해결 방법>
    # yum -y install redhat-lsb
    ```
    
1. Autodesk Account에서 네트워크 라이센스 파일을 생성하기

    1. Autodesk Account 접속 - [https://manage.autodesk.com/home/](https://manage.autodesk.com/)
        - OTP | Google Authenticator
        
    1. 라이센스 서버 모델 선택
    
    1. 사용 가능한 제품 선택
    
    1. 라이센스 파일 생성
        ![Generate the License File](https://knowledge.autodesk.com/sites/default/files/images/account-server-single-get-650.jpg)
    
    1. 

    1. 라이센스(.lic) 파일을 ```/opt/flexnetserver``` 디렉토리에 저장한다.
        - ```ex) /opt/flexnetserver/adsk_license.lic```


1. 네트워크 라이센스 서버를 시작하기
    ```
    #cd /opt/flexnetserver
    
    # ./lmgrd -c /opt/flexnetserver/adsk_license.lic -l /opt/flexnetserver/server_log.log
    ex) # ./lmgrd -c /opt/flexnetserver/storage6003089af239.lic -l /opt/flexnetserver/server_log.log
    ```

1. 라이센스 서버 상태 쿼리를 얻기
    ```
    #cd /opt/flexnetserver
    
    # ./lmutil lmstat -a -c /opt/flexnetserver/adsk_license.lic
    ex) # ./lmutil lmstat -a -c /opt/flexnetserver/storage6003089af239.lic
    ```

### 참고

1. 라이센스 서버 서비스를 중지하기
    ```
    #cd /opt/flexnetserver
    
    # ./lmutil lmdown -q -force
    ```

1. 시스템을 재부팅한 후 라이센스 서버를 자동으로 시작하기
    ```
    # chmod +x /etc/rc.d/rc.local
    
    # vim /etc/rc.d/rc.local
        >> touch /var/lock/subsys/local 
        >> /opt/flexnetserver/lmgrd -c /opt/flexnetserver/adsk_license.lic -l /opt/flexnetserver/server_log.log 
    ```


## Client Computer

1. Install Dependencies
    
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

1. [Install Maya on Linux using the installation wizard](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/CloudHelp/cloudhelp/2018/ENU/Installation-Maya/files/GUID-10FE31A8-7092-45BE-9E53-44D0D096E431-htm.html)

    - 다운로드한 마야 앞축파일을 풀어준다    
    ```
    # cd ~/Downloads
    # mkdir maya2018
    # mv Autodesk_Maya_2018_EN_Linux_64bit.tgz maya2018
    # tar –zxvf Autodesk_Maya_2018_EN_Linux_64bit.tgz
    
    # ./setup
    ```
    
    - Installation Wizard
    

---

## Useful Links

- [How to set up the Autodesk Network License Manager on Linux](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/sfdcarticles/sfdcarticles/How-to-set-up-a-Network-License-Server-Manager-on-Linux.html)

- [Network License Administration | Finding Your Host Name and Physical Address](https://knowledge.autodesk.com/customer-service/network-license-administration/get-ready-network-license/getting-network-license-file/finding-your-host-name-and-id)

- [Lmutil error: lib64ld-lsb-x86-64.so.3: bad ELF interpreter](https://knowledge.autodesk.com/support/maya/learn-explore/caas/sfdcarticles/sfdcarticles/Lmutil-error-lib64ld-lsb-x86-64-so-3-bad-ELF-interpreter.html)

- [Maya 2018 Dependency Install Script (CentOS 7.x)](https://gitlab.com/snippets/1690538)

- [Additional Linux notes](https://knowledge.autodesk.com/support/maya/troubleshooting/caas/CloudHelp/cloudhelp/2018/ENU/Installation-Maya/files/GUID-D2B5433C-E0D2-421B-9BD8-24FED217FD7F-htm.html)
