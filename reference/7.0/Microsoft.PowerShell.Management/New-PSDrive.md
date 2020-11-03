---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 71605d2c630cb456a44226ddbe2a99f92347b617
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201768"
---
# New-PSDrive

## 概要
建立暫存和持續連線的網路磁碟機。

## SYNTAX

### 全部

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 `New-PSDrive` Cmdlet 會建立與資料存放區中的位置對應或相關聯的暫存和持續磁片磁碟機，例如網路磁碟機機、本機電腦上的目錄或登錄機碼，以及與遠端電腦上的檔案系統位置相關聯的持續性 Windows 對應網路磁碟機機。

暫存磁片磁碟機只存在於目前的 PowerShell 會話，以及您在目前會話中建立的會話中。 它們可以擁有任何在 PowerShell 中有效的名稱，而且可以對應到任何本機或遠端資源。 您可以使用暫存的 PowerShell 磁片磁碟機來存取相關聯資料存放區中的資料，就像使用任何對應的網路磁碟機機一樣。 您可以使用或存取磁片磁碟機的內容，以將位置變更為磁片磁碟機 `Set-Location` `Get-Item` `Get-ChildItem` 。

因為暫存磁片磁碟機只有 PowerShell 知道，所以您無法使用檔案總管、Windows Management Instrumentation (WMI) 、元件物件模型 (COM) 、Microsoft .NET Framework，或使用 **NET use** 之類的工具來存取它們。

PowerShell 3.0 中已新增下列功能 `New-PSDrive` ：

- 對應的網路磁碟機。 您可以使用的 [ **保存** ] 參數 `New-PSDrive` 建立 Windows 對應的網路磁碟機機。 不同于暫存的 PowerShell 磁片磁碟機，Windows 對應的網路磁碟機機不是會話特定的。 它們會儲存在 Windows 中，並可使用標準 Windows 工具（例如檔案總管和 **net use** ）進行管理。 連線的網路磁碟機必須擁有磁碟機代號名稱並連線至遠端檔案系統位置。 當您的命令設定在本機的範圍時，如果沒有任何點來源，則 **保存** 參數不會在命令執行的範圍之外保存 **new-psdrive** 的建立。 如果您是在 `New-PSDrive` 腳本內部執行，而且您想要讓磁片磁碟機無限期保存，則必須以點為來源的腳本。 為了獲得最佳結果，若要強制無限期保留新的磁碟機，請在命令中加入 **Scope** 參數，並將其值設定為 **Global** 。 如需有關點出來源的詳細資訊，請參閱 [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)。
- 外部磁片磁碟機。 當外部磁片磁碟機連接到電腦時，PowerShell 會自動將 **new-psdrive** 新增至代表新磁片磁碟機的檔案系統。 您不需要重新開機 PowerShell。 同樣地，當外部磁片磁碟機與電腦中斷連線時，PowerShell 會自動刪除代表已移除之磁片磁碟機的 **new-psdrive** 。
- 通用命名慣例的認證 (UNC) 路徑。

當 **Root** 參數的值是 UNC 路徑時（例如 `\\Server\Share` ），會使用 **credential** 參數值中指定的認證來建立 **new-psdrive** 。 否則，當您建立新的檔案系統磁片磁碟機時， **認證** 將不會生效。

某些程式碼範例會使用展開來減少行長度，並提高可讀性。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

## 範例

### 範例1：建立對應至網路共用的暫存磁片磁碟機

此範例會建立對應至網路共用的暫存 PowerShell 磁片磁碟機。

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

`New-PSDrive` 使用 **Name** 參數來指定名為的 powershell 磁片磁碟機 `Public` ，並使用 **PSProvider** 參數來指定 powershell `FileSystem` 提供者。 **Root** 參數指定網路共用的 UNC 路徑。

若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path Public:`

### 範例2：建立對應至本機目錄的暫存磁片磁碟機

這個範例會建立暫存的 PowerShell 磁片磁碟機，以提供本機電腦上目錄的存取權。

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

展開會建立參數索引鍵和值。 **Name** 參數會指定磁片磁碟機名稱 **MyDocs** 。 **PSProvider** 參數會指定 PowerShell `FileSystem` 提供者。 **Root** 指定本機電腦的目錄。 **Description** 參數描述磁片磁碟機的用途。 `New-PSDrive` 使用 splatted 參數來建立 `MyDocs` 磁片磁碟機。

若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path MyDocs:`

### 範例3：建立登錄機碼的暫存磁片磁碟機

這個範例會建立暫存的 PowerShell 磁片磁碟機，以提供登錄機碼的存取權。 它會建立一個名為 MyCompany 的磁片磁碟機，它會對應到登錄機 `HKLM:\Software\MyCompany` 碼。

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

`New-PSDrive` 使用 **Name** 參數來指定名為的 powershell 磁片磁碟機 `MyCompany` ，並使用 **PSProvider** 參數來指定 powershell `Registry` 提供者。 **Root** 參數指定登錄位置。

若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path MyCompany:`

### 範例4：使用認證建立持續性對應的網路磁碟機機

此範例會對應以網域服務帳戶的認證進行驗證的網路磁碟機機。
如需有關用來儲存認證的 **PSCredential** 物件，以及密碼如何儲存為 **SecureString** 的詳細資訊，請參閱 **Credential** 參數的描述。

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> 請記住，如果您在腳本中使用上述程式碼片段，請將 **範圍** 參數值設定為 "Global"，以確保磁片磁碟機在目前的範圍之外保持不變。

`$cred`變數會儲存一個 **PSCredential** 物件，其中包含服務帳戶的認證。 `Get-Credential` 提示您輸入儲存在 **SecureString** 中的密碼。

`New-PSDrive` 使用數個參數建立對應的網路磁碟機機。 **名稱** 會指定 `S` Windows 接受的磁碟機號。 和 **Root** 定義 `\\Server01\Scripts` 為遠端電腦上的位置。 [ **保存** ] 會建立儲存在本機電腦上的 Windows 對應網路磁碟機機。 **PSProvider** 指定 `FileSystem` 提供者。 **認證會** 使用 `$cred` 變數來取得服務帳戶認證以進行驗證。

您可以在本機電腦上的 PowerShell 會話中、檔案總管，以及利用 **net use** 之類的工具，來查看對應的磁片磁碟機。 若要從 PowerShell 會話中查看內容： `Get-ChildItem -Path S:`

### 範例5：建立持續性和暫存磁片磁碟機

此範例顯示持續連線的網路磁碟機機與對應到相同網路共用的暫存 PowerShell 磁片磁碟機之間的差異。

如果您關閉 PowerShell 會話，然後開啟新的會話，則暫時 `PSDrive:` 無法使用，但仍 `X:` 可使用持續性磁片磁碟機。 當您決定要使用哪一種方法來對應網路磁碟機機時，請考慮您將如何使用該磁片磁碟機。 例如，它是否必須是持續性，以及其他 Windows 功能是否都能看到磁片磁碟機。

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## PARAMETERS

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作之許可權的使用者帳戶。 預設為目前使用者。

從 PowerShell 3.0 開始，當 **Root** 參數的值是 UNC 路徑時，您可以使用認證來建立檔案系統磁片磁碟機。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Description

指定磁碟機的簡短文字描述。 輸入任何字串。

若要查看所有會話磁片磁碟機的描述，請參閱 `Get-PSDrive | Format-Table Name, Description` 。

若要查看特定磁片磁碟機的描述，請輸入 `(Get-PSDrive <DriveName>).Description` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定新磁碟機的名稱。 若為持續連線的網路磁碟機機，請使用磁碟機號。 針對暫存的 PowerShell 磁片磁碟機，您不限於磁碟機號，請使用任何有效的字串。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Persist

指出此 Cmdlet 會建立 Windows 對應的網路磁碟機機。 **保存** 參數只能在 Windows 上使用。

連線的網路磁碟機會儲存在本機電腦的 Windows 中。 它們是持續性的，不是會話特定的，而且可以在檔案總管和其他工具中加以查看和管理。

當您在本機將命令範圍限定在本機（沒有點對端）時， **保存** 參數不會在您執行命令的範圍之外保存 **new-psdrive** 的建立。 如果您在 `New-PSDrive` 腳本內執行，而您想要讓新的磁片磁碟機無限期保存，則必須以點為來源的腳本。 為了獲得最佳結果，若要強制保留新的磁片磁碟機，請指定 **Global** 作為 **Scope** 參數的值，並在您的命令中包含 **保存** 。

磁片磁碟機的名稱必須是字母，例如 `D` 或 `E` 。 **Root** 參數的值必須是不同電腦的 UNC 路徑。 **PSProvider** 參數的值必須是 `FileSystem` 。

若要中斷 Windows 對應網路磁碟機機的連線，請使用 `Remove-PSDrive` Cmdlet。 當您中斷 Windows 連線網路磁碟機的連線時，該連線會永久從該電腦上刪除，而不是只從目前的工作階段中刪除。

連線網路磁碟機僅適用於特定使用者帳戶。 使用不同的認證來啟動的會話中，不會顯示在提高許可權的會話中建立的對應磁片磁碟機或使用另一個使用者認證的會話。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

指定支援此類型磁片磁碟機的 PowerShell 提供者。

例如，如果磁片磁碟機與網路共用或檔案系統目錄相關聯，則 PowerShell 提供者為 `FileSystem` 。 如果磁片磁碟機與登錄機碼關聯，則提供者為 `Registry` 。

暫存的 PowerShell 磁片磁碟機可以與任何 PowerShell 提供者相關聯。 對應的網路磁碟機機只能與 `FileSystem` 提供者相關聯。

若要查看 PowerShell 會話中的提供者清單，請使用 `Get-PSProvider` Cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Root

指定 PowerShell 磁片磁碟機對應的資料存放區位置。

例如，指定網路共用，例如，本機目錄（例如）或登錄機 `\\Server01\Public` `C:\Program Files` 碼（例如） `HKLM:\Software\Microsoft` 。

暫存的 PowerShell 磁片磁碟機可以與任何支援的提供者磁片磁碟機上的本機或遠端位置相關聯。 連線的網路磁碟機只能與遠端電腦上的檔案系統位置關聯。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定磁碟機的範圍。 此參數可接受的值為： **Global** 、 **Local** 和 **Script** ，或相對於目前範圍的數位。 範圍編號0至範圍數目。 目前的範圍號碼為0，而其父系為1。 如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法對此 Cmdlet 進行管線輸入。

## 輸出

### System.Management.Automation.PSDriveInfo

## 注意

`New-PSDrive` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出會話中可用的提供者，請使用 `Get-PSProvider` 。 如需提供者的詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

連線網路磁碟機僅適用於特定使用者帳戶。 使用不同的認證來啟動的會話中，不會顯示在提高許可權的會話中建立的對應磁片磁碟機或使用另一個使用者認證的會話。

## 相關連結

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PSDrive](Get-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)
