---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: cb0fb1a6d7de033438c3165d44d5b8f8c03ba9a4
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342989"
---
# Get-HotFix

## 概要
取得安裝在本機或遠端電腦上的修補程式。

## SYNTAX

### Default (預設值)

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### 說明

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## DESCRIPTION

此 `Get-Hotfix` Cmdlet 會取得本機電腦或指定的遠端電腦上安裝的修補程式或更新。 您可以 Windows Update、Microsoft Update、Windows Server Update Services 或手動安裝更新來安裝更新。

## 範例

### 範例1：取得本機電腦上的所有修補程式

`Get-Hotfix`Cmdlet 會取得本機電腦上安裝的所有修補程式。

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### 範例2：從以字串篩選的多部電腦取得修補程式

此 `Get-Hotfix` 命令會使用參數來取得在遠端電腦上安裝的修補程式。 結果會依指定的描述字串進行篩選。

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

`Get-Hotfix`篩選具有 **Description** 參數的輸出，以及包含星號 **Security** () 萬用字元的字串安全性 `*` 。 **ComputerName** 參數包含以逗號分隔的遠端電腦名稱稱字串。 **Credential** 參數指定具有存取遠端電腦和執行命令之許可權的使用者帳戶。

### 範例3：確認是否已安裝更新，並將電腦名稱稱寫入檔案

此範例中的命令會確認是否已安裝特定的更新。 如果未安裝此更新，則會將電腦名稱稱寫入文字檔。

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

`$A`變數包含從文字檔取得的電腦名稱稱 `Get-Content` 。 中的物件 `$A` 會向下傳送到管線 `ForEach-Object` 。 `if`語句會使用 `Get-Hotfix` Cmdlet 搭配 **Id** 參數和每個電腦名稱稱的特定識別碼。 如果電腦未安裝指定的修正程式識別碼，則 Cmdlet 會將 `Add-Content` 電腦名稱稱寫入檔案。

### 範例4：在本機電腦上取得最新的修正程式

此範例會取得電腦上安裝的最新的修正程式。

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-Hotfix` 將物件沿著管線向下傳送至 `Sort-Object` Cmdlet。 `Sort-Object` 依遞增順序排序物件，並使用 **Property** 參數來評估每個 **InstalledOn** 日期。 陣列標記法會 `[-1]` 選取最近安裝的修正程式。

## PARAMETERS

### -ComputerName

指定遠端電腦。 輸入 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或遠端電腦 (FQDN) 的完整功能變數名稱。

如果未指定 **ComputerName** 參數，會 `Get-Hotfix` 在本機電腦上執行。

**ComputerName** 參數不依賴 Windows PowerShell 遠端處理。 如果您的電腦未設定為執行遠端命令，請使用 **ComputerName** 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定擁有存取電腦和執行命令之許可權的使用者帳戶。 預設值為目前的使用者

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
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

`Get-HotFix` 使用 **Description** 參數指定修正程式類型。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Id

篩選 `Get-HotFix` 特定修正程式識別碼的結果。 不接受萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 字串

您可以透過管道將一或多個電腦名稱稱傳送至 Get-修正程式。

## 輸出

### System.management.managementobject # root\CIMV2\ Win32_QuickFixEngineering

`Get-HotFix` 傳回物件，代表電腦上的修正程式。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

**Win32_QuickFixEngineering** [WMI 類別](/windows/desktop/WmiSdk/retrieving-a-class)代表一小段全系統更新，通常稱為快速修正工程 (QFE) update，套用至目前的作業系統。 這個類別只會傳回以元件為基礎的服務 (CBS) 所提供的更新。 這些更新不會列在登錄中。 **Win32_QuickFixEngineering** 不會傳回 Microsoft WINDOWS INSTALLER (MSI) 或 [Windows Update](https://update.microsoft.com)網站所提供的更新。 如需詳細資訊，請參閱 [Win32_QuickFixEngineering 類別](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)。

`Get-HotFix`不同的作業系統可能會有不同的輸出。

## 相關連結

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Add-Content](Add-Content.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Win32_QuickFixEngineering 類別](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
