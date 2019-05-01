---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 取得命令的相關資訊
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057701"
---
# <a name="getting-information-about-commands"></a>取得命令的相關資訊

PowerShell `Get-Command` 會顯示您目前工作階段中的所有可用命令。
當您執行 `Get-Command` Cmdlet 時，您會看到如下輸出：

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

此輸出與 **cmd.exe** 的 Help 輸出十分相似：內部命令的表格式摘要。 如上面 `Get-Command` 命令輸出的摘要所示，每個顯示的命令都有一個屬於 Cmdlet 的 CommandType。 Cmdlet 是 PowerShell 的內建命令類型。 此類型大致上對應至 **cmd.exe** 中 `dir` 與 `cd` 之類的命令，或是 Unix 殼層 (例如 Bash) 的內建命令。

`Get-Command` Cmdlet 有一個 **Syntax** 參數，可傳回每個 Cmdlet 的語法。 下列範例示範如何取得 `Get-Help` Cmdlet 的語法：

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>依類型顯示可用的命令

`Get-Command` 命令只會列出目前工作階段中的 Cmdlet。 PowerShell 實際上支援數個其他類型的命令：

- 別名
- 函式
- 指令碼

外部可執行檔案或具有已登錄之檔案類型處理常式的檔案，也會分類為命令。

若要取得工作階段中的所有命令，請輸入：

```powershell
Get-Command *
```

此清單包含您搜尋路徑中的外部命令，因此會包含數千個項目。
所以查看一組精簡過的命令會更實用。

> [!NOTE]
> 星號 (\*) 會用於 PowerShell 命令引數中的萬用字元比對。 \* 表示「符合一或多個任意字元」。 您可以鍵入 `Get-Command a*` 來尋找開頭為字母 "a" 的所有命令。 不同於 **cmd.exe** 中的萬用字元比對，PowerShell 的萬用字元也會比對句點。

使用 `Get-Command` 的 **CommandType** 參數來取得其他類型的原生命令。
Cmdlet。

若要取得命令別名 (指派給命令的暱稱)，請輸入：

```powershell
Get-Command -CommandType Alias
```

若要取得目前工作階段中的函式，請輸入：

```powershell
Get-Command -CommandType Function
```

若要顯示 PowerShell 搜尋路徑中的指令碼，請輸入：

```powershell
Get-Command -CommandType Script
```