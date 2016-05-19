---
title: ISESnippetCollection 物件
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
---
# ISESnippetCollection 物件
  **ISESnippetCollection** 物件是 **ISESnippet** 物件的集合。 與 **PowerShellTab** 物件相關聯的檔案集合是這個類別的成員。 **$psISE.CurrentPowerShellTab.Files** 集合即為一例。

## 方法

### Load( FilePathName )
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。 

 載入 .snippets.ps1xml 檔案，其中包含使用者定義的程式碼片段。 建立程式碼片段的最簡單方式是使用 New-IseSnippet Cmdlet，自動將它們儲存於您的設定檔資料夾中，如此一來，每當您啟動 Windows PowerShell ISE 時就會自動載入它們。

 **FilePathName** – 字串
 .snippets.ps1xml 檔案的路徑和檔案名稱，其中包含程式碼片段定義。

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## 另請參閱
 [ISESnippetObject](The-ISESnippetObject.md) 
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


