---
title: ISEFile 物件
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
---
# ISEFile 物件
  **ISEFile** 物件代表 Windows PowerShell® 整合式指令碼環境 (ISE) 中的檔案。 它是 Microsoft.PowerShell.Host.ISE.ISEFile 類別的執行個體。 本主題列出其成員方法和成員屬性。 **$psISE.CurrentFile** 以及 PowerShell 索引標籤上檔案集合中的檔案就是 Microsoft.PowerShell.Host.ISE.ISEFile 類別的所有執行個體。

## 方法

###  <a name="save-override"></a> Save( [saveEncoding] )
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 將檔案儲存至磁碟。

 **[saveEncoding]** – 選擇性的 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 可供所儲存檔案使用的選擇性字元編碼參數。 預設值為 **UTF8**.

 **例外狀況**
 -   **System.IO.IOException**︰無法儲存檔案。

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <a name="saveas"></a> SaveAs(filename, [saveEncoding])
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 使用指定的檔案名稱和編碼方式來儲存檔案。

 **filename** - 字串
 要用來儲存檔案的名稱。

 **[saveEncoding]** – 選擇性的 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 可供所儲存檔案使用的選擇性字元編碼參數。 預設值為 **UTF8**.

 **例外狀況**
 -   **System.ArgumentNullException**：**filename** 參數為 Null。

-   **System.ArgumentException**：**filename** 參數是空的。

-   **System.IO.IOException**︰無法儲存檔案。

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## [內容]

###  <a name="Displayname"></a> DisplayName
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，可取得包含此檔案顯示名稱的字串。 名稱會顯示於編輯器頂端的 [檔案] 索引標籤上。 名稱結尾出現的星號 (*) 表示檔案有尚未儲存的變更。

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <a name="Editor"></a> Editor
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，可取得用於指定檔案的[編輯器物件](The-ISEEditor-Object.md)。

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <a name="Encoding"></a> 編碼
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，可取得原始的檔案編碼方式。 這是 **System.Text.Encoding** 物件。

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <a name="FullPath"></a> FullPath
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，可取得指定已開啟檔案之完整讀取路徑的字串。

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <a name="IsSaved"></a> IsSaved
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀的布林值屬性，如果檔案在上次修改後已儲存，即會傳回 **$true**。

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <a name="IsUntitled"></a> IsUntitled
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，如果檔案不具標題，即會傳回 **$true**。

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## 另請參閱
 [ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


