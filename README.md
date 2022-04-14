# ZNS_dev

### Based on Ubuntu 20.04 LTS kernel 5.13.0-39-generic
## Install using apt
> ```
> sudo apt update && sudo apt upgrade -y
> sudo apt-get install -y git
> sudo apt-get install -y build-essential
> sudo apt-get install -y make
> sudo apt-get install -y curl
> sudo sh -c 'curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/microsoft.gpg'
> sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
> sudo apt-get install -y unzip
> sudo apt-get install -y libtool
> sudo apt-get install -y g++
> sudo apt-get install -y nvme-cli
> sudo apt-get install -y uuid-dev
> sudo apt-get install -y gcc
> sudo apt-get install -y valgrind
> sudo apt-get install -y doxygen
> sudo apt-get install -y cmake
> sudo apt-get install -y zlib1g-dev
> sudo apt-get install -y zlib1g
> sudo apt-get install -y ninja-build
> sudo apt-get install -y meson
> sudo apt-get install -y tar
> sudo apt-get install -y fio
> sudo apt-get install -y libglib2.0
> sudo apt-get install -y autoconf
> sudo apt-get install -y aptitude
> sudo aptitude install flex
> sudo aptitude install bison
> sudo apt-get install -y cpu-checker
> sudo apt-get install -y libffi-dev
> sudo apt-get install -y libmount-dev
> sudo apt-get install -y libpcre3-dev
> sudo apt-get install -y sparse
> sudo apt-get install -y libpixman-1-dev
> sudo apt-get install -y libvirt-clients
> sudo apt-get install -y 
> sudo apt-get install -y git-email
> sudo apt-get install -y libaio-dev
> sudo apt-get install -y libbluetooth-dev
> sudo apt-get install -y libbrlapi-dev
> sudo apt-get install -y libbz2-dev
> sudo apt-get install -y libcap-ng-dev
> sudo apt-get install -y libcurl4-gnutls-dev
> sudo apt-get install -y libgtk-3-dev
> sudo apt-get install -y libibverbs-dev
> sudo apt-get install -y libjpeg8-dev
> sudo apt-get install -y libncurses5-dev
> sudo apt-get install -y libnuma-dev
> sudo apt-get install -y librbd-dev
> sudo apt-get install -y librdmacm-dev
> sudo apt-get install -y libsasl2-dev
> sudo apt-get install -y libsdl2-dev
> sudo apt-get install -y libseccomp-dev
> sudo apt-get install -y libsnappy-dev
> sudo apt-get install -y libssh-dev
> sudo apt-get install -y libvde-dev
> sudo apt-get install -y libvdeplug-dev
> sudo apt-get install -y libvte-2.91-dev
> sudo apt-get install -y libxen-dev
> sudo apt-get install -y liblzo2-dev
> sudo apt-get install -y valgrind
> sudo apt-get install -y xfslibs-dev 
> sudo apt-get install -y libnfs-dev
> sudo apt-get install -y libiscsi-dev
> sudo apt-get install -y 
> ```

### Install Virtual machine manager
> ```
> sudo apt-get install -y virt-manager
> ```

## 시스템이 KVM 가상화를 지원하는지 확인하려면 다음 명령을 실행하십시오.
> ```
> sudo kvm-ok
> ```
> ![스크린샷, 2022-04-12 15-52-15](https://user-images.githubusercontent.com/45022422/162898916-5ef22325-386d-465e-8616-18ef1c0a957a.png)


## Install QEMU
> ```
> wget https://download.qemu.org/qemu-7.0.0-rc4.tar.xz
> tar xvJf qemu-7.0.0-rc4.tar.xz
> cd qemu-7.0.0-rc4
> ./configure
> make
> make -j4
> sudo make install
> ```

+ Qemu 설치 확인
> ```
> qemu-system-x86_64 --version
> ```
> ![스크린샷, 2022-04-13 16-25-29](https://user-images.githubusercontent.com/45022422/163122872-4e840566-4775-4b16-8486-17764b630229.png)

## 우분투 설치
+ 우분투 설치 이미지 다운로드
> ```
> cd ~
> wget https://releases.ubuntu.com/focal/ubuntu-20.04.4-live-server-amd64.iso
> ```
+ 이미지 설치 디스크 생성
> ```
> qemu-img create -f qcow2 [이미지이름].img 32G
> ls -alh
> ```
+ 해당 디스크에 운영체제 설치
> ```
> 
> ```
