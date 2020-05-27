---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxFileLine 資源
ms.openlocfilehash: 4b07c5dd2715ce9f937b1e52deb97b6b4de64975
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560877"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC for Linux nxFileLine 資源

PowerShell 預期狀態設定 (DSC) 的 **nxFileLine** 資源會提供在 Linux 節點上管理設定檔案內各行的機制。

## <a name="syntax"></a>語法

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|FilePath |在目標節點上要管理程式碼行的檔案完整路徑。 |
|ContainsLine |確保存在於檔案中的程式碼行。 如果不存在於檔案中，這一行就會附加至檔案。 **ContainsLine** 是必要的，但如不需要，也可以設為空字串 (`ContainsLine = ""`)。 |
|DoesNotContainPattern |不應該存在於檔案中的程式碼行的規則運算式模式。 對於存在於符合這個規則運算式檔案中的任何程式碼行，會從檔案中移除該行。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |

## <a name="example"></a>範例

這個範例示範如何使用 **nxFileLine** 資源來設定 `/etc/sudoers` 檔案，如此可確保 user: monuser 已設定為不是 requiretty。

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
