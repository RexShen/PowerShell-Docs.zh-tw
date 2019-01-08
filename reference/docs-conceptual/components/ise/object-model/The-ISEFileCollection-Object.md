---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEFileCollection 物件
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402069"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="4e7d2-103">ISEFileCollection 物件</span><span class="sxs-lookup"><span data-stu-id="4e7d2-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="4e7d2-104">**ISEFileCollection** 物件是 **ISEFile** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="4e7d2-105">$psISE.CurrentPowerShellTab.Files 集合即為一例。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="4e7d2-106">Methods</span><span class="sxs-lookup"><span data-stu-id="4e7d2-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="4e7d2-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="4e7d2-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="4e7d2-108">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4e7d2-109">建立並傳回未命名的新檔案，並將它加入至集合。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="4e7d2-110">新建立檔案的 **IsUntitled** 屬性是 **$true**。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="4e7d2-111">**\[fullPath\]** - 選擇性字串：完整指定的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="4e7d2-112">如果您包含 **fullPath** 參數和相對路徑，或者使用檔案名稱而非完整路徑，即會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="4e7d2-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="4e7d2-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="4e7d2-114">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4e7d2-115">從目前的 PowerShell 索引標籤中移除指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="4e7d2-116">**File** - 字串：您想要從集合中移除的 ISEFile 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="4e7d2-117">如果檔案尚未儲存，這個方法就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="4e7d2-118">使用 **Force** 切換參數，強制移除尚未儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="4e7d2-119">**\[Force\]** - 選擇性布林值：如果設定為 **$true**，就會授與權限來移除檔案，即使檔案在最後一次使用之後尚未儲存也一樣。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="4e7d2-120">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="4e7d2-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="4e7d2-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="4e7d2-122">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4e7d2-123">選取 **selectedFile** 參數所指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="4e7d2-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile。您想要選取的 ISEFile 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e7d2-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="4e7d2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e7d2-125">See Also</span></span>

- [<span data-ttu-id="4e7d2-126">ISEFile 物件</span><span class="sxs-lookup"><span data-stu-id="4e7d2-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="4e7d2-127">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="4e7d2-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="4e7d2-128">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="4e7d2-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)