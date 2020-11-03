---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: 1b0fbfca365e9cf369decbf4eafc0a8b4e2741bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204795"
---
# Remove-PSSession

## 概要
 (Pssession) 關閉一或多個 PowerShell 會話。

## SYNTAX

### Id (預設值)

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 工作階段

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ContainerId

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMId

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMName

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Name

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**移除 PSSession** Cmdlet 會關閉目前會話中 ( **Pssession** ) 的 PowerShell 會話。
它會停止任何在 **PSSession** 中執行的命令、結束 **PSSession** ，並釋放 **PSSession** 使用的資源。
若 **PSSession** 連線到遠端電腦，此 Cmdlet 也會關閉本機和遠端電腦之間的連線。

若要移除 **PSSession** ，請輸入工作階段的 *Name* 、 *ComputerName* 、 *ID* 或 *InstanceID* 。

若您已將 *PSSession* 儲存在變數中，工作階段物件仍會維持在該變數中，但 *PSSession* 的狀態是「已關閉」。

## 範例

### 範例 1︰使用識別碼移除工作階段

```powershell
Remove-PSSession -Id 1, 2
```

此命令會移除具有識別碼 1 和 2 的 **PSSession** 。

### 範例 2︰移除目前工作階段中的所有工作階段

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

這些命令會移除目前工作階段中的所有 **PSSession** 。
雖然這三個命令的格式看起來不同，但它們作用相同。

### 範例 3︰使用名稱關閉工作階段

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

這些命令會關閉連線到名稱開頭為 Serv 之電腦的 **PSSession** 。

### 範例 4︰關閉連線至連接埠的工作階段

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

此命令會關閉連線至連接埠 90 的 **PSSession** 。
您可以使用此命令格式，以 *ComputerName* 、 *Name* 、 *InstanceID* 及 *ID* 之外的屬性來識別 **PSSession** 。

### 範例 5︰根據執行個體識別碼關閉工作階段

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

這些命令示範如何根據其執行個體識別碼或 **RemoteRunspaceID** 來關閉 **PSSession** 。

第一個命令會使用 **Get-PSsession** Cmdlet，來取得目前工作階段中的 **PSSession** 。
它使用管線運算子 (|) 將 **PSSession** 傳送至 Format-Table Cmdlet，以將它們的 **ComputerName** 和 **InstanceID** 屬性格式化為表格。
*AutoSize* 參數會壓縮顯示的欄位。

您可以從顯示的結果中識別要關閉的 **PSSession** ，並複製該 **PSSession** 的 *InstanceID* ，然後在第二個命令中貼上。

第二個命令會使用 **Remove-PSSession** Cmdlet，來移除具有指定執行個體識別碼的 *PSSession* 。

### 範例 6︰建立函式以刪除目前工作階段中所有的工作階段

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

此函式會刪除目前工作階段中所有的 **PSSession** 。
將此函式新增至您的 PowerShell 設定檔之後，若要刪除所有的會話，請輸入 `EndPSS` 。

## PARAMETERS

### -ComputerName

指定電腦名稱的陣列。
此 Cmdlet 會關閉連線到指定電腦的 **PSSession** 。
允許使用萬用字元。

輸入一或多部遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。
若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ContainerId

指定容器的識別碼陣列。 此 Cmdlet 會移除每個指定容器的會話。 使用 `docker ps` 命令來取得容器識別碼的清單。 如需詳細資訊，請參閱 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的說明。

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Id

指定工作階段識別碼的陣列。
此 Cmdlet 會關閉具有指定識別碼的 *PSSession* 。
輸入一或多個識別碼 (以逗號分隔)，或使用範圍運算子 (..) 來指定某個範圍的識別碼。

識別碼是整數，可唯一識別目前工作階段中的 **PSSession** 。
與 *InstanceId* 相比，它比較容易記住並輸入，但是它只有在目前工作階段內是唯一的。
若要尋找 **PSSession** 的識別碼，請執行 Get-PSSession 且不搭配任何參數。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定執行階段識別碼的陣列。
此 Cmdlet 會關閉具有指定執行個體識別碼的 **PSSession** 。

執行個體識別碼是 GUID，可唯一識別目前工作階段中的 **PSSession** 。
執行個體識別碼是唯一的，即使在同一部電腦上有多個正在執行的工作階段也一樣。

執行個體識別碼會儲存在代表 **PSSession** 之物件的 **InstanceID** 屬性中。
若要在目前工作階段中尋找 **PSSessions** 的 **InstanceID** ，請輸入 `Get-PSSession | Format-Table Name, ComputerName, InstanceId`。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定工作階段好記名稱的陣列。
此 Cmdlet 會關閉具有指定好記名稱的 **PSSession** 。
允許使用萬用字元。

由於 **PSSession** 的好記名稱可能不是唯一的，因此在使用 *Name* 參數時，請考慮在 **Remove-PSSession** 命令中使用 *WhatIf* 或 *Confirm* 參數。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

指定要關閉的 **PSSession** 工作階段物件。
輸入包含 **PSSession** 的變數，或輸入會建立或取得 **PSSession** 的命令 (例如 New-PSSession 或 **Get-PSSession** 命令)。
您也可以使用管線將一或多個工作階段物件傳送至 **Remove-PSSession** 。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMId

指定虛擬機器的識別碼陣列。
此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。
若要查看可供您使用的虛擬機器，請使用下列命令：

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定虛擬機器名稱的陣列。
此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。
若要查看可供您使用的虛擬機器，請使用 **取得 VM** Cmdlet。

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### System.Management.Automation.Runspaces.PSSession

您可以使用管線將工作階段物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何物件。

## 注意

* *Id* 參數是必要的。 若要刪除目前工作階段中所有的 **PSSession** ，請輸入 `Get-PSSession | Remove-PSSession`。
* **PSSession** 會使用遠端電腦的持續連線。 建立 **PSSession** 來執行一系列共用資料的命令。 如需詳細資訊，請鍵入 `Get-Help about_PSSessions`。
* **PSSession** 專屬於目前的工作階段。 當您結束工作階段時，即會強制關閉您在該工作階段中建立的 **PSSession** 。

## 相關連結

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

