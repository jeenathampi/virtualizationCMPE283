Assignment 1: Contribution by Jeena Thampi and Anisha Agarwal
Part 1: Environment Setup
Setup on MAC: (Done by Jeena Thampi)
1.	Downloaded and installed VMware Fusion Pro.
2.	Download Ubuntu Desktop 20.04LTS from ubuntu.com
3.	Created an Outer VM of host OS as Linux
a.	Browsed ISO image of downloaded Ubuntu so that the host OS is Linux.
b.	Changed the disc space to 200GB.
c.	Memory – 4GB.
d.	Processors – 2.
e.	For enabling Nested Virtualization, check the “Enable hypervisor applications in this virtual machine option”. You will find this option under advanced options of the Processors & Memory screen of the VM you would want to perform nested virtualization.
f.	Check this option with command kvm-ok. 
g.	If error is thrown “Command 'kvm-ok' not found”, install it using command “sudo apt install cpu-checker”   O/P INFO: /dev/kvm exists. KVM acceleration can be used.
Setup done on Windows: (Done by Anisha Agarwal)
1.	Downloaded and installed VMware Workstation 16 Pro.
2.	Download Ubuntu Desktop 20.04LTS from ubuntu.com
3.	Created an Outer VM of host OS as Linux
a.	Browsed ISO image of downloaded Ubuntu so that the host OS is Linux.
b.	Changed the disc space to 200GB.
c.	Memory – 4GB.
d.	Processors – 2.
e.	For enabling Nested Virtualization, check the “Virtualize Intel VT-x/EPT or AMD-V-RI” and “Virtualize CPU performance counters”. You will find this option under Hardware Settings->Processors of the VM you would want to perform nested virtualization.
f.	Not able to set up the Nested environment on Windows.
g.	Tried many other scenarios, did research and found that Windows do not support VMware and do support Hyper-V. Not sure what to use.
Verify if the setup is done correctly for nested virtualization:
Working on MAC
1.	Run command  “/proc/cpuinfo | more” and check in the output if VMX flag exists. If it exits then the setup is ready for Nested Virtualization. In our case it is present.
Not Working on Windows
1.	Run command  “/proc/cpuinfo | more” VMX flag does not exists.
Part 2: Functionality Implementation 
Done by Jeena Thampi
1.	Fork the linux master github URL from https://github.com/torvalds/linux to the local VM.
2.	In order to fork the Master Linux, first install git to your VM by using command “sudo apt install git”.
3.	git clone https://github.com/jeenathampi/linux.git
4.	To go ahead and implement the functionality, install the make file and cmpe283-1.c provided in canvas, using command “sudo apt install make”
5.	If it throws error saying make file do not exist, Install gcc by using command “sudo apt install gcc”
6.	Install make file now.
7.	Install Editors like VIM by using command “sudo apt install vim”.
8.	Modified the C file as per the requirement to create a kernel module, load the new module and verified proper output.
a.	Modified the length of the array of each control 
b.	created a structure for the controls referring SDM.
9.	Referred SDM Vol.3 section 24.6.1 for Pin-Based VM execution controls, SDM vol.3 section 24.6.2 for Processor-Based VM-Execution Controls for both primary and secondary type.
10.	To build the code use command make.
11.	Cmpe283-1.ko will be created after the successful build which is the object/module which can load to kernel
12.	Run sudo insmod ./cmpe283-1.ko to insert the module.
13.	Run dmesg to see the output.
14.	As a result we can see the different controls of the MSR’S which we can turn it on or off according to the output.
Done by Anisha Agarwal:
1.	Modified the C file as per the requirement to create a kernel module, load the new module and verified proper output.
a.	Modified the length of the array of each control 
b.	created a structure for the controls referring SDM
c.	Referred SDM vol.3 24.7.1 for VM-Exits Control and SDM vol.3 24.8.1 for VM-Entry Controls. 
Documentation: ReadMe prepared by Anisha Agarwal.


