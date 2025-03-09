# 🚀 Active Directory & Group Policy Implementation (Windows Server 2019)

## 📌 Overview
This project demonstrates the **installation and configuration of Active Directory Domain Services (AD DS)** on Windows Server 2019, along with **Group Policy management** to enforce security policies.

## 🔧 Key Features
- **Active Directory Setup**: Installed and configured **AD DS** using PowerShell.
- **User & Group Management**: Created **users, groups, and Organizational Units (OUs)**.
- **Group Policy Enforcement**: Configured **GPOs to block USB access** and applied security policies.
- **Automation**: Used **PowerShell scripting** to streamline deployment and administration.

## 📜 Technologies Used
- **Windows Server 2019**
- **Active Directory (AD DS)**
- **Group Policy (GPO)**
- **PowerShell**
- **User & Group Management**

## 🏗️ Installation & Setup
### **1️⃣ Install AD DS and Promote Server to Domain Controller**
```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName "lab.local"
```
### **2️⃣ Create Organizational Units (OUs) & Users**
```powershell
New-ADOrganizationalUnit -Name "IT" -Path "DC=lab,DC=local"
New-ADUser -Name "John Doe" -GivenName "John" -Surname "Doe" -SamAccountName "jdoe" -UserPrincipalName "jdoe@lab.local" -Path "OU=IT,DC=lab,DC=local" -AccountPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) -Enabled $true
```
### **3️⃣ Configure Group Policy to Block USB**
```powershell
New-GPO -Name "USB Block Policy" | New-GPLink -Target "OU=IT,DC=lab,DC=local"
```
### **4️⃣ Apply GPOs & Verify Policy Enforcement**
```powershell
gpupdate /force
gpresult /r
```

## 📸 Program Walkthrough
Below are screenshots documenting the Active Directory setup and Group Policy implementation.

### **1️⃣ Installing Active Directory Services**
![AD Installation](https://i.imgur.com/dg97xlq.png)

### **2️⃣ Promoting the Server to Domain Controller**
![Promote DC](https://i.imgur.com/didhRIR.png))

### **3️⃣ Creating Organizational Units (OUs)**
![Create OUs](https://i.imgur.com/I7of6PF.png)

### **4️⃣ Adding Users to Active Directory**
![Create Users](https://i.imgur.com/fWRunpy.png)

### **5️⃣ Configuring Group Policy (GPO) to Block USB**
![GPO Block USB](https://i.imgur.com/gksCbHP.png)

### **6️⃣ Linking GPO to an Organizational Unit**
![Link GPO](https://i.imgur.com/ahUV36V.png)

### **7️⃣ Forcing Group Policy Update on Clients**
![GPO Update](https://i.imgur.com/PGrxkNb.png)

### **8️⃣ Verifying Applied Policies on a Client Machine**
![Verify GPO](https://i.imgur.com/bq3XNnq.png)

### **9️⃣ Testing USB Block Policy in Action**
![USB Block](https://i.imgur.com/beEPVYZ.png)

### **🔟 Checking Group Policy**
![GPO Results](https://i.imgur.com/1OYr4SG.png)

### **1️⃣1️⃣ Final Active Directory & GPO Configuration Summary**
![Final Summary](https://i.imgur.com/AFrOorW.png)

---

## 📩 Contact & More
If you have any questions or want to collaborate, feel free to reach out!
