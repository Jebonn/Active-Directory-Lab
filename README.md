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
1. Download VMware Workstation Pro, the Win Server 2022 .ISO file, and the Win 11 .ISO file mentioned in the [Downloadables](#downloadables) section above.
2. Run VMWare .exe file. An installation pop-up window will appear. Click "Next" and check the License Agreemeent box.
3. Then continue clicking "Next" through the rest of the installation pop-up windows to install. The default configurations during this process can be left as is or customized to preference.
4. Once installation is complete, click "Finish" and open the program.
<img src="/images/Part2.png" width="800">

## 3. Create two Virtual Machines
1. Click "Create a New Virtual Machine" and choose the "Typical (recommended)" option.
<p float="left">
  <img src="/images/Part3-Step1a.jpg" width="400"/>
  <img src="/images/Part3-Step1b.jpg" width="400"/> 
</p>

2. Choose the "I will install the operating system later." option.
3. Select Microsoft Windows and select Windows Server 2022.
<p float="left">
  <img src="/images/Part3-Step3.jpg"/>
</p>

4. The name and location of the VM can be left as is.
5. Use 32 GB for the disk size (Microsoft recommends 32 GB as the minimum).
6. A minimum of **2 GB of memory and 2 CPU cores** should be chosen. Click "Finish" to create the VM.
<p float="left">
  <img src="/images/Part3-Step6.jpg" width="400"/>
</p>

7. Once the first VM has been made, create the second VM by clicking on the "Home" tab and repeat steps 1 and 2.
8. This time, select Windows 11 x64 instead of Windows Server.
<p float="left">
  <img src="/images/Part3-Step8.jpg" width="400"/>
</p>

9. The name and location of the Windows 11 VM can be left as is.
10. The OS requires a password that will be used for encrpytion. Create a password and keep it somewhere safe.
11. Use 64 GB for the disk size (Microsoft recommends 64 GB as the minimum).
12. A minimum of **4 GB of memory and 2 CPU cores** should be chosen. Click "Finish" to create the VM.

## 4. Install Windows Server 2022
1. After creating the two VMs, select the Windows Server VM and click on "Edit virtual machine settings".
2. Select "CD/DVD (SATA)". Choose the "Use ISO image file" option and click "Browse". Select the downloaded Windows Server ISO file.
3. Click "OK" to close the Settings window. Then click on "Power on this virtual machine".
4. Quickly press any key to boot using the mounted ISO file otherwise the VM will timeout. *(NOTE: Restart by right-clicking on the VM then go to Power -> Shut Down)*
> ![boot timeout](/images/Part4-Step4.5.png)

5. If successful, a setup screen will be shown where the preferred language/time and currency/keyboard settings can be chosen. Click "Next", then click "Install".
6. Choose the "Standard Evaluation (Desktop Experience)" option. *(Desktop Experience provides a graphical user interface to manage AD rather than a command line interface)*
7. Accept the License Terms.
8. Choose the "Custom" install option. *(The "Upgrade" option is when there's an existing OS on the computer)*
9. Then it will ask where to install the OS. There should only one Drive shown. Simply click "Next" to start the installation.
10. The installation may take a few minutes. Once complete the VM will restart. Create a password the Admin account then click "Finish".

## 5. Install Active Directory Domain Services (AD DS) on Windows Server
1. Log into the Administrator account. The Server Manager window should automatically pop up. If not, it can be opened in the Start Menu.

*(Optional: After log in, install VMWare Tools so that VMWare will automatically adjust screen resolution to fit the window. In the top menu bar, go to VM -> Install VMWare tools. Open file explorer and go to DVD Drive (D:) and run the setup file.)*
<img src="/images/Part5-Step1-(Optional).jpg" width="800">

2. In the top right side of Server Manager, click on "Manage" -> "Add Roles and Features".
3. The Add Roles and Features Wizard will pop-up. Click "Next".
4. Choose the "Role-based or feature-based installation" option.
5. Server Selection can be left as is.
6. Check the "Active Directory Domain Services" box. A pop-up will appear showing other necessary tools along with AD DS. Click "Add Features".
7. Continue clicking "Next" and install AD DS. This may take a few minutes.

## 6. Promote Server to Domain Controller
1. In the top right side of Server Manager, click the flag icon. Click on "Promote this server to a domain controller".
2. Choose "Add a new forest". Choose a root domain name such as "ad.mydomain.com".
3. Create a Directory Servicdes Restore Mode (DSRM) password. (Used to restore from backups, unlikely to be needed)
4. Continue clicking "Next" and install. After installation, the VM will restart.

## 7. Create Organization Units (OUs) & User Accounts
Log into the Admin account. Now that AD DS has been installed and the server has been promoted to a Domain Controller (DC), OUs and user accounts can be created.

1. In the Server Manager, click on "Tools" in the upper right, then click on the "Active Directory Users & Computers" tool.
2. Right-click on the domain and go to New -> Organization Unit. Choose a name for the OU such as "Sales". *(OUs can represent different departments or locations of a business)*
3. Right-click on the newly created OU and this time create a new user.
4. Create other users and other OUs such as "Customer Support" or "Accounting" by repeating steps 2-3 a couple more times.

## 8. Install Windows 11
1.
