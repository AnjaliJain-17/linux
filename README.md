Assignment 2
=============

Team Member: Anjali Jain (015244151)

1. Did the assignment by myself.
2. Steps used to complete the assignment :
- Used the setup from assignment 1
- Added code in cpuid.c and vmx.c to implement the functionality for eax= 0x4FFFFFFF and 0x4FFFFFFE(as required in the question)
- make -j 8 modules
- sudo bash
- make INSTALL_MOD_STRIP=1 modules_install && make install
- lsmod | grep kvm
- rmmod kvm_intel
- rmmod kvm
- modprobe kvm
- modprobe kvm_intel
- lsmod | grep kvm
3. Steps used for testing
- Download inner virtual machine  image of CentOS distribution image using below commands:
  - wget http://mirror.math.princeton.edu/pub/centos/7.9.2009/isos/x86_64/CentOS-7-x86_64-DVD-2009.iso
- Install the packages
  - sudo apt-get install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
- Install the downloaded virtual machine image
  - virt-install  --network bridge:virbr0 --name centOSvm --os-variant=centos7.0 --ram=1024 --vcpus=1 --disk path=/var/lib/libvirt/images/centOSvm-os.qcow2,format=qcow2,bus=virtio,size=5 --graphics none  --location=CentOS-7-x86_64-DVD-2009.iso --extra-args="console=tty0 console=ttyS0,115200"  --check all=off
- Login into the inner vm
  - sudo virsh start centOSvm
  - sudo virsh console centOSvm

-Install cpuid in inner VM
  - sudo yum -y install cpuid

-Run the below commands
  - cpuid -l 0x4fffffff 
  - cpuid -l 0x4ffffffe
  ### screenshot of output 
  ![Screenshot 3](cmpe283/assignment2-output.png)
  
Assignment 1
=============

Team Member: Anjali Jain (015244151)

1. Did the assignment by myself.
2. Steps used to complete the assignment :
- Setup VMX enabled VM instance on GCP.
- Download cmpe283.c file and MakeFile (as provided by professor Mike Larkin).
- Make the code changes as required in the assignment and upload above two files to GCP VM instance.
- Fork and clone linux repository (master branch)
- Navigate to Linux directory(where the source code is cloned) and run the below commands :
  - make menuconfig
  - make oldconfig (press enter for the selecting the default answers)
  - make prepare
  - make -j 8 modules
  - make -j 8 
  - sudo make INSTALL_MOD_STRIP=1 modules_install
  - sudo make install (installs module)
  - sudo reboot (reboots to apply the changes of the latest version of kernal)
  - uname -a (should reflect the latest version of the kernal)
- While following the above step,install all the missing packages i.e git, make, gcc, build-essential, sslclient etc to successfully build the kernal module.
- Run the "make" command. There will be an error of missing module license. Open the cmpe283-1.c file and add (MODULE_LICENSE("GPL v2");) at the end of the file and save the changes
- Execute the make command again.After it is successfully executed, check that the .ko file is created using "lsmod | grep cmpe283"
- Insert module using sudo insmod cmpe283-1.ko
- To Unload a module use (sudo rmmmod cmpe283-1)
- run "dmesg" command to see the output of the code
- Commit & push the changes to git using below commands
  - git add
  - git commit -m "This is assignment1 of CMPE283"
  - git push
Output:
### Screenshot 1
![Screenshot 1](cmpe283/output-1.png)
### Screenshot 2
![Screenshot 2](cmpe283/output-2.png)
