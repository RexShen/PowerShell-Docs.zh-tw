---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 發佈至提取伺服器，使用設定識別碼 (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400676"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="9c7c1-103">發佈至提取伺服器，使用設定識別碼 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="9c7c1-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="9c7c1-104">下列各節假設您有已設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="9c7c1-105">如果您還沒有設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="9c7c1-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="9c7c1-106">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="9c7c1-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9c7c1-107">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="9c7c1-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="9c7c1-108">若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="9c7c1-109">本文將說明如何上傳資源，讓它們可被下載，並設定用戶端會自動下載的資源。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="9c7c1-110">當節點會收到指派的組態，透過**提取**或是**推送**(v5)，便會自動下載從 LCM 中指定的位置組態所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="9c7c1-111">編譯組態</span><span class="sxs-lookup"><span data-stu-id="9c7c1-111">Compile Configurations</span></span>

<span data-ttu-id="9c7c1-112">若要儲存的第一個步驟[組態](../configurations/configurations.md)在提取伺服器上，是將它們編譯成 「.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="9c7c1-113">若要進行組態，一般和適用於多個用戶端，使用`localhost`節點區塊中。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="9c7c1-114">下列範例顯示使用的設定殼層`localhost`而不是特定用戶端名稱。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="9c7c1-115">當您編譯您的一般設定時，您應該有"localhost.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="9c7c1-116">重新命名的 MOF 檔案</span><span class="sxs-lookup"><span data-stu-id="9c7c1-116">Renaming the MOF file</span></span>

<span data-ttu-id="9c7c1-117">您可以設定 「.mof 」 檔案，提取伺服器上的儲存**ConfigurationName**或是**ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="9c7c1-118">根據您計劃如何設定提取用戶端，您可以選擇適當地重新命名已編譯的 「.mof"檔案下一節。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="9c7c1-119">設定識別碼 (GUID)</span><span class="sxs-lookup"><span data-stu-id="9c7c1-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="9c7c1-120">您必須重新命名您的 「 localhost.mof"檔案，以 「<GUID>.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="9c7c1-121">您可以建立的隨機**Guid**下方，或使用範例[New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="9c7c1-122">取樣輸出</span><span class="sxs-lookup"><span data-stu-id="9c7c1-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="9c7c1-123">然後，您可以重新命名 「.mof"檔案使用任何可接受的方法。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="9c7c1-124">下列範例中，使用[重新命名項目](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="9c7c1-125">如需使用詳細資訊**Guid**在您環境中，請參閱[Guid 的計劃](/powershell/dsc/secureserver#guids)。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="9c7c1-126">設定名稱</span><span class="sxs-lookup"><span data-stu-id="9c7c1-126">Configuration Names</span></span>

<span data-ttu-id="9c7c1-127">您必須重新命名您的 「 localhost.mof"檔案，以 「<Configuration Name>.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="9c7c1-128">在下列範例中，會使用上一節的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="9c7c1-129">然後，您可以重新命名 「.mof"檔案使用任何可接受的方法。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="9c7c1-130">下列範例中，使用[重新命名項目](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="9c7c1-131">建立總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="9c7c1-131">Create the CheckSum</span></span>

<span data-ttu-id="9c7c1-132">每個".mof"檔案會儲存在提取伺服器或 SMB 共用上必須有相關聯的 「.checksum"檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="9c7c1-133">此檔案可讓用戶端知道當相關聯的 「.mof"檔案已變更，而且應該會再次下載。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="9c7c1-134">您可以建立**總和檢查碼**具有[New-dscchecksum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="9c7c1-135">您也可以執行`New-DSCCheckSum`檔案的目錄對`-Path`參數。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="9c7c1-136">如果總和檢查碼已經存在，您可以強制它重新建立與`-Force`參數。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="9c7c1-137">下列範例會指定包含上一節中，「.mof 」 檔案的目錄，並使用`-Force`參數。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="9c7c1-138">將會顯示任何輸出，但您現在應該會看到 「<GUID or Configuration Name>。 mof.checksum"檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="9c7c1-139">要儲存 MOF 檔案與總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="9c7c1-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="9c7c1-140">在 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="9c7c1-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="9c7c1-141">當您設定您的 HTTP 提取伺服器，如所述[設定 DSC HTTP 提取伺服器](pullServer.md)，您指定的目錄**ModulePath**並**ConfigurationPath**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="9c7c1-142">**ConfigurationPath**而 key 則代表儲存的任何 「.mof 」 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="9c7c1-143">**ConfigurationPath**表示來儲存任何 「.mof 「 檔案和".checksum 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="9c7c1-144">在 SMB 共用</span><span class="sxs-lookup"><span data-stu-id="9c7c1-144">On an SMB Share</span></span>

<span data-ttu-id="9c7c1-145">當您設定提取用戶端使用之 SMB 共用時，您會指定**ConfigurationRepositoryShare**。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="9c7c1-146">所有 「.mof 「 檔案和".checksum"檔案應該則會儲存在**SourcePath**目錄**ConfigurationRepositoryShare**區塊。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="9c7c1-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9c7c1-147">Next Steps</span></span>

<span data-ttu-id="9c7c1-148">接下來，您會想要設定提取用戶端提取指定的組態。</span><span class="sxs-lookup"><span data-stu-id="9c7c1-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="9c7c1-149">如需詳細資訊，請參閱下列指南：</span><span class="sxs-lookup"><span data-stu-id="9c7c1-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="9c7c1-150">設定提取用戶端使用設定識別碼 (v4)</span><span class="sxs-lookup"><span data-stu-id="9c7c1-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="9c7c1-151">設定提取用戶端使用設定識別碼 (v5)</span><span class="sxs-lookup"><span data-stu-id="9c7c1-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="9c7c1-152">設定提取用戶端使用設定名稱 (v5)</span><span class="sxs-lookup"><span data-stu-id="9c7c1-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="9c7c1-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c7c1-153">See also</span></span>

- [<span data-ttu-id="9c7c1-154">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="9c7c1-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9c7c1-155">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="9c7c1-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="9c7c1-156">封裝並上傳到提取伺服器的資源</span><span class="sxs-lookup"><span data-stu-id="9c7c1-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
