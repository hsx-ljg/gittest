#### How to use FaceSDK on Debian
* Download and install Debian on VMware, recommend this version http://cdimage.debian.org/debian-cd/8.5.0/multi-arch/iso-cd/debian-8.5.0-amd64-i386-netinst.iso
* Follow the below commands to install OpenCV2.4
```
user1@debian:~/work$ sudo apt-get udpate
user1@debian:~/work$ sudo apt-get install libopencv-dev
```
* Get FaceSDK from github  
```
user1@debian:~/work$ git clone git@github.azc.ext.hp.com:qian-lin/FaceSDK_Debian.git
```
* Modify **sDataTestPath**'s value in shell file, which point to your input file's directory
```Bash
user1@debian:~/work/FaceSDK/Linux/FaceCluster/bin$ ls
FaceClusterTest  test_d.sh  test_f.sh  test_i.sh
user1@debian:~/work/FaceSDK/Linux/FaceCluster/bin$ cat test_d.sh 
#!/bin/sh
sDataPath=../../Data
sDataTestPath=../../../../DataTest/comm/photos6/  
sOutputPath=../../../../DataTest/FaceCluster/out3
./FaceClusterTest -i $sDataTestPath -o $sOutputPath -d $sDataPath -r true -c true
```
* run shell file 
```Bash
user1@debian:~/work/FaceSDK/Linux/FaceCluster/bin$ ./test_d.sh 
```