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
