---
title: 其他有用的指令碼物件
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
---
# 其他有用的指令碼物件
  下列物件會提供 Windows PowerShell ISE 中額外的指令碼功能。 它們不屬於 **$psISE** 階層。

## 有用的指令碼物件

### $psUnsupportedConsoleApplications
 有一些關於 Windows PowerShell ISE 與主控台應用程式互動方式的限制。 需要使用者介入的命令或自動化指令碼，可能無法依照它從 Windows PowerShell 主控台運作的方式來運作。 您可能想要封鎖這些命令或指令碼在 [Windows PowerShell ISE 命令] 窗格中執行。 **$psUnsupportedConsoleApplications** 物件會保留這類命令的清單。 如果您嘗試執行此清單中的命令，您會收到不支援這類命令的訊息。 下列指令碼會在清單中新增項目。

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### $psLocalHelp
 這個字典物件會在本機編譯的 HTML 說明檔中，維護說明主題及其相關聯連結之間內容相關性的對應。 您可以使用它來尋找特定主題的本機說明。 您可以新增或刪除此清單中的主題。 下列程式碼範例示範一些 **$psLocalHelp** 中所含的索引鍵值組範例。.

```
# See the local help map
$psLocalHelp |Format-List

```

### 取樣輸出

|||
|-|-|
|索引鍵：Add-Computer|值︰WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|索引鍵：Add-Content|值︰WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 下列指令碼會在清單中新增項目。

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### $psOnlineHelp
 這個字典物件會維護說明主題的主題標題及其相關聯外部 URL 之間內容相關性的對應。 您可以使用它，在 Web 上尋找特定主題的說明。 您可以新增或刪除此清單中的主題。

```
$psOnlineHelp |format-list

```

### 取樣輸出

|||
|-|-|
|索引鍵：Add-Computer|值︰http://go.microsoft.com/fwlink/?LinkID=135194|
|索引鍵：Add-Content|值︰http://go.microsoft.com/fwlink/?LinkID=113278|

 下列指令碼會在清單中新增項目。

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## 另請參閱
 [Windows PowerShell ISE 指令碼物件模型](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


