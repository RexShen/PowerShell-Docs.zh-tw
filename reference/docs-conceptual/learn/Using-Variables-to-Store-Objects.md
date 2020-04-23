---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用變數儲存物件
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030365"
---
# <a name="using-variables-to-store-objects"></a>使用變數儲存物件

PowerShell 可以搭配物件來使用。 PowerShell 可讓您建立稱為變數的具名物件。
變數名稱可以包括底線字元與任何英數字元。 在 PowerShell 中使用時，變數一律使用 \$ 字元後面接著變數名稱來指定。

## <a name="creating-a-variable"></a>建立變數

您可以輸入有效的變數名稱來建立變數︰

```
PS> $loc
PS>
```

此範例不會傳回任何結果，因為 `$loc` 沒有值。 您可以在相同的步驟中建立變數並指派其值。 PowerShell 只有在變數不存在時才會加以建立。
否則，它會將指定的值指派給現有變數。 下列範例會將目前的位置儲存在變數 `$loc` 中：

```powershell
$loc = Get-Location
```

當您輸入此命令時，PowerShell 不會顯示任何輸出。 PowerShell 會將 'Get-location' 的輸出傳送到 `$loc`。 在 PowerShell 中，會將未指派或重新導向的資料傳送到畫面。 輸入 `$loc` 會顯示您的目前位置：

```
PS> $loc

Path
----
C:\temp
```

您可以使用 `Get-Member` 來顯示變數內容的相關資訊。 `Get-Member` 會顯示 `$loc` 為 **PathInfo** 物件，就像來自 `Get-Location` 的輸出：

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>操作變數

PowerShell 提供數個命令來操作變數。 您可以查看可讀取形式的完整清單，方法是輸入︰

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell 也會建立數個系統定義的變數。 您可以使用 `Remove-Variable` Cmdlet，從目前的工作階段移除所有不受 PowerShell 控制的變數。 輸入下列命令以清除所有變數：

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

執行上一個命令之後，`Get-Variable` Cmdlet 會顯示 PowerShell 系統變數。

PowerShell 也會建立變數磁碟機。 使用下列範例，利用變數磁碟機來顯示所有 PowerShell 變數：

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>使用 Cmd.exe 變數

PowerShell 可以使用可供任何 Windows 處理序 (包括 **cmd.exe**) 使用的相同環境變數。 這些變數會透過名為 `env:` 的磁碟機來公開。 您可以輸入下列命令來檢視這些變數：

```powershell
Get-ChildItem env:
```

標準的 `*-Variable` Cmdlet 不是設計來使用環境變數。 環境變數可以使用 `env:` 磁碟機前置詞來存取。 例如，**cmd.exe** 中的 **%SystemRoot%** 變數包含作業系統的根目錄名稱。 在 PowerShell 中，您會使用 `$env:SystemRoot` 來存取相同的值。

```
PS> $env:SystemRoot
C:\WINDOWS
```

您也可以從 PowerShell 建立和修改環境變數。 PowerShell 中的環境變數會遵循在作業系統中其他地方所使用之環境變數的相同規則。 下列範例會建立新的環境變數：

```powershell
$env:LIB_PATH='/usr/local/lib'
```

雖然並非必要，但通常會針對環境變數名稱全部使用大寫字母。
