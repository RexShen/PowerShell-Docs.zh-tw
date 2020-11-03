---
description: 防止腳本在沒有必要元素的情況下執行。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: c6b10137ca58da93caff365a50b125929fd4d11a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208159"
---
# <a name="about-requires"></a>關於需求

## <a name="short-description"></a>簡短描述
防止腳本在沒有必要元素的情況下執行。

## <a name="long-description"></a>完整描述

此 `#Requires` 語句可防止腳本執行，除非 PowerShell 版本、模組 (和版本) 或嵌入式管理單元 (和版本) ，以及符合版本的必要條件。 如果不符合必要條件，則 PowerShell 不會執行腳本。

### <a name="syntax"></a>Syntax

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

如需語法的詳細資訊，請參閱 [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)。

### <a name="rules-for-use"></a>使用的規則

腳本可以包含一個以上的 `#Requires` 語句。 這些 `#Requires` 語句可以出現在腳本中的任何一行。

將語句放在函式 `#Requires` 內不會限制其範圍。 所有 `#Requires` 語句一律會全域套用，而且必須符合，腳本才能執行。

> [!WARNING]
> 雖然 `#Requires` 語句可以出現在腳本中的任何一行，但它在腳本中的位置並不會影響其應用程式的順序。 在 `#Requires` 腳本執行之前，必須符合語句所呈現的全域狀態。

範例：

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

您可能會認為上述程式碼不應該執行，因為必要的模組會在 `#Requires` 語句之前移除。 不過，在 `#Requires` 腳本甚至可以執行之前，必須先符合狀態。 然後，腳本的第一行會使所需的狀態失效。

### <a name="parameters"></a>參數

#### <a name="-assembly-assembly-path--net-assembly-specification"></a>-Assembly \<Assembly path> |\<.NET assembly specification>

指定元件 DLL 檔案的路徑或 .NET 元件名稱。 **元件** 參數是在 PowerShell 5.0 中引進。 如需 .NET 元件的詳細資訊，請參閱 [元件名稱](/dotnet/standard/assembly/names)。

例如：

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a>-Version \<N\> [. \<n\> ]

指定腳本所需的 PowerShell 最低版本。 輸入主要版本號碼和選用的次要版本號碼。

例如：

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a>-PSSnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]

指定腳本需要的 PowerShell 嵌入式管理單元。 輸入嵌入式管理單元名稱和選用的版本號碼。

例如：

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a>-模組 \<Module-Name\> |\<Hashtable\>

指定腳本需要的 PowerShell 模組。 輸入模組名稱和選用的版本號碼。

如果必要的模組不在目前的會話中，則 PowerShell 會將它們匯入。
如果無法匯入模組，則 PowerShell 會擲回終止錯誤。

針對每個模組，輸入 (\<String\>) 或雜湊表的模組名稱。 此值可以是字串和雜湊表的組合。 雜湊表具有下列索引鍵。

- `ModuleName` - **必要** 指定模組名稱。
- `GUID` - **選擇性** 指定模組的 GUID。
- 您也 **必須** 指定下列三個索引鍵中的其中一個。 這些金鑰無法一起使用。
  - `ModuleVersion` -指定模組可接受的最小版本。
  - `RequiredVersion` -指定完全必要的模組版本。
  - `MaximumVersion` -指定模組可接受的最大版本。

> [!NOTE]
> `RequiredVersion` 已在 Windows PowerShell 5.0 中新增。
> `MaximumVersion` 已在 Windows PowerShell 5.1 中新增。

例如：

需要 `AzureRM.Netcore` 安裝 (版 `0.12.0` 或更高的) 。

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

要求 `AzureRM.Netcore` **只** 安裝 (版本 `0.12.0`) 。

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

需要 `AzureRM.Netcore` 安裝 (版本 `0.12.0` 或較少的) 。

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

需要安裝任何版本的 `AzureRM.Netcore` 和 `PowerShellGet` 。

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

使用金鑰時 `RequiredVersion` ，請確定您的版本字串完全符合所需的版本字串。

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

下列範例會失敗，因為 **0.12** 與 **v0.12.0** 完全相符。

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a>-PSEdition \<PSEdition-Name\>

指定腳本需要的 PowerShell 版本。 有效的值為 PowerShell Core 的 **核心** 和 Windows PowerShell 的 **桌面** 。

例如：

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a>-ShellId

指定腳本所需的 shell。 輸入 shell 識別碼。 如果您使用 **ShellId** 參數，則也必須包含 **PSSnapin** 參數。
您可以藉由查詢自動變數來尋找目前的 **ShellId** `$ShellId` 。

例如：

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> 這個參數的目的是要在已被取代的迷你 shell 中使用。

#### <a name="-runasadministrator"></a>-RunAsAdministrator

當此切換參數加入至您的 `#Requires` 語句時，它會指定您要在其中執行腳本的 PowerShell 會話必須以提高的使用者權限來啟動。 非 Windows 作業系統會忽略 **RunAsAdministrator** 參數。 **RunAsAdministrator** 參數是在 PowerShell 4.0 中引進。

例如：

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a>範例

下列腳本有兩個 `#Requires` 語句。 如果不符合這兩個語句中指定的需求，腳本就不會執行。 每個 `#Requires` 語句都必須是該行的第一個專案：

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Language_Keywords](about_Language_Keywords.md)
