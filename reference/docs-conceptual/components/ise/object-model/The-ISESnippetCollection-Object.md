---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetCollection 物件
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030508"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection 物件

**ISESnippetCollection** 物件是 **ISESnippet** 物件的集合。 與 **PowerShellTab** 物件相關聯的檔案集合是這個類別的成員。 **$psISE.CurrentPowerShellTab.Files** 集合即為一例。

## <a name="methods"></a>Methods

### <a name="load-filepathname-"></a>Load\( FilePathName \)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

載入 .snippets.ps1xml 檔案，其中包含使用者定義的程式碼片段。 建立程式碼片段的最簡單方式是使用 New-IseSnippet Cmdlet，自動將它們儲存於您的設定檔資料夾中，如此一來，每當您啟動 Windows PowerShell ISE 時就會自動載入它們。

**FilePathName** - .snippets.ps1xml 檔案的路徑和檔案名稱，其中包含程式碼片段定義。

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>另請參閱

- [ISESnippetObject](The-ISESnippetObject.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
