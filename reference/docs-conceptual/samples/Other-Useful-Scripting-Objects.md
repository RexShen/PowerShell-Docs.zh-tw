---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 其他有用的指令碼物件
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71325148"
---
# <a name="other-useful-scripting-objects"></a>其他有用的指令碼物件

下列物件會提供 Windows PowerShell ISE 中額外的指令碼功能。 它們不屬於 **$psISE** 階層。

## <a name="useful-scripting-objects"></a>有用的指令碼物件

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

有一些關於 Windows PowerShell ISE 與主控台應用程式互動方式的限制。 需要使用者介入的命令或自動化指令碼，可能無法依照它從 Windows PowerShell 主控台運作的方式來運作。 您可能想要封鎖這些命令或指令碼在 [Windows PowerShell ISE 命令] 窗格中執行。 **$psUnsupportedConsoleApplications** 物件會保留這類命令的清單。 如果您嘗試執行此清單中的命令，您會收到不支援這類命令的訊息。 下列指令碼會在清單中新增項目。

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

這個字典物件會在本機編譯的 HTML 說明檔中，維護說明主題及其相關聯連結之間內容相關性的對應。 您可以使用它來尋找特定主題的本機說明。 您可以新增或刪除此清單中的主題。 下列程式碼範例示範一些 `$psLocalHelp` 中所含的索引鍵值組範例。

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

下列指令碼會在清單中新增項目。

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

這個字典物件會維護說明主題的主題標題及其相關聯外部 URL 之間內容相關性的對應。 您可以使用它，在 Web 上尋找特定主題的說明。 您可以新增或刪除此清單中的主題。

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

下列指令碼會在清單中新增項目。

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>另請參閱

[Windows PowerShell ISE 指令碼物件模型的用途](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
