---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 封裝資源並上傳到提取伺服器
ms.openlocfilehash: d0e070b7aa43acbbbf087729d53f06dbc7e7734a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782883"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="23a96-103">封裝資源並上傳到提取伺服器</span><span class="sxs-lookup"><span data-stu-id="23a96-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="23a96-104">下列各節假設您已經設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="23a96-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="23a96-105">如果尚未設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="23a96-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="23a96-106">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="23a96-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="23a96-107">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="23a96-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="23a96-108">每個目標節點都設定為下載設定、資源，甚至是報告其狀態。</span><span class="sxs-lookup"><span data-stu-id="23a96-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="23a96-109">本文將示範如何上傳資源，讓它們可供下載，並設定用戶端以自動下載資源。</span><span class="sxs-lookup"><span data-stu-id="23a96-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="23a96-110">當節點收到指派的設定時，透過**提取**或**推送** (v5)，它就會自動從 LCM 中指定的位置下載設定所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="23a96-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="23a96-111">封裝資源模組</span><span class="sxs-lookup"><span data-stu-id="23a96-111">Package Resource Modules</span></span>

<span data-ttu-id="23a96-112">可供用戶端下載的每項資源都必須儲存為 `.zip` 檔案。</span><span class="sxs-lookup"><span data-stu-id="23a96-112">Each resource available for a client to download must be stored in a `.zip` file.</span></span> <span data-ttu-id="23a96-113">下列範例將示範使用 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) \(英文\) 資源所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="23a96-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="23a96-114">如果有任何使用 PowerShell 4.0 的用戶端，您將必須壓平合併資源資料夾結構，並移除所有的版本資料夾。</span><span class="sxs-lookup"><span data-stu-id="23a96-114">If you have any clients using PowerShell 4.0, you will need to flatten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="23a96-115">如需詳細資訊，請參閱[多個資源版本](../configurations/import-dscresource.md#multiple-resource-versions)。</span><span class="sxs-lookup"><span data-stu-id="23a96-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="23a96-116">您可以使用任何慣用的公用程式、指令碼或方法來壓縮資源目錄。</span><span class="sxs-lookup"><span data-stu-id="23a96-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="23a96-117">在 Windows 中，您可「用滑鼠右鍵按一下」`xPSDesiredStateConfiguration`目錄，然後依序選取 [傳送到] 和 [壓縮的資料夾]。</span><span class="sxs-lookup"><span data-stu-id="23a96-117">In Windows, you can _right-click_ on the `xPSDesiredStateConfiguration` directory, and select **Send To**, then **Compressed Folder**.</span></span>

![以滑鼠右鍵按一下 - [傳送到] - [壓縮的資料夾]](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="23a96-119">為資源封存命名</span><span class="sxs-lookup"><span data-stu-id="23a96-119">Naming the Resource Archive</span></span>

<span data-ttu-id="23a96-120">資源封存必須使用下列格式來命名：</span><span class="sxs-lookup"><span data-stu-id="23a96-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="23a96-121">在上例中，`xPSDesiredStateConfiguration.zip` 應該重新命名為 `xPSDesiredStateConfiguration_8.4.4.0.zip`。</span><span class="sxs-lookup"><span data-stu-id="23a96-121">In the example above, `xPSDesiredStateConfiguration.zip` should be renamed `xPSDesiredStateConfiguration_8.4.4.0.zip`.</span></span>

### <a name="create-checksums"></a><span data-ttu-id="23a96-122">建立總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="23a96-122">Create CheckSums</span></span>

<span data-ttu-id="23a96-123">一旦將資源模組壓縮並重新命名之後，您必須建立**總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="23a96-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span> <span data-ttu-id="23a96-124">用戶端上的 LCM 會使用**總和檢查碼**來判斷資源是否已變更且需要再次下載。</span><span class="sxs-lookup"><span data-stu-id="23a96-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="23a96-125">您可以使用 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) Cmdlet 來建立**總和檢查碼**，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="23a96-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="23a96-126">系統將不會顯示任何輸出，但您現在應該會看到 "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum"。</span><span class="sxs-lookup"><span data-stu-id="23a96-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="23a96-127">您也可以使用 `-Path` 參數，針對檔案的目錄執行 `New-DSCCheckSum`。</span><span class="sxs-lookup"><span data-stu-id="23a96-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="23a96-128">如果總和檢查碼已經存在，您可以使用 `-Force` 參數強制重新建立它。</span><span class="sxs-lookup"><span data-stu-id="23a96-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="23a96-129">儲存資源封存的位置</span><span class="sxs-lookup"><span data-stu-id="23a96-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="23a96-130">在 DSC HTTP 提取伺服器上</span><span class="sxs-lookup"><span data-stu-id="23a96-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="23a96-131">當您設定 HTTP 提取伺服器時，如[設定 DSC HTTP 提取伺服器](pullServer.md)中所述，您會針對 **ModulePath** 和 **ConfigurationPath** 索引碼指定目錄。</span><span class="sxs-lookup"><span data-stu-id="23a96-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="23a96-132">**ConfigurationPath** 索引碼指出應儲存所有 ".mof" 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="23a96-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="23a96-133">**ModulePath** 指出應儲存所有 DSC 資源模組的位置。</span><span class="sxs-lookup"><span data-stu-id="23a96-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="23a96-134">在 SMB 共用上</span><span class="sxs-lookup"><span data-stu-id="23a96-134">On an SMB Share</span></span>

<span data-ttu-id="23a96-135">如果您指定了 **ResourceRepositoryShare**，當您設定提取用戶端時，需將封存與總和檢查碼儲存於 **ResourceRepositoryShare** 區塊的 **SourcePath** 目錄中。</span><span class="sxs-lookup"><span data-stu-id="23a96-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="23a96-136">如果您只指定 **ConfigurationRepositoryShare**，當您設定提取用戶端時，則需將封存與總和檢查碼儲存於 **ConfigurationRepositoryShare** 區塊的 **SourcePath** 目錄中。</span><span class="sxs-lookup"><span data-stu-id="23a96-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="23a96-137">更新資源</span><span class="sxs-lookup"><span data-stu-id="23a96-137">Updating resources</span></span>

<span data-ttu-id="23a96-138">您可以藉由變更封存名稱中的版本號碼，或建立新的總和檢查碼，來強制節點更新其資源。</span><span class="sxs-lookup"><span data-stu-id="23a96-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="23a96-139">提取用戶端將檢查較新版本的必要資源，而且會在其 LCM 重新整理時更新總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="23a96-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="23a96-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23a96-140">See also</span></span>

- [<span data-ttu-id="23a96-141">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="23a96-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="23a96-142">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="23a96-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
