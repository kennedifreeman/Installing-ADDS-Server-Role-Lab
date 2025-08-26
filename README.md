<h1>AD DS Server Role Lab</h1>

<h2>Description</h2>
In this Server Academy lab, I configured a Windows Server (SADC01) as an Active Directory Domain Controller. The project involved assigning a static IP address, installing the Active Directory Domain Services (AD DS) role, and promoting the server to a Domain Controller with a new forest (lab.local). After deployment, I verified the setup using both Active Directory Users and Computers (ADUC) and command-line tools.

This lab provided hands-on experience with Windows Server administration, including network configuration, role installation, and domain verification—core skills required for managing enterprise IT environments.


<br />

<h2>Project Highlights</h2>

<b> 
> Platform: Server Academy  
> Environment: Windows Server (Browser-based Lab)  <br>
> Skills Practiced: Static IP config, AD DS role install, DC promotion, DNS/DSRM basics, verification via ADUC/CLI <br> 
> Objectives: Configure networking, install AD DS, promote to Domain Controller, verify domain  <br>
> Tools Used: Server Manager, AD DS, Active Directory Users and Computers (ADUC), Command Prompt  <br>
> Difficulty Level: 🟢 Beginner-Friendly  <br>
</b>

<h2>Program walk-through:</h2>

<p align="center">
🛠 Step 1: Configure the IP Address <br/>
<p align="left">
After logging into the Server Academy lab environment:<br>
 1. Open Server Manager from the Start Menu. <br>
2. On the left panel, click Local Server. <br>
3. In the Properties section, find the network adapter (Ethernet) link. Click it to open the Network Connections window. <br>
4. Right-click the active adapter → Properties. <br>
5. Select Internet Protocol Version 4 (TCP/IPv4) → Properties. <br>
6. Change from *Obtain an IP address automatically* to **Use the following IP address**. <br>
     - IP Address: 10.1.0.10 <br>
     - Subnet Mask: 255.255.255.0 <br>
     - Default Gateway: 10.1.0.1 <br>
7. Under DNS settings, set the Preferred DNS Server to 10.0.0.1 (this will later loop back to the domain controller).  <br>
8. Click OK → Close.  <br>
9. Open Command Prompt and verify with:  <br>
   ipconfig /all <br>



Confirm that the adapter now shows 10.1.0.10.

<br />
<br />
<p align="center">
👤 Step 2 – 🛠 Install Active Directory Domain Services (AD DS)  <br/>
<p align="left">
1. Back in Server Manager, click Manage → Add Roles and Features. <br>
2. In the wizard: <br>
   - Installation Type: Role-based or feature-based. <br>
   - Server Selection: Choose the local server (SADC01). <br>
   - Server Roles: Check Active Directory Domain Services. <br>
   - A pop-up will appear asking to add required features → click Add Features. <br>
   - Continue with defaults through the Features section. <br>
3. On the confirmation page, leave Restart the destination server automatically if required unchecked (manual restart is better). <br>
4. Click Install. <br>
5. Wait for installation to finish. Do not close Server Manager.

<br />
<br />
<p align="center">
🔄 Step 3 – 🌐 Promote SADC01 to a Domain Controller <br/>
<p align="left">
1. Once AD DS finishes installing, a yellow triangle notification appears in Server Manager (top right). <br>
2. Click the notification → Promote this server to a domain controller. <br> 
3. In the Deployment Configuration window: <br>
   - Select Add a new forest. <br>
   - Enter a Root domain name, e.g., lab.local.  <br>
4. In the Domain Controller Options: <br>
   - Leave Domain Name System (DNS) server checked. <br>
   - Specify a Directory Services Restore Mode (DSRM) password (used for recovery mode). <br>
5. Skip additional options unless custom delegation is required. <br>
6. The wizard runs prerequisite checks → click Install. <br>
7. The server will restart automatically to complete promotion. <br>

<br />
<br />
<p align="center">
🔀 Step 4 – 🔎 Verify Domain Controller Setup  <br/>
<p align="left">
1. Log back in to SADC01 (note: you may now log in using the domain context if available). <br>
2. Open Server Manager → Tools → Active Directory Users and Computers (ADUC).  <br>
3. Click yes to confirm the move. <br>


<br />
<br />

<h2>Key Takeaways:</h2>
  📌 Key Takeaways <br>
- Static IP before AD DS: A Domain Controller must always have a fixed IP; DHCP-assigned addresses cause domain issues. <br> 
- Server Manager is central: All installs, promotions, and ADUC access are done from Server Manager → Tools. <br>
- DSRM password: This recovery password is critical in disaster recovery scenarios. <br>

 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
