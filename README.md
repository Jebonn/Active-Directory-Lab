# Active Directory Lab
## 1. Introduction
### Objective
This lab's goal is to become acquainted with virtual machines (VMs), active directory, and group policy concepts. To reach that goal, a virtual network environment will be set up using VMWare's hypervisor software and it will be used to simulate a small network that uses Active Directory Domain Services (AD DS). Sample user accounts will be created and then logically grouped under Organizational Units (OUs). Finally, the sample accounts will have various settings configured by applying Group Policy Objects (GPOs) to the OUs.
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
9. *(Optional) more RAM and cores may be allocated to help speed up the installation process of Windows Server 2022 and Active Directory in the next couple of steps. Once installed, the allocation can be reverted back.*

> https://github.com/user-attachments/assets/c75774ee-c3c5-49ea-a81f-b579ff695e59

## 4. Install Windows Server 2022
1. After creating the VM, click on "Edit virtual machine settings".
2. In the Settings window, select "CD/DVD (SATA)". Choose the "Use ISO image file" option and click "Browse". Navigate to where the Windows Server ISO file was downloaded and select it.
3. Click "OK" to close the Settings window. Then click on "Power on this virtual machine".
4. Quickly press any key to boot using the mounted ISO file. *(NOTE: If you missed this, it will time out. The VM can be restarted by right-clicking on it and go to Power > Power Off)*
> ![boot timeout](/images/boot-timeout.png)

5. If successful, a setup screen will be shown where the preferred language/time and currency/keyboard settings can be chosen. Click "Next", then click "Install".
6. Choose the "Standard Evaluation (Desktop Experience)" option. *(Desktop Experience provides a graphical user interface to manage AD, instead of a command line interface)*
7. Accept the License Terms.
8. Choose the "Custom" install option. *(The "Upgrade" option is when there's an existing OS on the computer)*
9. Then it will ask where to install the OS. There should only one Drive shown. Simply click "Next" to start the installation.
10. Once the installtion is complete, enter a password for the Administrator account. Then click "Finish".
