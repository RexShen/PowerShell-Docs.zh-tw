---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 封裝並上傳到提取伺服器的資源
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400651"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="e1097-103">封裝並上傳到提取伺服器的資源</span><span class="sxs-lookup"><span data-stu-id="e1097-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="e1097-104">下列各節假設您有已設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1097-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="e1097-105">如果您還沒有設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="e1097-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="e1097-106">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e1097-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e1097-107">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e1097-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="e1097-108">若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。</span><span class="sxs-lookup"><span data-stu-id="e1097-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="e1097-109">本文將說明如何上傳資源，讓它們可被下載，並設定用戶端會自動下載的資源。</span><span class="sxs-lookup"><span data-stu-id="e1097-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="e1097-110">當節點會收到指派的組態，透過**提取**或是**推送**(v5)，便會自動下載從 LCM 中指定的位置組態所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="e1097-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="e1097-111">套件資源模組</span><span class="sxs-lookup"><span data-stu-id="e1097-111">Package Resource Modules</span></span>

<span data-ttu-id="e1097-112">若要下載的用戶端可用的每個資源必須儲存在 「.zip 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="e1097-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="e1097-113">下列範例會顯示所需的步驟，使用[xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0)資源。</span><span class="sxs-lookup"><span data-stu-id="e1097-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="e1097-114">如果您有任何使用 PowerShell 4.0 的用戶端時，您將需要 flaten 資源資料夾結構，並移除任何版本的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e1097-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="e1097-115">如需詳細資訊，請參閱 <<c0> [ 多個資源版本](../configurations/import-dscresource.md#multiple-resource-versions)。</span><span class="sxs-lookup"><span data-stu-id="e1097-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="e1097-116">您可以壓縮任何公用程式、 指令碼或您偏好的方法所使用的資源目錄。</span><span class="sxs-lookup"><span data-stu-id="e1097-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="e1097-117">在 Windows 中，您可以*上按一下滑鼠右鍵*"xPSDesiredStateConfiguration"目錄，然後選取 「 傳送到"，則 「 壓縮資料夾 」。</span><span class="sxs-lookup"><span data-stu-id="e1097-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![以滑鼠右鍵按一下](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="e1097-119">命名資源封存</span><span class="sxs-lookup"><span data-stu-id="e1097-119">Naming the Resource Archive</span></span>

<span data-ttu-id="e1097-120">資源封存，就必須使用下列格式命名：</span><span class="sxs-lookup"><span data-stu-id="e1097-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="e1097-121">在上述範例中，「 xPSDesiredStateConfiguration.zip"應該是已重新命名 「 xPSDesiredStateConfiguration_8.4.4.0.zip"。</span><span class="sxs-lookup"><span data-stu-id="e1097-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="e1097-122">建立總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="e1097-122">Create CheckSums</span></span>

<span data-ttu-id="e1097-123">一旦已壓縮並重新命名資源模組，您需要建立**總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="e1097-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="e1097-124">**總和檢查碼**使用時，依用戶端上的 LCM 以判斷資源已變更，且必須再次下載。</span><span class="sxs-lookup"><span data-stu-id="e1097-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="e1097-125">您可以建立**總和檢查碼**具有[New-dscchecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e1097-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="e1097-126">將會顯示任何輸出，但您現在應該會看到 「 xPSDesiredStateConfiguration_8.4.4.0.zip.checksum"。</span><span class="sxs-lookup"><span data-stu-id="e1097-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="e1097-127">您也可以執行`New-DSCCheckSum`檔案的目錄對`-Path`參數。</span><span class="sxs-lookup"><span data-stu-id="e1097-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="e1097-128">如果總和檢查碼已經存在，您可以強制它重新建立與`-Force`參數。</span><span class="sxs-lookup"><span data-stu-id="e1097-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="e1097-129">儲存資源封存位置</span><span class="sxs-lookup"><span data-stu-id="e1097-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="e1097-130">在 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e1097-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="e1097-131">當您設定您的 HTTP 提取伺服器，如所述[設定 DSC HTTP 提取伺服器](pullServer.md)，您指定的目錄**ModulePath**並**ConfigurationPath**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e1097-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="e1097-132">**ConfigurationPath**而 key 則代表儲存的任何 「.mof 」 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="e1097-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="e1097-133">**ModulePath**指出應儲存的任何 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="e1097-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="e1097-134">在 SMB 共用</span><span class="sxs-lookup"><span data-stu-id="e1097-134">On an SMB Share</span></span>

<span data-ttu-id="e1097-135">如果您指定**ResourceRepositoryShare**，當您提取用戶端，設定存放區封存和總和檢查碼，在**SourcePath**目錄從**ResourceRepositoryShare**區塊。</span><span class="sxs-lookup"><span data-stu-id="e1097-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

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

<span data-ttu-id="e1097-136">如果您只指定**ConfigurationRepositoryShare**，當您提取用戶端，設定存放區封存和總和檢查碼，在**SourcePath**目錄從**ConfigurationRepositoryShare**區塊。</span><span class="sxs-lookup"><span data-stu-id="e1097-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="e1097-137">更新資源</span><span class="sxs-lookup"><span data-stu-id="e1097-137">Updating resources</span></span>

<span data-ttu-id="e1097-138">您可以強制更新其資源，藉由變更版本號碼，在 封存的名稱，或建立新的總和檢查碼的節點。</span><span class="sxs-lookup"><span data-stu-id="e1097-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="e1097-139">提取用戶端會檢查所需的資源，較新版本，以及其 LCM 會重新整理時更新總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="e1097-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1097-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1097-140">See also</span></span>

- [<span data-ttu-id="e1097-141">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e1097-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e1097-142">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e1097-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
