---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用登錄機碼"
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: efb2c016afa2212c2907c0740ad26c4e4cddd3af
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="0bf3b-103">使用登錄機碼</span><span class="sxs-lookup"><span data-stu-id="0bf3b-103">Working with Registry Keys</span></span>
<span data-ttu-id="0bf3b-104">因為登錄機碼是 Windows PowerShell 磁碟機上的項目，所以使用它們很像是使用檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="0bf3b-105">最大的差別是登錄式 Windows PowerShell 磁碟機上的每個項目都是容器，就像檔案系統磁碟機上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="0bf3b-106">不過，登錄項目及其相關值都是項目的屬性，而非不同的項目。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="0bf3b-107">列出登錄機碼所有的子機碼</span><span class="sxs-lookup"><span data-stu-id="0bf3b-107">Listing All Subkeys of a Registry Key</span></span>
<span data-ttu-id="0bf3b-108">您可以使用 **Get-ChildItem** 直接顯示登錄機碼內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="0bf3b-109">加入選用的 **Force** 參數，以顯示隱藏或系統項目。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="0bf3b-110">例如，這個命令會直接顯示 Windows PowerShell 磁碟機 HKCU: 內的項目，與 HKEY_CURRENT_USER 登錄區相對應︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="0bf3b-111">這些是在登錄編輯程式 (Regedit.exe) 中可看到的 HKEY_CURRENT_USER 的最上層機碼。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="0bf3b-112">您也可以指定登錄提供者的名稱，後面加上 "**::**"，來指定這個登錄路徑。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="0bf3b-113">登錄提供者的完整名稱是 **Microsoft.PowerShell.Core\\Registry**，但可以縮短到 **Registry**。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="0bf3b-114">下列任一命令都會直接列出 HKCU 下的內容︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="0bf3b-115">這些命令只會列出直接包含的項目，很像使用 Cmd.exe 的 **DIR** 命令或 UNIX 殼層的 **ls**。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="0bf3b-116">若要顯示包含的項目，您必須指定 **Recurse** 參數。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="0bf3b-117">若要列出 HKCU 的所有登錄機碼，請使用下列命令 (這項作業可能耗費很長時間)︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="0bf3b-118">**Get-ChildItem** 可以透過其 **Path**、**Filter**、**Include** 和 **Exclude** 參數執行複雜的篩選功能，但這些參數通常只以名稱為基礎。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="0bf3b-119">您可以使用 **Where-Object** Cmdlet 根據項目的其他屬性來執行複雜的篩選。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-119">You can perform complex filtering based on other properties of items by using the **Where-Object**cmdlet.</span></span> <span data-ttu-id="0bf3b-120">下列命令會尋找 HKCU:\\Software 內，只有一個子機碼且僅有四個值的所有機碼︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="0bf3b-121">複製機碼</span><span class="sxs-lookup"><span data-stu-id="0bf3b-121">Copying Keys</span></span>
<span data-ttu-id="0bf3b-122">以 **Copy-Item** 完成複製。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="0bf3b-123">下列命令會將 HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion 及其所有屬性複製到 HKCU:\\，建立名為 "CurrentVersion" 的新機碼︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="0bf3b-124">如果您使用登錄編輯程式或 **Get-ChildItem** 檢查這個新機碼，您會發現新位置沒有所包含子機碼的複本。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="0bf3b-125">若要複製容器的所有內容，您必須指定 **Recurse** 參數。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="0bf3b-126">若要讓上述的複製命令遞迴，您可以使用這個命令︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-126">To make the preceding copy command recursive, you would use this command:</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="0bf3b-127">您仍然可以使用現有的其他工具執行檔案系統複製作業。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="0bf3b-128">您可以在 Windows PowerShell 中使用任何登錄編輯工具，包括 reg.exe、regini.exe、regedit.exe 和支援登錄編輯的 COM 物件 (如 WScript.Shell 和 WMI 的 StdRegProv 類別)。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="0bf3b-129">建立機碼</span><span class="sxs-lookup"><span data-stu-id="0bf3b-129">Creating Keys</span></span>
<span data-ttu-id="0bf3b-130">在登錄中建立新機碼比在檔案系統中建立新項目簡單。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="0bf3b-131">因為所有的登錄機碼都是容器，所以不需要指定項目類型，只要提供明確的路徑，例如︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="0bf3b-132">您也可以使用提供者路徑來指定機碼︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-132">You can also use a provider-based path to specify a key:</span></span>

```
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="0bf3b-133">刪除機碼</span><span class="sxs-lookup"><span data-stu-id="0bf3b-133">Deleting Keys</span></span>
<span data-ttu-id="0bf3b-134">所有提供者的項目刪除作業本質上是相同的。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="0bf3b-135">下列命令會以無訊息模式移除項目︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-135">The following commands will silently remove items:</span></span>

```
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="0bf3b-136">移除特定機碼下的所有機碼</span><span class="sxs-lookup"><span data-stu-id="0bf3b-136">Removing All Keys Under a Specific Key</span></span>
<span data-ttu-id="0bf3b-137">您可以使用 **Remove-Item** 移除包含的項目，但如果項目包含任何其他項目，系統會提示您確認移除。</span><span class="sxs-lookup"><span data-stu-id="0bf3b-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="0bf3b-138">例如，如果我們嘗試刪除之前建立的 HKCU:\\CurrentVersion 子機碼，我們會看到︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="0bf3b-139">若要刪除包含的項目但不顯示提示，請指定 **-Recurse** 參數︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="0bf3b-140">如果想要移除 HKCU:\\CurrentVersion 內的所有項目但保留 HKCU:\\CurrentVersion 本身，您可以改用︰</span><span class="sxs-lookup"><span data-stu-id="0bf3b-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

