---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEFile 物件"
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 0e1c09c4a92868448d76cc7b4954d250773ce2f2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="9b384-103">ISEFile 物件</span><span class="sxs-lookup"><span data-stu-id="9b384-103">The ISEFile Object</span></span>
  <span data-ttu-id="9b384-104">**ISEFile** 物件代表 Windows PowerShell® 整合式指令碼環境 (ISE) 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="9b384-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9b384-105">它是 Microsoft.PowerShell.Host.ISE.ISEFile 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b384-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="9b384-106">本主題列出其成員方法和成員屬性。</span><span class="sxs-lookup"><span data-stu-id="9b384-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="9b384-107">**$psISE.CurrentFile** 以及 PowerShell 索引標籤上檔案集合中的檔案就是 Microsoft.PowerShell.Host.ISE.ISEFile 類別的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b384-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="9b384-108">方法</span><span class="sxs-lookup"><span data-stu-id="9b384-108">Methods</span></span>

###  <span data-ttu-id="9b384-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="9b384-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="9b384-110">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-111">將檔案儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="9b384-111">Saves the file to disk.</span></span>

 <span data-ttu-id="9b384-112">**\[saveEncoding\]** - 選擇性 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 可供所儲存檔案使用的選擇性字元編碼參數。</span><span class="sxs-lookup"><span data-stu-id="9b384-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="9b384-113">預設值為 **UTF8**。</span><span class="sxs-lookup"><span data-stu-id="9b384-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="9b384-114">**例外狀況**</span><span class="sxs-lookup"><span data-stu-id="9b384-114">**Exceptions**</span></span>
 -   <span data-ttu-id="9b384-115">**System.IO.IOException**︰無法儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9b384-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <span data-ttu-id="9b384-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="9b384-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="9b384-117">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-118">使用指定的檔案名稱和編碼方式來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9b384-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="9b384-119">**filename** - 字串：要用來儲存檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b384-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="9b384-120">**\[saveEncoding\]** - 選擇性 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 可供所儲存檔案使用的選擇性字元編碼參數。</span><span class="sxs-lookup"><span data-stu-id="9b384-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="9b384-121">預設值為 **UTF8**。</span><span class="sxs-lookup"><span data-stu-id="9b384-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="9b384-122">**例外狀況**</span><span class="sxs-lookup"><span data-stu-id="9b384-122">**Exceptions**</span></span>
 -   <span data-ttu-id="9b384-123">**System.ArgumentNullException**：**filename** 參數為 Null。</span><span class="sxs-lookup"><span data-stu-id="9b384-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

-   <span data-ttu-id="9b384-124">**System.ArgumentException**：**filename** 參數是空的。</span><span class="sxs-lookup"><span data-stu-id="9b384-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

-   <span data-ttu-id="9b384-125">**System.IO.IOException**︰無法儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9b384-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="9b384-126">[內容]</span><span class="sxs-lookup"><span data-stu-id="9b384-126">Properties</span></span>

###  <span data-ttu-id="9b384-127"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="9b384-127"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="9b384-128">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-129">唯讀屬性，可取得包含此檔案顯示名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9b384-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="9b384-130">名稱會顯示於編輯器頂端的 [檔案] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="9b384-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="9b384-131">名稱結尾的星號 \(\*\) 表示檔案有尚未儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="9b384-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <span data-ttu-id="9b384-132"><a name="Editor"></a> Editor</span><span class="sxs-lookup"><span data-stu-id="9b384-132"><a name="Editor"></a> Editor</span></span>
  <span data-ttu-id="9b384-133">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-134">唯讀屬性，可取得用於指定檔案的[編輯器物件](The-ISEEditor-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="9b384-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <span data-ttu-id="9b384-135"><a name="Encoding"></a> Encoding</span><span class="sxs-lookup"><span data-stu-id="9b384-135"><a name="Encoding"></a> Encoding</span></span>
  <span data-ttu-id="9b384-136">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-137">唯讀屬性，可取得原始的檔案編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9b384-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="9b384-138">這是 **System.Text.Encoding** 物件。</span><span class="sxs-lookup"><span data-stu-id="9b384-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <span data-ttu-id="9b384-139"><a name="FullPath"></a> FullPath</span><span class="sxs-lookup"><span data-stu-id="9b384-139"><a name="FullPath"></a> FullPath</span></span>
  <span data-ttu-id="9b384-140">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-141">唯讀屬性，可取得指定已開啟檔案之完整路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="9b384-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <span data-ttu-id="9b384-142"><a name="IsSaved"></a> IsSaved</span><span class="sxs-lookup"><span data-stu-id="9b384-142"><a name="IsSaved"></a> IsSaved</span></span>
  <span data-ttu-id="9b384-143">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-144">唯讀的布林值屬性，如果檔案在上次修改後已儲存，即會傳回 **$true**。</span><span class="sxs-lookup"><span data-stu-id="9b384-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <span data-ttu-id="9b384-145"><a name="IsUntitled"></a> IsUntitled</span><span class="sxs-lookup"><span data-stu-id="9b384-145"><a name="IsUntitled"></a> IsUntitled</span></span>
  <span data-ttu-id="9b384-146">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="9b384-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9b384-147">唯讀屬性，如果檔案不具標題，即會傳回 **$true**。</span><span class="sxs-lookup"><span data-stu-id="9b384-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="9b384-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b384-148">See Also</span></span>
- [<span data-ttu-id="9b384-149">The ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="9b384-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="9b384-150">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="9b384-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="9b384-151">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="9b384-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="9b384-152">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="9b384-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
