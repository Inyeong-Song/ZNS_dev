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
> sudo apt-get install -y 
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
> make -j$(nproc)
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

