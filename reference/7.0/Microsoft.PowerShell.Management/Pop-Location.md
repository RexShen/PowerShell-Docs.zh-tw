---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 4f5dffdc942112672c3a193fd1fef49b3b5c15d6
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205872"
---
# Pop-Location

## 概要
將目前的位置變更至最近推送到堆疊上的位置。

## SYNTAX

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## DESCRIPTION

此 `Pop-Location` Cmdlet 會使用 Cmdlet 將目前的位置變更為最近推送至堆疊的位置 `Push-Location` 。 您可以從預設堆疊或從您使用命令建立的堆疊中取出位置 `Push-Location` 。

## 範例

### 範例 1︰變更為最新的位置

```
PS C:\> Pop-Location
```

此命令將您的位置變更至最近新增到目前堆疊的位置。

### 範例 2︰變更為具名堆疊中的最新位置

```
PS C:\> Pop-Location -StackName "Stack2"
```

此命令將您的位置變更至最近新增到 Stack2 位置堆疊的位置。

如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。

### 範例 3︰在不同提供者的位置之間移動

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

這些命令會使用 `Push-Location` 和 `Pop-Location` Cmdlet 來移動不同 PowerShell 提供者所支援的位置。 這些命令會使用的 `pushd` 別名 `Push-Location` ，以及的 `popd` 別名 `Pop-Location` 。

第一個命令會將目前的檔案系統位置推送到堆疊上，並移至 PowerShell 登錄提供者所支援的 HKLM 磁片磁碟機。

第二個命令將登錄位置推送到堆疊上，並移至 PowerShell 憑證提供者所支援的位置。

最後兩個命令將這些位置從堆疊中取出。 第一個 `popd` 命令會返回登錄磁片磁碟機，第二個命令則會返回檔案系統磁片磁碟機。

## PARAMETERS

### -PassThru

將代表位置的物件傳遞至管線。 根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

指定要從中取出位置的位置堆疊。 請輸入位置堆疊名稱。

如果沒有這個參數，會 `Pop-Location` 從目前的位置堆疊取出位置。 根據預設，目前的位置堆疊是 PowerShell 所建立的未命名預設位置堆疊。 若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。 如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。

`Pop-Location` 無法從未命名的預設堆疊中 pop 位置，除非它是目前的位置堆疊。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無、System.Management.Automation.PathInfo

如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表位置的 **System.Management.Automation.PathInfo** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

PowerShell 支援每個進程有多個空間。 每個運行空間都有自己的 _目前的目錄_ 。
這與不同 `[System.Environment]::CurrentDirectory` 。 呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。

即使位置 Cmdlet 已設定整個進程的目錄，您也無法依賴它，因為另一個執行時間可能會隨時變更。 您應該使用 location Cmdlet 來執行以路徑為基礎的作業，並使用目前的運行時特定的工作目錄。

堆疊是一份後進先出的清單，其中只能存取最近新增的項目。 將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。 PowerShell 可讓您將提供者位置儲存在位置堆疊中。

PowerShell 會建立未命名的預設位置堆疊，而且您可以建立多個命名位置堆疊。 如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。 根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。

若要管理位置堆疊，請使用 PowerShell Cmdlet，如下所示 `*-Location` ：

- 若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。

- 若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。

- 若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。

- 若要顯示命名位置堆疊中的位置，請使用 Cmdlet 的 **StackName** 參數 `Get-Location` 。

- 若要建立新的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Push-Location` 。 如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。

- 若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。

未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。
如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用 `Get-Location` Cmdlet 來顯示未命名堆疊中的位置。 若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$Null` 或 () 的空字串 `""` 。

您也可以 `Pop-Location` 使用內建的別名來參考 `popd` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

`Pop-Location` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Get-Location](Get-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
