---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 4774c87c4f6ebe7f374f30139ead833bde7074e3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343397"
---
# Unblock-File

## 概要
將從網際網路下載的檔案解除封鎖。

## SYNTAX

### ByPath (預設值)

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Unblock-File` Cmdlet 可讓您開啟從網際網路下載的檔案。 它會將從網際網路下載的 PowerShell 指令檔解除封鎖，讓您可以執行它們，即使是在 **RemoteSigned** powershell 執行原則時也一樣。 這些檔案預設會被封鎖，以保護電腦免於不受信任檔案的損害。

使用 Cmdlet 之前 `Unblock-File` ，請先檢查檔案和其來源，並確認可以安全地開啟。

就內部而言，此 `Unblock-File` Cmdlet 會移除區域。識別碼替代資料流程（其值為 "3"）表示它是從網際網路下載。

如需 PowerShell 執行原則的詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：將檔案解除封鎖

這個命令會將 PowerShellTips.chm 檔案解除封鎖。

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### 範例 2：將多個檔案解除封鎖

此命令會解除封鎖 `C:\Downloads` 目錄中名稱包含 "PowerShell" 的所有檔案。 除非您已確認所有檔案都是安全的，否則請勿執行這類命令。

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### 範例 3：尋找指令碼並將其解除封鎖

此命令示範如何尋找 PowerShell 腳本，並將其解除封鎖。

第一個命令會使用 *取得專案* Cmdlet 的 **資料流程** 參數，並取得具有區域識別碼資料流程的檔案。

第二個命令會顯示當您在執行原則 **RemoteSigned** 所在的 PowerShell 會話中執行封鎖的腳本時，會發生什麼事。 RemoteSigned 原則會防止您執行從網際網路下載的指令碼，除非指令碼經過數位簽署。

第三個命令 `Unblock-File` 會使用 Cmdlet 將腳本解除封鎖，讓它可以在會話中執行。

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## PARAMETERS

### -LiteralPath

指定要解除封鎖的檔案。 與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要解除封鎖的檔案。 支援使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

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

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將檔案路徑傳送至 `Unblock-File` 。

## 輸出

### None

此 Cmdlet 不會產生任何輸出。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

- 此 `Unblock-File` Cmdlet 只適用于檔案系統磁片磁碟機。
- `Unblock-File`在檔案總管中的 [ **屬性** ] 對話方塊上，執行與 [ **解除封鎖** ] 按鈕相同的作業。
- 如果您 `Unblock-File` 在未封鎖的檔案上使用指令程式，此命令不會影響已解除封鎖的檔案，而且 Cmdlet 不會產生錯誤。

## 相關連結

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-Item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-File](Out-File.md)

[FileSystem 提供者](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
