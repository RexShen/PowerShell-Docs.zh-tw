---
title: "Just Enough Administration 的改善功能"
contributor: ryanpu
translationtype: Human Translation
ms.sourcegitcommit: 598bfd856d45e8763525df68fad7696900af4dff
ms.openlocfilehash: 7d2f293f000d3d82f4a227d3b3760988d9f02be7

---

## 限制 JEA 端點間的檔案複製

您現在可遠端將檔案複製到 JEA 端點及從中複製檔案，並可確保連接的使用者無法隨意複製*任何*一項系統上的檔案。
方法是將 PSSC 檔案設定為掛接連接使用者的使用者磁碟機。
使用者磁碟機是新的 PSDrive，對每個連接的使用者而言皆為唯一，並在工作階段之間保存。
使用 Copy-Item 將檔案複製到 JEA 端點或從中複製檔案時，其會受限為僅允許存取使用者磁碟機。
嘗試將檔案複製到任何其他 PSDrive 將會失敗。

若要在您的 JEA 工作階段設定檔中設定使用者磁碟機，請使用下列新欄位︰
```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

支援使用者磁碟機的資料夾將會建立於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

若要利用使用者磁碟機，並將檔案複製到設為公開使用者磁碟機的 JEA 端點及從中複製檔案，請使用 Copy-Item 上的 `-ToSession` 和 `-FromSession` 參數。
```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

接著您便可以撰寫自訂的函數來處理使用者磁碟機中儲存的資料，並讓角色功能檔案中的使用者可加以使用。

## 群組受管理服務帳戶的支援

在某些情況下，使用者需要在 JEA 工作階段中執行的工作可能需要存取本機電腦以外的資源。
JEA 工作階段設定為使用虛擬帳戶時，任何嘗試連接到此類資源的行為將會顯示為來自本機電腦的身分識別，而非來自虛擬帳戶或連接的使用者。
在 TP5 中，我們已啟用支援在 [群組受管理服務帳戶] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx) 內容下執行 JEA，使其更容易使用網域身分識別存取網路資源。

若要將 JEA 工作階段設為在 gMSA 帳戶下執行，請使用您 PSSC 檔案中的下列新金鑰︰
```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **注意︰** 群組受管理服務帳戶無法承受隔離或受限的虛擬帳戶範圍。
> 每個連接的使用者會共用相同 gMSA 身分識別，其可能具備整個企業的權限。
> 若選取使用 gMSA，請務必特別小心，並一律盡可能優先選擇僅限於本機電腦的虛擬帳戶。

## 條件式存取原則

JEA 對於限制連接至系統且要管理系統的人員可做事項而言很實用，但若您同時想限制人員*何時*可使用 JEA 呢？
我們已在工作階段設定檔 (.pssc) 中加入設定選項，以讓您指定使用者必須屬於哪個安全性群組才能建立 JEA 工作階段。
若您的環境中有 Just In Time (JIT) 系統，且您要讓使用者提高其權限後才能存取高權限 JEA 端點，則這項相當實用。

PSSC 檔案中新的 *RequiredGroups* 欄位可讓您指定邏輯，以判斷使用者是否可連接到 JEA。
其包含指定雜湊表 (選擇性地為巢狀)，該雜湊表會使用 'And' 及 'Or' 索引鍵來建構您的規則。
以下是如何運用此欄位的一些範例︰
```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## 固定︰Windows Server 2008 R2 現在支援虛擬帳戶
在 WMF 5.1 中，您現在可於 Windows Server 2008 R2 使用虛擬帳戶，讓 Windows Server 2008 R2 - 2016 上的設定和功能同位一致。
在 Windows 7 上使用 JEA 時，仍不支援虛擬帳戶。


<!--HONumber=Jul16_HO4-->


