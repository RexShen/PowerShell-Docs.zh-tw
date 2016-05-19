---
title: ISESnippetObject
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
---
# ISESnippetObject
  **ISESnippet** 物件是 Microsoft.PowerShell.Host.ISE.ISESnippet 類別的執行個體。 **$psISE.CurrentPowerShellTab.Snippets** 集合的成員都是 **ISESnippet** 物件的範例。 建立程式碼片段的最簡單方式是使用 [New\-IseSnippet&#91;PSITPro5\_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) Cmdlet。

## [內容]

###  <a name="DisplayName"></a> 作者
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。 

 唯讀屬性，可取得程式碼片段的作者名稱。

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <a name="Action"></a> CodeFragment
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。 

 唯讀屬性，可取得要插入至編輯器的程式碼片段。

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <a name="Shortcut"></a> 捷徑
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。 

 唯讀屬性，可取得功能表項目的 Windows 鍵盤快速鍵。

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## 另請參閱
 [ISESnippetCollection 物件](The-ISESnippetCollection-Object.md) 
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


