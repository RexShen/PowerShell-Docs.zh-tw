---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEFile 物件
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951387"
---
# <a name="the-isefile-object"></a>ISEFile 物件

**ISEFile** 物件代表 Windows PowerShell® 整合式指令碼環境 (ISE) 中的檔案。 它是 Microsoft.PowerShell.Host.ISE.ISEFile 類別的執行個體。 本主題列出其成員方法和成員屬性。 **$psISE.CurrentFile** 以及 PowerShell 索引標籤上檔案集合中的檔案就是 Microsoft.PowerShell.Host.ISE.ISEFile 類別的所有執行個體。

## <a name="methods"></a>Methods

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

將檔案儲存至磁碟。

**\[saveEncoding\]** - 選擇性 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) 可供所儲存檔案使用的選擇性字元編碼參數。 預設值為 **UTF8**。

### <a name="exceptions"></a>例外狀況

- **System.IO.IOException**︰無法儲存檔案。

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

使用指定的檔案名稱和編碼方式來儲存檔案。

**filename** - 字串：要用來儲存檔案的名稱。

**\[saveEncoding\]** - 選擇性 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) 可供所儲存檔案使用的選擇性字元編碼參數。 預設值為 **UTF8**。

### <a name="exceptions"></a>例外狀況

- **System.ArgumentNullException**：**filename** 參數為 Null。
- **System.ArgumentException**：**filename** 參數是空的。
- **System.IO.IOException**︰無法儲存檔案。

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Properties

### <a name="displayname"></a>DisplayName

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得包含此檔案顯示名稱的字串。 名稱會顯示於編輯器頂端的 [檔案] 索引標籤上。 名稱結尾的星號 \(\*\) 表示檔案有尚未儲存的變更。

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得用於指定檔案的[編輯器物件](The-ISEEditor-Object.md)。

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>編碼

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得原始的檔案編碼方式。 這是 **System.Text.Encoding** 物件。

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得指定已開啟檔案之完整路徑的字串。

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀的布林值屬性，如果檔案在上次修改後已儲存，即會傳回 **$true**。

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，如果檔案不具標題，即會傳回 **$true**。

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>另請參閱

- [The ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)