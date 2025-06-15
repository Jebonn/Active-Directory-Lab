# Active Directory Lab
## Introduction
### Objective
This lab's goal is to become acquainted with virtual machines, active directory, and group policy concepts. To reach that goal, an isolated virtual network environment will be set up using VMWare's hypervisor software and it will be used to simulate a small network that uses Active Directory Domain Services (AD DS). Sample user accounts will be created and then logically grouped under Organizational Units (OUs). Finally, the sample accounts will have various settings configured by applying Group Policy Objects (GPOs) to the OUs.
### Downloadables
* VMware Workstation Pro
  * Download: [broadcom.com/group/ecx/free-downloads](https://support.broadcom.com/group/ecx/free-downloads) (requires login)
* Windows Server 2022 (64-bit edition)
  * Download: [microsoft.com/en-us/evalcenter/download-windows-server-2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022)
* Windows 11 Enterprise (64-bit edition)
  * Download: [microsoft.com/en-us/evalcenter/download-windows-11-enterprise](https://www.microsoft.com/en-us/evalcenter/download-windows-11-enterprise)
## 1. Setup Steps
### a. Download & Install
Download VMware Workstation Pro, the Win Server 2022 .ISO file, and the Win 11 .ISO file mentioned in the [Downloadables](#downloadables) section above. Then run the VMWare .exe file. An installation pop-up window will appear. Click "Next" and check the License Agreemeent box, then continue clicking "Next" through the rest of the installation pop-up windows to install. The default configurations during this process can be left as it is or customized to your preference.
![VMWare Installation Steps](/images/1a.png)
### b. Create the Virtual Machines
* After installation, open VMware Workstation and click "Create a New Virtual Machine".
