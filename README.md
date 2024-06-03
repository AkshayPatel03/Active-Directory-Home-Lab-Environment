# Active Directory Home Lab Environment

This project demonstrates how I created a Microsoft Active Directory home lab environment using VirtualBox. This setup simulates a business environment by configuring a Domain Controller, setting up various network services, and creating over 1000 users using a PowerShell script. This project highlights my skills in network administration, Active Directory management, and virtualization.

## Prerequisites

Before starting, ensure you have the following:

- Microsoft Server 2019 ISO
- Windows 10 Enterprise ISO
- VirtualBox installed on your host machine
- PowerShell script for user creation
- Basic knowledge of networking and Active Directory concepts

## Project Steps

### 1. Setting Up the Virtual Environment

#### Install VirtualBox
First, I downloaded and installed VirtualBox from [VirtualBox](https://www.virtualbox.org/).

![Install VirtualBox](path/to/screenshot1.png)

#### Create Virtual Machines
I created two virtual machines: one for the Microsoft Server 2019 and one for Windows 10 Enterprise.

- **Microsoft Server 2019 VM**: Configured with at least 2GB of RAM and 40GB of storage, attaching the Server 2019 ISO.

  ![Create Server VM](path/to/screenshot2.png)

- **Windows 10 Enterprise VM**: Configured with similar specs and attached the Windows 10 Enterprise ISO.

  ![Create Client VM](path/to/screenshot3.png)

### 2. Installing Microsoft Server 2019

#### Attach ISO and Boot
I booted the Server 2019 VM with the ISO attached.

![Attach Server ISO](path/to/screenshot4.png)

#### Install Server 2019
I followed the installation wizard to set up the server, ensuring to set a strong Administrator password.

![Install Server 2019](path/to/screenshot5.png)

### 3. Configuring Network Settings

#### Network Adapter Configuration
I ensured the network adapters were set to either NAT or Bridged mode in VirtualBox and assigned static IP addresses to both the Server and Client VMs.

![Network Settings](path/to/screenshot6.png)

### 4. Installing Active Directory Domain Services (AD DS)

#### Open Server Manager
I opened the Server Manager on the Microsoft Server 2019.

![Open Server Manager](path/to/screenshot7.png)

#### Add Roles and Features
In Server Manager, I added roles and features, selecting Active Directory Domain Services.

![Add Roles and Features](path/to/screenshot8.png)

#### Promote to Domain Controller
After installing AD DS, I promoted the server to a Domain Controller, creating a new forest and domain (e.g., `myhomelab.local`).

![Promote to Domain Controller](path/to/screenshot9.png)

### 5. Configuring DHCP Server

#### Open Server Manager
I reopened the Server Manager to add new roles and features.

![Open Server Manager](path/to/screenshot10.png)

#### Add DHCP Role
I selected the DHCP Server role.

![Add DHCP Role](path/to/screenshot11.png)

#### Configure DHCP Scope
I configured the DHCP scope, setting the IP address range, subnet mask, gateway, and DNS settings.

![Configure DHCP Scope](path/to/screenshot12.png)

### 6. Setting Up NAT (Network Address Translation)

#### Open Routing and Remote Access Service (RRAS)
I configured NAT using the Routing and Remote Access Service to allow the virtual network to access the internet.

![Set Up NAT](path/to/screenshot13.png)

### 7. Setting Up Remote Access Service (RAS)

#### Open Server Manager
I opened the Server Manager once again to add roles and features.

![Open Server Manager](path/to/screenshot14.png)

#### Add RAS Role
I selected the Remote Access Service role.

![Add RAS Role](path/to/screenshot15.png)

#### Configure VPN and DirectAccess
I configured VPN and DirectAccess for remote access as needed.

![Configure VPN and DirectAccess](path/to/screenshot16.png)

### 8. Creating Users Using PowerShell Script

#### PowerShell Script
I used the following PowerShell script to create multiple users:

```powershell
Import-Module ActiveDirectory
for ($i=1; $i -le 1000; $i++) {
    $username = "User$i"
    $password = ConvertTo-SecureString "Password123!" -AsPlainText -Force
    New-ADUser -Name $username -AccountPassword $password -PasswordNeverExpires $true -Enabled $true
}
```

#### Run the Script
I executed the script on the Domain Controller to create the users.

![Run PowerShell Script](path/to/screenshot17.png)

### 9. Setting Up the Windows 10 Enterprise Client

#### Install Windows 10
I booted the Windows 10 VM with the ISO attached and completed the installation process.

![Install Windows 10](path/to/screenshot18.png)

#### Join Domain
I joined the client to the domain `myhomelab.local` and logged in using one of the newly created user accounts.

![Join Domain](path/to/screenshot19.png)

### 10. Verifying the Setup

#### Test User Logins
I tested logging in with multiple user accounts on the client machine to ensure proper setup.

![Test User Logins](path/to/screenshot20.png)

#### Internet Access
I verified that the client could access the internet through the configured NAT.

![Internet Access](path/to/screenshot21.png)

#### DHCP Verification
I confirmed that DHCP was providing IP addresses correctly to devices on the network.

![DHCP Verification](path/to/screenshot22.png)

## Additional Concepts

In addition to the basic setup, I also explored the following concepts:

- **Group Policy Management**: Configured various policies for users and computers.
- **DNS Server**: Ensured DNS was correctly configured on the Domain Controller.
- **Security Settings**: Configured basic security settings and permissions for users and groups.
- **Backup and Recovery**: Set up backup policies for the Active Directory to ensure data integrity and availability.

## Conclusion

This project showcases my ability to set up a robust home lab environment simulating a business setup with Microsoft Active Directory. This lab demonstrates my practical skills in network services, user management, and domain administration, providing a solid foundation for enterprise-level IT infrastructure management.

---
