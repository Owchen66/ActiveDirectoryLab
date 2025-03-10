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
![AD Installation](https://github.com/user-attachments/assets/2e288c45-016e-4f43-95eb-f8da7e33d284)

### **2️⃣ Promoting the Server to Domain Controller**
![Promote DC](https://github.com/user-attachments/assets/88103a13-0a78-4c60-a04f-d5ee36caf4ae)

### **3️⃣ Creating Organizational Units (OUs)**
![Create OUs](https://github.com/user-attachments/assets/937a6e49-4295-411a-b62f-b877adbb4dd8)

### **4️⃣ Adding Users to Active Directory**
![Create Users](https://github.com/user-attachments/assets/7893a171-e5e9-41c8-b41c-0f9a91be8987)

### **5️⃣ Configuring Group Policy (GPO) to Block USB**
![GPO Block USB](https://github.com/user-attachments/assets/1997032b-5cc5-4be1-bb72-7d640aba8b65)

### **6️⃣ Linking GPO to an Organizational Unit**
![Link GPO](https://github.com/user-attachments/assets/93c273f0-6a06-42f8-9e2d-0f6693298fb4)

### **7️⃣ Forcing Group Policy Update on Clients**
![GPO Update](https://github.com/user-attachments/assets/a65917b5-122f-42ba-b89c-6d2ff4f8c2d1)

### **8️⃣ Verifying Applied Policies on a Client Machine**
![Verify GPO](https://github.com/user-attachments/assets/3b497683-00aa-488a-8b5f-5de4b8ed3557)

### **9️⃣ Testing USB Block Policy in Action**
![USB Block](https://github.com/user-attachments/assets/7d6062d0-344e-4e9b-bc88-4e6b798cfcc6)

### **🔟 Checking Group Policy**
![GPO Results](https://github.com/user-attachments/assets/8f773ca9-c44c-4975-8b70-5ee88123ecdc)

### **1️⃣1️⃣ Final Active Directory & GPO Configuration Summary**
![Final Summary](https://github.com/user-attachments/assets/66eb5474-9e1b-4569-b941-b611e7b34392)

---

## 📩 Contact & More
If you have any questions or want to collaborate, feel free to reach out!
