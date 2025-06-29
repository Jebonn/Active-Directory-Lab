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
<img src="/images/Part2/Part2.png" width="800">

## 3. Create two Virtual Machines
1. Click "Create a New Virtual Machine" and choose the "Typical (recommended)" option.
<p float="left">
  <img src="/images/Part3/Part3-Step1a.jpg" width="400"/>
  <img src="/images/Part3/Part3-Step1b.jpg" width="400"/> 
</p>

2. Choose the "I will install the operating system later." option.
3. Select Microsoft Windows and select Windows Server 2022.
<p float="left">
  <img src="/images/Part3/Part3-Step3.jpg" width="400"/>
</p>

4. The name and location of the VM can be left as is.
5. Use 32 GB for the disk size (Microsoft recommends 32 GB as the minimum).
6. A minimum of **2 GB of memory and 2 CPU cores** should be chosen. Click "Finish" to create the VM.
<p float="left">
  <img src="/images/Part3/Part3-Step6.jpg" width="400"/>
</p>

7. Once the first VM has been made, create the second VM by clicking on the "Home" tab and repeat steps 1 and 2.
8. This time, select Windows 11 x64 instead of Windows Server.
<p float="left">
  <img src="/images/Part3/Part3-Step8.jpg" width="400"/>
</p>

9. The name and location of the Windows 11 VM can be left as is.
10. The OS requires a password that will be used for encrpytion. Create or generate a password and keep it somewhere safe.
11. Use 64 GB for the disk size (Microsoft recommends 64 GB as the minimum).
12. A minimum of **4 GB of memory and 2 CPU cores** should be chosen. Click "Finish" to create the VM.
<p float="left">
  <img src="/images/Part3/Part3-Step12.jpg" width="400"/>
</p>

## 4. Install Windows Server 2022
1. After creating the two VMs, select the Windows Server VM.
2. Under "Devices", click on "CD/DVD (SATA)". Choose the "Use ISO image file" option. Click "Browse" and use the downloaded Windows Server ISO file.
<p float="left">
  <img src="/images/Part4/Part4-Step2a.jpg" width="400"/>
  <img src="/images/Part4/Part4-Step2b.jpg" width="400"/> 
</p>

3. Click "OK" to close the Settings window. Then click on "Power on this virtual machine".
4. Quickly click anywhere in the VM window and then press any key to boot using the mounted ISO file otherwise the VM will timeout.

*(NOTE: In case of timeout, restart by right-clicking on the VM then go to Power -> Shut Down, then Power On again)*
> ![boot timeout](/images/Part4/Part4-Step4.5.png)

5. If successful, a setup screen will be shown where the preferred language/time and currency/keyboard settings can be chosen. Click "Next", then click "Install".
6. Choose the "Standard Evaluation (Desktop Experience)" option. *(Desktop Experience provides a graphical user interface to manage AD rather than a command line interface)*
<p float="left">
  <img src="/images/Part4/Part4-Step6.jpg" width="400"/>
</p>

7. Accept the License Terms.
8. Choose the "Custom" install option. *(The "Upgrade" option is when there's an existing OS on the computer)*
9. Then it will ask where to install the OS. There should only one Drive shown. Simply click "Next" to start the installation.
10. The installation may take a few minutes. Once complete the VM will restart. Create a password the Administrator account then click "Finish".
<p float="left">
  <img src="/images/Part4/Part4-Step10a.jpg" width="400"/>
  <img src="/images/Part4/Part4-Step10b.jpg" width="400"/> 
</p>

## 5. Install Active Directory Domain Services (AD DS) and Group Policy Management (GPM)
1. There's a button with an icon of three boxes in the VMWare Workstation menu bar at the top. Click it to send a "Ctrl"+"Alt"+"Delete" input to the VM to unlock the OS. Then log in using the recently created Admin account and password.
<p float="left">
  <img src="/images/Part5/Part5-Step1a.jpg" width="400"/>
  <img src="/images/Part5/Part5-Step1b.jpg" width="400"/> 
</p>

*(Optional: After logging in, install VMWare Tools. It will automatically adjust screen resolution to fit the window. In the top menu bar, go to VM -> Install VMWare Tools. Open file explorer and go to DVD Drive (D:) and run the setup file. Use the "Typical" install option. Then restart after.)*
<p float="left">
  <img src="/images/Part5/Part5-Step1-(Optional).jpg" width="600"/>
</p>

2. The Server Manager window should automatically pop up. If not, it can be opened in the Start Menu. In the top right side of Server Manager, click on "Manage" -> "Add Roles and Features".
<p float="left">
  <img src="/images/Part5/Part5-Step2.jpg" width="400"/>
</p>

3. The Add Roles and Features Wizard will pop-up. Click "Next".
4. Choose the "Role-based or feature-based installation" option.
5. Server Selection can be left as is.
6. In Server Roles, check the "Active Directory Domain Services" box. A pop-up will appear showing other necessary tools along with AD DS. Click "Add Features" and click "Next"
<p float="left">
  <img src="/images/Part5/Part5-Step6a.jpg" width="400"/>
  <img src="/images/Part5/Part5-Step6b.jpg" width="400"/> 
</p>

7. In Features, check the "Group Policy Management" box.
8. Continue clicking "Next" and install. This may take a few minutes.

## 6. Promote Server to Domain Controller
1. In the top right side of Server Manager, click the flag icon. Click on "Promote this server to a domain controller".
<p float="left">
  <img src="/images/Part6/Part6-Step1.jpg" width="400"/>
</p>

2. Choose "Add a new forest". Choose a root domain name such as "ad.mydomain.com".
3. Create a Directory Services Restore Mode (DSRM) password. *(Used to restore from backups, unlikely to be needed)*
4. Continue clicking "Next" and install. After installation, the VM will restart. Log back in.
5. The Domain Controller will act as a DNS server. Following best practice, the DC will be configured with a static IP address. In the Start menu, open Command Prompt and use "ipconfig" to find the VM's IP information.
<p float="left">
  <img src="/images/Part6/Part6-Step5.jpg" width="400"/>
</p>

6. Then in the Start Menu, search "View network connections" and click on it.
<p float="left">
  <img src="/images/Part6/Part6-Step6.jpg" width="400"/>
</p>

7. Right-click on the adapter and click on "Properties". Click on "Internet Protocol Version 4" to highlight it and then click on "Properties".
<p float="left">
  <img src="/images/Part6/Part6-Step7a.jpg" width="400"/>
  <img src="/images/Part6/Part6-Step7b.jpg" width="400"/>
</p>

8. Click on "Use the following IP address" and copy the information from the Command Prompt to set a static IP address. Then click on "Use the following DNS server addresses" and use the loopback address 127.0.0.1 as the preferred DNS server.
<p float="left">
  <img src="/images/Part6/Part6-Step8.jpg" width="400"/>
</p>

## 7. Create Organization Units (OUs) & User Accounts
Now that AD DS has been installed and the server has been promoted to a Domain Controller (DC) with a static IP address, OUs and user accounts can be created.

1. In the Server Manager, click on "Tools" in the upper right, then click on the "Active Directory Users & Computers" tool.
<p float="left">
  <img src="/images/Part7/Part7-Step1.jpg" width="400"/>
</p>

2. Right-click on the domain and go to New -> Organization Unit. Choose a name for the OU such as "Sales". *(OUs can represent different departments or locations of a business)*
<p float="left">
  <img src="/images/Part7/Part7-Step2.jpg" width="400"/>
</p>

3. Right-click on the newly created OU and go to New -> User. Choose a name for the user then click "Next" and create a password for the user. For convenience, since this is only a lab, uncheck the box that says "User must change password at next logon".
<p float="left">
  <img src="/images/Part7/Part7-Step3a.jpg" width="400"/>
  <img src="/images/Part7/Part7-Step3b.jpg" width="400"/>
</p>

4. Create a few more OUs and a user within those OUs by repeating steps 2-3. *(Create other sample departments, such as Accounting or Helpdesk)*

## 8. Install Windows 11
Now that user accounts have been made, the other VM will be setup to connect to the DC.

1. Similar to installing Windows Server, select the Windows Server VM. Under "Devices", click on "CD/DVD (SATA)". Choose the "Use ISO image file" option. Click "Browse" and use the downloaded Windows 11 ISO file.
<p float="left">
  <img src="/images/Part8/Part8-Step1a.jpg" width="400"/>
  <img src="/images/Part8/Part8-Step1b.jpg" width="400"/>
</p>

2. Click "OK" to close the Settings window. Then click on "Power on this virtual machine".
3. Quickly click anywhere in the VM window and then press any key to boot using the mounted ISO file otherwise the VM will timeout.
4. If successful, a setup screen will be shown where the preferred currency, language, time, and keyboard settings can be chosen.
5. Choose the "Install Windows 11" and check the "I agree" box.
<p float="left">
  <img src="/images/Part8/Part8-Step5.jpg" width="400"/>
</p>

6. Accept the License Terms.
7. Then it will ask where to install the OS. There should only one Drive shown, if there's more than one, choose the "Primary" one with the most drive space.
8. Click "Next" and click "Install" to start the installation. This may take a while.
<p float="left">
  <img src="/images/Part8/Part8-Step8a.jpg" width="400"/>
  <img src="/images/Part8/Part8-Step8b.jpg" width="400"/>
</p>

9. Once the installation is complete, the VM will restart and will ask for a country then for a keyboard layout. Select what's appropriate and continue. The VM will restart again.
10. After restart, a Microsoft login screen should appear. Click "Sign-in options", then click "Domain join instead".
<p float="left">
  <img src="/images/Part8/Part8-Step10.jpg" width="400"/>
</p>

11. Create a name, a password, and security questions for the local account. The password will be needed to log in later.
12. Privacy settings can be left as is or turned off, then click "Accept". The OS will check for updates and may take a while.
13. After Windows 11 finishes updating, log in using the local account.
<p float="left">
  <img src="/images/Part8/Part8-Step12.jpg" width="400"/>
</p>

*(Optional: Similar to the Windows Server VM, VMWare Tools may be installed by logging into the recently created account. Then go to VM -> Install VMWare Tools in the menu bar.)*

## 9. Adding a Computer to the Domain
1. Similar to steps 6 and 7 in [Part 6](#6-promote-server-to-domain-controller), search "View network connections" and click on it. Right-click on the adapter and click on "Properties". Click on "Internet Protocol Version 4" to highlight it and then click on "Properties".
<p float="left">
  <img src="/images/Part9/Part9-Step1a.jpg" width="400"/>
  <img src="/images/Part9/Part9-Step1b.jpg" width="400"/>
</p>

2. Click on "Use the following DNS server addresses" and enter the IP address of the Domain Controller *(this is the IP address of the Windows Server VM)*. The alternate DNS server can be 8.8.8.8 which is Google's server. Click "OK".
<p float="left">
  <img src="/images/Part9/Part9-Step2.jpg" width="400"/>
</p>

3. In the Start menu, search and open "About your PC". Then scroll down and click "Domain or Workgroup".
<p float="left">
  <img src="/images/Part9/Part9-Step3a.jpg" width="400"/>
  <img src="/images/Part9/Part9-Step3b.jpg" width="400"/>
</p>

4. Click the "Change..." button and select the "Domain" option. Type the name of the Domain chosen from step 2 in [Part 6](#6-promote-server-to-domain-controller) and click "OK".
5. Enter the credentials of the Administrator account to join the domain. The VM will restart.
6. Log in using one of the user accounts created in [Part 7](#7-create-organization-units-ous--user-accounts).

