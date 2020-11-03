---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: d404f0fdc82e3730f1f6a04d7f39d5988a3de7d6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201384"
---
# Get-PSDrive

## 概要
取得目前工作階段中的磁碟機。

## SYNTAX

### Name (預設值)

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### LiteralName

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-PSDrive`Cmdlet 會取得目前會話中的磁片磁碟機。 您可以取得工作階段中的特定磁碟機或所有磁碟機。

此 Cmdlet 會取得下列類型的磁片磁碟機：

- 電腦上的 Windows 邏輯磁碟機，包括對應至網路共用的磁碟機。
- PowerShell 提供者所公開的磁片磁碟機 (例如 Certificate：、Function：和 Alias：磁片磁碟機) 和 Windows PowerShell 登錄提供者所公開的 HKLM：和 HKCU：磁片磁碟機。
- 工作階段指定的暫時性磁碟機，以及您使用 New-PSDrive Cmdlet 建立的永久連線網路磁碟機。

從 Windows PowerShell 3.0 開始，此 Cmdlet 的 **保存** 參數 `New-PSDrive` 可以建立儲存在本機電腦上且可在其他會話中使用的對應網路磁碟機機。 如需詳細資訊，請參閱 New-PSDrive。

此外，從 Windows PowerShell 3.0 開始，當外接式磁碟機連接到電腦時，Windows PowerShell 便會自動將代表新磁碟機的 PSDrive 新增到檔案系統。
您不需要重新啟動 Windows PowerShell。 同樣地，當外接式磁碟機已從電腦中斷連接時，Windows PowerShell 也會自動刪除代表已移除之磁碟機的 PSDrive 。

## 範例

### 範例1：取得目前會話中的磁片磁碟機

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

這個命令會取得目前工作階段中的磁碟機。

輸出顯示硬碟 (C： ) 、CD-ROM 光碟機 (D： ) ，以及 Windows PowerShell 提供者所公開的磁片磁碟機 (Alias：、Cert：、Env：、Function：、HKCU：、HKLM：和 Variable： ) 。

### 範例2：取得電腦上的磁片磁碟機

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

這個命令會取得電腦上的 D: 磁碟機。 請注意，命令中的磁碟機代號後面不接冒號。

### 範例3：取得 Windows PowerShell 檔案系統提供者所支援的所有磁片磁碟機

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

這個命令會取得 Windows PowerShell FileSystem 提供者所支援的全部磁碟機。 這包括固定式磁碟機、邏輯磁碟分割、連線的網路磁碟機，以及您使用 New-PSDrive Cmdlet 建立的暫時性磁碟機。

### 範例4：檢查磁片磁碟機是否使用 Windows PowerShell 磁片磁碟機名稱

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

這個命令會檢查 X 磁碟機是否已被用來做為 Windows PowerShell 磁碟機名稱。
如果不是，此命令會使用指令程式 `New-PSDrive` 來建立與 HKLM： \ SOFTWARE 登錄機碼對應的暫存磁片磁碟機。

### 範例5：比較檔案類型的系統磁片磁碟機

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

此範例會將顯示的檔案系統磁片磁碟機類型， `Get-PSDrive` 與使用其他方法顯示的檔案系統磁片磁碟機類型進行比較。 此範例示範在 Windows PowerShell 中顯示磁片磁碟機的不同方式，並顯示使用 New-PSDrive Cmdlet 所建立的會話特定磁片磁碟機只能在 Windows PowerShell 中存取。

第一個命令會使用 `Get-PSDrive` 來取得會話中的所有檔案系統磁片磁碟機。 這包括固定磁片磁碟機 (C：和 D： ) 、使用的 **保存** 參數所建立的對應網路磁碟機 (G： ) `New-PSDrive` ，以及使用 `New-PSDrive` 不含 **保存** 參數的來建立的 PowerShell 磁片磁碟機 (T： ) 。

**Net use** 命令會顯示 Windows 連線的網路磁碟機機，在此情況下，它只會顯示 G 磁片磁碟機。 它不會顯示所建立的 X：磁片磁碟機 `New-PSDrive` 。 它會顯示 G：磁片磁碟機也會對應到 \\ \\ 音樂 \\ GratefulDead。

第三個命令使用 Microsoft .NET Framework **System.IO.DriveInfo** 類別的 **GetDrives** 方法。 此命令會取得 Windows 檔案系統磁片磁碟機（包括磁片磁碟機 G：），但不會取得所建立的磁片磁碟機 `New-PSDrive` 。

第四個命令會使用 `Get-CimInstance` Cmdlet 來取得 **Win32_LogicalDisk** 類別的實例。 它會傳回：、C：、D：、E：和 G：磁片磁碟機，但不會傳回所建立的磁片磁碟機 `New-PSDrive` 。

最後一個命令會使用 `Get-CimInstance` Cmdlet 來顯示 **Win32_NetworkConnection** 類別的實例。 就像 **net use** 一樣，它只會傳回所建立的持續性 G：磁片磁碟機 `New-PSDrive` 。

## PARAMETERS

### -LiteralName

指定磁碟機的名稱。

**LiteralName** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果名稱包含逸出字元，請將它括在單引號中。 單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

以字串陣列指定此 Cmdlet 在作業中取得的磁片磁碟機名稱或名稱。
請輸入不含冒號 (:) 的磁碟機名稱或代號。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

將 Windows PowerShell 提供者指定為字串陣列。 此 Cmdlet 只會取得這個提供者所支援的磁片磁碟機。 請輸入提供者的名稱，例如 FileSystem、Registry 或 Certificate。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定此 Cmdlet 取得磁片磁碟機的範圍。

此參數可接受的值為：

- 全球
- 本機
- 指令碼
- 相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父) 。 "Local" 為預設值。

如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

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

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSDriveInfo

此 Cmdlet 會傳回代表會話中磁片磁碟機的物件。

## 注意

* 此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出會話中可用的提供者，請使用 `Get-PSProvider` Cmdlet。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。
* 使用 New-PSDrive Cmdlet 的 **Persist** 參數來建立的連線網路磁碟機是使用者帳戶特定的磁碟機。 您在使用 [以系統管理員身分執行] 選項啟動的會話中建立的對應網路磁碟機機，或使用其他使用者的認證來啟動的會話，不會顯示在不含明確認證或使用目前使用者的認證啟動的會話中。

## 相關連結

[New-PSDrive](New-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

[Get-PSProvider](Get-PSProvider.md)
