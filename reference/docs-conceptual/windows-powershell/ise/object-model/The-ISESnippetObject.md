---
ms.date: 06/05/2017
title: ISESnippetObject
description: ISESnippet 物件是 Microsoft.PowerShell.Host.ISE.ISESnippet 類別的執行個體。
ms.openlocfilehash: 602b344686cbcfb1e994914d4e26438ff7e4b1de
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663415"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

**ISESnippet** 物件是 Microsoft.PowerShell.Host.ISE.ISESnippet 類別的執行個體。 `$psISE.CurrentPowerShellTab.Snippets` 集合的成員都是 **ISESnippet** 物件的範例。 建立程式碼片段的最簡單方式是使用 [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) Cmdlet。

## <a name="properties"></a>屬性

### <a name="author"></a>作者

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

唯讀屬性，可取得程式碼片段的作者名稱。

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

唯讀屬性，可取得要插入至編輯器的程式碼片段。

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>快速鍵

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

唯讀屬性，可取得功能表項目的 Windows 鍵盤快速鍵。

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>另請參閱

- [ISESnippetCollection 物件](The-ISESnippetCollection-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
