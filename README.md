# ZNS_dev

### Based on Ubuntu 20.04 LTS kernel 5.13.0-39-generic
## Install using apt (local system)
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

### Install Virtual machine manager (local system)
> ```
> sudo apt-get install -y virt-manager
> ```

### Install vnc viewer (local system)
> ```
> https://www.realvnc.com/en/connect/download/viewer/linux/
> ```

## 시스템이 KVM 가상화를 지원하는지 확인하려면 다음 명령을 실행 (local system)
> ```
> sudo kvm-ok
> ```
> ![스크린샷, 2022-04-12 15-52-15](https://user-images.githubusercontent.com/45022422/162898916-5ef22325-386d-465e-8616-18ef1c0a957a.png)


## Install QEMU (local system)
> ```
> wget https://download.qemu.org/qemu-7.0.0-rc4.tar.xz
> tar xvJf qemu-7.0.0-rc4.tar.xz
> cd qemu-7.0.0-rc4
> ./configure
> make
> make -j4
> sudo make install
> ```

+ Qemu 설치 확인 (local system)
> ```
> qemu-system-x86_64 --version
> ```
> ![스크린샷, 2022-04-13 16-25-29](https://user-images.githubusercontent.com/45022422/163122872-4e840566-4775-4b16-8486-17764b630229.png)

## QEMU에 우분투 설치
+ 우분투 설치 이미지 다운로드 (local system)
> ```
> cd ~
> wget https://releases.ubuntu.com/focal/ubuntu-20.04.4-live-server-amd64.iso
> 또는
> wget http://releases.ubuntu.com/22.04/ubuntu-22.04-live-server-amd64.iso
> ```
+ 이미지 설치 디스크 생성 (local system)
> ```
> qemu-img create -f qcow2 ubuntu.img 64G
> ls -alh
> ```
+ 해당 디스크에 운영체제 설치 (local system)
> ```
> sudo qemu-system-x86_64 \
> -m 8G \
> -enable-kvm \
> -hda ubuntu.img \
> -cdrom ubuntu-22.04-live-server-amd64.iso \
> -boot d \
> -vga virtio \
> -vnc :2
> ```
+ VNC viewer VM 접속 (local system)
> ```
> vncviewer 127.0.0.1:5902
> ```
+ 업데이트 가능한 커널 확인 (virtual system)
> ```
> sudo apt-cache search linux-image-5.10
> ```
+ 커널 업데이트 (virtual system)
> ```
> sudo apt update -y && sudo apt upgrade -y
> sudo apt install linux-image-5.10.0-1057-oem -y
> ```
+ QEMU 재실행 (local system)
> ```
> sudo qemu-system-x86_64 \
> -hda ubuntu.img \
> -m 8G \
> -smp 4 \
> -cpu host \
> --enable-kvm \
> -vga virtio \
> -vnc :2
> ```

### ZNS 에뮬레이션
+ ZNS를 에뮬레이션하기 위한 디스크 생성 (8GiB 생성) (local system)
> ```
> dd if=/dev/zero of=zns.raw bs=1M count=8192
> ```
+ Creating a ZNS and using the Backstore File (local system)
> ```
> sudo qemu-system-x86_64 \
> -hda ubuntu.img \
> -m 8G \
> -smp 4 \
> -cpu host \
> --enable-kvm \
> -vga virtio \
> -vnc :2 \
> -device nvme,id=nvme0,serial=deadbeef,zoned.zasl=5 \
> -drive file=zns.raw,id=nvmezns0,format=raw,if=none \
> -device nvme-ns,drive=nvmezns0,bus=nvme0,nsid=1,logical_block_size=4096,\
> physical_block_size=4096,zoned=true,zoned.zone_size=64M,zoned.\
> zone_capacity=62M,zoned.max_open=16,zoned.max_active=32,\
> uuid=5e40ec5f-eeb6-4317-bc5e-c919796a5f79 \
> -net user,hostfwd=tcp::2222-:22 \
> -net nic \
> ```
+ ZNS 동작 확인 (virtual system)
> ```
> sudo apt install nvme-cli
> sudo nvme list
> sudo blkzone report /dev/nvme0n1 | less
> ```
### SSH로 QEMU와 통신하기
+ How to Transfer files between the Host and Qemu via SSH and NFS (local system)
+ https://www.cnx-software.com/2011/10/02/how-to-transfer-files-between-host-and-qemu-via-ssh-and-nfs/
> ```
> sudo apt-get install dropbear
> ```

### FEMU 설치
+ FEMU 우분투 이미지 다운로드 (local system)
> ```
> mkdir -p ~/images
> cd ~/images
> wget http://people.cs.uchicago.edu/~huaicheng/femu/femu-vm.tar.xz
> tar -xJvf femu-vm.tar.xz
> ```
> After these steps, you will get two files: "u20s.qcow2" and "u20s.md5sum".
+ 이미지 검증 과정 (local system)
> ```
> md5sum u20s.qcow2 > tmp.md5sum
> diff tmp.md5sum u20s.md5sum
> ```
> If diff complains that the above two files differ, then the VM image file is corrupted.
> Please redo the above steps.
+ The user account and guest OS of the VM:
> ```
> username: femu
> passwd : femu
> Guest OS: Ubuntu 20.04.1 server, with kernel 5.4
> ```
+ FEMU 컴파일 및 실행 (local system)
> ```
> git clone https://github.com/ucare-uchicago/femu.git
> cd femu
> mkdir build-femu
+ FEMU 빌드 디렉터리로 변경
> ```
> cd build-femu
> ```
+ FEMU 사용에 필요한 스크립트들의 복사 과정 (local system)
> ```
> cp ../femu-scripts/femu-copy-scripts.sh .
> ./femu-copy-scripts.sh .
> sudo ./pkgdep.sh # 데비안 및 우분투에서만 수행
> ./femu-compile.sh
> ```
