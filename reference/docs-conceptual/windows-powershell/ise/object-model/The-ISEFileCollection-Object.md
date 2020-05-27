---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEFileCollection 物件
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809334"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection 物件

**ISEFileCollection** 物件是 **ISEFile** 物件的集合。 例如，`$psISE.CurrentPowerShellTab.Files` 集合。

## <a name="methods"></a>方法

### <a name="add-fullpath-"></a>Add\( \[FullPath\] \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

建立並傳回未命名的新檔案，並將它加入至集合。 新建立檔案的 **IsUntitled** 屬性是 `$true`。

**\[FullPath\]** - 選擇性字串：完整指定的檔案路徑。 如果您包含 **FullPath** 參數和相對路徑，或者使用檔案名稱而非完整路徑，即會產生例外狀況。

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

從目前的 PowerShell 索引標籤中移除指定的檔案。

**File** - 字串：您想要從集合中移除的 ISEFile 檔案。 如果檔案尚未儲存，這個方法就會擲回例外狀況。 使用 **Force** 切換參數，強制移除尚未儲存的檔案。

**\[Force\]** - 選擇性布林值：如果設定為 `$true`，就會授與權限來移除檔案，即使檔案在最後一次使用之後尚未儲存也一樣。 預設值為 `$false`。

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

選取 **SelectedFile** 參數所指定的檔案。

**SelectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile。您想要選取的 ISEFile 檔案。

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>另請參閱

- [ISEFile 物件](The-ISEFile-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
