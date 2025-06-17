# Active Directory Lab
## Introduction
### 1. Objective
This lab's goal is to become acquainted with virtual machines, active directory, and group policy concepts. To reach that goal, an isolated virtual network environment will be set up using VMWare's hypervisor software and it will be used to simulate a small network that uses Active Directory Domain Services (AD DS). Sample user accounts will be created and then logically grouped under Organizational Units (OUs). Finally, the sample accounts will have various settings configured by applying Group Policy Objects (GPOs) to the OUs.
### Recommended Minimum Host Hardware
* 256 GB Disk Space
* 12 GB RAM
* 6 Core CPU

### Downloadables
* VMware Workstation Pro
  * Download: [broadcom.com/group/ecx/free-downloads](https://support.broadcom.com/group/ecx/free-downloads) (requires login)
* Windows Server 2022 (64-bit edition)
  * Download: [microsoft.com/en-us/evalcenter/download-windows-server-2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
* Windows 11 Enterprise (64-bit edition)
  * Download: [microsoft.com/en-us/evalcenter/download-windows-11-enterprise](https://www.microsoft.com/en-us/evalcenter/download-windows-11-enterprise)
## 2. Download & Install
Download VMware Workstation Pro, the Win Server 2022 .ISO file, and the Win 11 .ISO file mentioned in the [Downloadables](#downloadables) section above. Then run the VMWare .exe file. An installation pop-up window will appear. Click "Next" and check the License Agreemeent box, then continue clicking "Next" through the rest of the installation pop-up windows to install. The default configurations during this process can be left as is or customized to preference.

> ![VMWare Installation Steps](/images/1a.png)
## 3. Create a Virtual Machine
1. After installing VMWare Workstation, run the program.
2. Click "Create a New Virtual Machine".
3. Choose the "Typical (recommended)" option.
4. Choose "I will install the operating system later." option.
5. Select Microsoft Windows and select Windows Server 2022.
6. The name and location of the VM can be left as is.
7. Use 32 GB for the disk size (Microsoft recommends 32 GB as the absolute minimum).
8. A minimum of 2 GB RAM and 2 CPU cores should be chosen. Click "Finish" to create the VM.
9. *(Optional) more RAM and cores may be allocated to help speed up the installation process of Windows Server 2022 and Active Directory in later steps. Once installed, the allocation can be reverted back after.*
## 4. Install Windows Server 2022

