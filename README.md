# Active Directory Lab
## 1. Introduction
### Objective
This lab's goal is to become acquainted with virtual machines (VMs), active directory, and group policy concepts. To reach that goal, a virtual network environment will be set up using VMWare's hypervisor software and it will be used to simulate a small network that uses Active Directory Domain Services (AD DS). Sample user accounts will be created and then logically grouped under Organizational Units (OUs). Finally, the sample accounts will have various settings configured by applying Group Policy Objects (GPOs) to the OUs.
### Recommended Minimum Host Hardware
* 96 GB of available disk space
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
## 3. Create two Virtual Machines
1. After installing VMWare Workstation, run the program.
2. Click "Create a New Virtual Machine".
3. Choose the "Typical (recommended)" option.
4. Choose the "I will install the operating system later." option.
5. Select Microsoft Windows and select Windows Server 2022.
6. The name and location of the VM can be left as is.
7. Use 32 GB for the disk size (Microsoft recommends 32 GB as the minimum).
8. A minimum of **2 GB of memory and 2 CPU cores** should be chosen. Click "Finish" to create the VM.
9. Once the first VM has been made, create the second VM by clicking on the "Home" tab and repeat steps 2 - 4.
10. This time, choose Windows 11 x64 instead of Windows Server.
11. The name and location of the Windows 11 VM can be left as is.
12. The OS requires a password for encryption. Create or generate a password.
13. Use 64 GB for the disk size (Microsoft recommends 64 GB as the minimum).
14. A minimum of **4 GB of memory and 2 CPU cores** should be chosen. Click "Finish" to create the VM.

https://github.com/user-attachments/assets/0ff570b1-2c24-48d0-a827-a1ac0638ace1

## 4. Install Windows Server 2022
1. After creating the two VMs, select the Windows Server VM and click on "Edit virtual machine settings".
2. Select "CD/DVD (SATA)". Choose the "Use ISO image file" option and click "Browse". Select the downloaded Windows Server ISO file.
3. Click "OK" to close the Settings window. Then click on "Power on this virtual machine".
4. Quickly press any key to boot using the mounted ISO file otherwise the VM will timeout. *(NOTE: Restart by right-clicking on the VM then go to Power -> Shut Down)*
> ![boot timeout](/images/boot-timeout.png)

5. If successful, a setup screen will be shown where the preferred language/time and currency/keyboard settings can be chosen. Click "Next", then click "Install".
6. Choose the "Standard Evaluation (Desktop Experience)" option. *(Desktop Experience provides a graphical user interface to manage AD rather than a command line interface)*
7. Accept the License Terms.
8. Choose the "Custom" install option. *(The "Upgrade" option is when there's an existing OS on the computer)*
9. Then it will ask where to install the OS. There should only one Drive shown. Simply click "Next" to start the installation.
10. The installation may take a few minutes. Once complete the VM will restart. Create a password the Admin account then click "Finish".

https://github.com/user-attachments/assets/c855394c-b0da-45b8-9b8e-fc1b8fa08600

## 5. Install Active Directory on Windows Server
1. Log into the Administrator account. The Server Manager window should automatically pop up. If not, it can be opened in the Start Menu.
*(Optional: After log in, install VMWare Tools to have the VM automatically adjust screen resolution to fit the window. In the top menu bar, go to VM -> Install VMWare tools. Open file explorer and go to DVD Drive (D:) and run the setup file.)*
2. In the top right hand side, click on "Manage" -> "Add Roles and Features".
3. The Add Roles and Features Wizard will pop-up. Click "Next".
4. Choose the "Role-based or feature-based installation" option.
5. Server Selection can be left as is.
6. Check the "Active Directory Domain Services" box. A pop-up will appear showing other necessary tools along with AD DS. Click "Add Features".
7. Continue clicking "Next" and install AD DS. This may take a few minutes.
