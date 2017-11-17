---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEFileCollection 物件"
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="ff0bf-103">ISEFileCollection 物件</span><span class="sxs-lookup"><span data-stu-id="ff0bf-103">The ISEFileCollection Object</span></span>
  <span data-ttu-id="ff0bf-104">**ISEFileCollection** 物件是 **ISEFile** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="ff0bf-105">$psISE.CurrentPowerShellTab.Files 集合即為一例。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="ff0bf-106">方法</span><span class="sxs-lookup"><span data-stu-id="ff0bf-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="ff0bf-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="ff0bf-107">Add\( \[fullPath\] \)</span></span>
  <span data-ttu-id="ff0bf-108">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff0bf-109">建立並傳回未命名的新檔案，並將它加入至集合。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="ff0bf-110">新建立檔案的 **IsUntitled** 屬性是 **$true**。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

 <span data-ttu-id="ff0bf-111">**\[fullPath\]** - 選擇性字串：完整指定的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="ff0bf-112">如果您包含 **fullPath** 參數和相對路徑，或者使用檔案名稱而非完整路徑，即會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a><span data-ttu-id="ff0bf-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="ff0bf-113">Remove\( File, \[Force\] \)</span></span>
  <span data-ttu-id="ff0bf-114">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff0bf-115">從目前的 PowerShell 索引標籤中移除指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-115">Removes a specified file from the current PowerShell tab.</span></span>

 <span data-ttu-id="ff0bf-116">**File** - 字串：您想要從集合中移除的 ISEFile 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="ff0bf-117">如果檔案尚未儲存，這個方法就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="ff0bf-118">使用 **Force** 切換參數，強制移除尚未儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

 <span data-ttu-id="ff0bf-119">**\[Force\]** - 選擇性布林值：如果設定為 **$true**，就會授與權限來移除檔案，即使檔案在最後一次使用之後尚未儲存也一樣。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="ff0bf-120">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-120">The default is **$false**.</span></span>

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="ff0bf-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="ff0bf-121">SetSelectedFile\( selectedFile \)</span></span>
  <span data-ttu-id="ff0bf-122">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff0bf-123">選取 **selectedFile** 參數所指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

 <span data-ttu-id="ff0bf-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile。您想要選取的 ISEFile 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff0bf-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a><span data-ttu-id="ff0bf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff0bf-125">See Also</span></span>
- [<span data-ttu-id="ff0bf-126">ISEFile 物件</span><span class="sxs-lookup"><span data-stu-id="ff0bf-126">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="ff0bf-127">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="ff0bf-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ff0bf-128">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="ff0bf-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="ff0bf-129">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="ff0bf-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
