---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 使用設定識別碼發佈至提取伺服器 (v4/v5)
description: 此文章顯示如何上傳資源，讓它們可供下載，並設定用戶端以自動下載資源。
ms.openlocfilehash: 20e12e3cac6b6e4a86563576f4a915429b18aadb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646832"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="40593-104">使用設定識別碼發佈至提取伺服器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="40593-104">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="40593-105">下列各節假設您已經設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="40593-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="40593-106">如果尚未設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="40593-106">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="40593-107">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="40593-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="40593-108">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="40593-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="40593-109">每個目標節點都設定為下載設定、資源，甚至是報告其狀態。</span><span class="sxs-lookup"><span data-stu-id="40593-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="40593-110">此文章顯示如何上傳資源，讓它們可供下載，並設定用戶端以自動下載資源。</span><span class="sxs-lookup"><span data-stu-id="40593-110">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="40593-111">當節點透過 **提取** 或 **推送** (v5) 收到指派的設定時，它會自動從本機 Configuration Manager (LCM) 中指定的位置下載設定所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="40593-111">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="40593-112">編譯設定</span><span class="sxs-lookup"><span data-stu-id="40593-112">Compile configurations</span></span>

<span data-ttu-id="40593-113">在提取伺服器上儲存[設定](../configurations/configurations.md)的第一個步驟是將它們編譯成 `.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-113">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="40593-114">若要使設定通用且適用於更多用戶端，請在節點區塊中使用 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="40593-114">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="40593-115">下列範例示範使用 `localhost` 而非特定用戶端名稱的設定殼層。</span><span class="sxs-lookup"><span data-stu-id="40593-115">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="40593-116">當您編譯一般設定之後，應該會有一個 `localhost.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-116">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="40593-117">將 MOF 檔案重新命名</span><span class="sxs-lookup"><span data-stu-id="40593-117">Renaming the MOF file</span></span>

<span data-ttu-id="40593-118">您可以依 **ConfigurationName** 或 **ConfigurationID** ，在提取伺服器上儲存設定`.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-118">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID** .</span></span> <span data-ttu-id="40593-119">視您計劃設定提取用戶端的方式，您可以選擇下列任一節，適當地將已編譯的 `.mof` 檔案重新命名。</span><span class="sxs-lookup"><span data-stu-id="40593-119">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="40593-120">設定識別碼 (GUID)</span><span class="sxs-lookup"><span data-stu-id="40593-120">Configuration IDs (GUID)</span></span>

<span data-ttu-id="40593-121">您必須將您的 `localhost.mof` 檔案重新命名為 `<GUID>.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-121">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="40593-122">您可以使用以下範例建立隨機 **Guid** ，或是使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40593-122">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="40593-123">範例輸出</span><span class="sxs-lookup"><span data-stu-id="40593-123">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="40593-124">您接著可以使用任何可接受的方法來將 `.mof` 檔案重新命名。</span><span class="sxs-lookup"><span data-stu-id="40593-124">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="40593-125">下列範例會使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40593-125">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="40593-126">如需在您環境中使用 **Guid** 的詳細資訊，請參閱 [為 GUID 規劃](secureServer.md#guids)。</span><span class="sxs-lookup"><span data-stu-id="40593-126">For more information about using **Guids** in your environment, see [Plan for Guids](secureServer.md#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="40593-127">設定名稱</span><span class="sxs-lookup"><span data-stu-id="40593-127">Configuration names</span></span>

<span data-ttu-id="40593-128">您必須將您的 `localhost.mof` 檔案重新命名為 `<Configuration Name>.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-128">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="40593-129">在下列範例中，會使用上一節的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="40593-129">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="40593-130">您接著可以使用任何可接受的方法來將 `.mof` 檔案重新命名。</span><span class="sxs-lookup"><span data-stu-id="40593-130">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="40593-131">下列範例會使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40593-131">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="40593-132">建立總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="40593-132">Create the checkSum</span></span>

<span data-ttu-id="40593-133">儲存於提取伺服器或 SMB 共用上的每個 `.mof` 檔案都需要有相關聯的 `.checksum` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-133">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="40593-134">此檔案可讓用戶端知道相關聯的 `.mof` 檔案何時已變更且應再次下載。</span><span class="sxs-lookup"><span data-stu-id="40593-134">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="40593-135">您可以使用 [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) Cmdlet 來建立 **總和檢查碼** 。</span><span class="sxs-lookup"><span data-stu-id="40593-135">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="40593-136">您也可以使用 `-Path` 參數，針對檔案的目錄執行 `New-DSCCheckSum`。</span><span class="sxs-lookup"><span data-stu-id="40593-136">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="40593-137">如果總和檢查碼已經存在，您可以使用 `-Force` 參數強制重新建立它。</span><span class="sxs-lookup"><span data-stu-id="40593-137">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="40593-138">下列範例會指定包含上一節 `.mof` 檔案的目錄，並使用 `-Force` 參數。</span><span class="sxs-lookup"><span data-stu-id="40593-138">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="40593-139">系統將不會顯示任何輸出，但您現在應該會看到 `<GUID or Configuration Name>.mof.checksum` 檔案。</span><span class="sxs-lookup"><span data-stu-id="40593-139">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="40593-140">儲存 MOF 檔案與總和檢查碼的位置</span><span class="sxs-lookup"><span data-stu-id="40593-140">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="40593-141">在 DSC HTTP 提取伺服器上</span><span class="sxs-lookup"><span data-stu-id="40593-141">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="40593-142">當您設定 HTTP 提取伺服器時，如 [設定 DSC HTTP 提取伺服器](pullServer.md)中所述，您會針對 **ModulePath** 和 **ConfigurationPath** 索引碼指定目錄。</span><span class="sxs-lookup"><span data-stu-id="40593-142">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="40593-143">**ModulePath** 機碼指出應儲存模組的封裝 `.zip` 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="40593-143">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="40593-144">**ConfigurationPath** 指出應儲存所有 `.mof` 檔案與 `.checksum` 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="40593-144">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="40593-145">在 SMB 共用上</span><span class="sxs-lookup"><span data-stu-id="40593-145">On an SMB share</span></span>

<span data-ttu-id="40593-146">當您設定提取用戶端來使用 SMB 共用時，您會指定 **ConfigurationRepositoryShare** 。</span><span class="sxs-lookup"><span data-stu-id="40593-146">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare** .</span></span>
<span data-ttu-id="40593-147">所有 `.mof` 檔案和 `.checksum` 檔案接著都應儲存於 **ConfigurationRepositoryShare** 區塊的 **SourcePath** 目錄中。</span><span class="sxs-lookup"><span data-stu-id="40593-147">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="40593-148">下一步</span><span class="sxs-lookup"><span data-stu-id="40593-148">Next steps</span></span>

<span data-ttu-id="40593-149">接下來，您可以設定提取用戶端來提取指定的設定。</span><span class="sxs-lookup"><span data-stu-id="40593-149">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="40593-150">如需詳細資訊，請參閱下列任一份指南：</span><span class="sxs-lookup"><span data-stu-id="40593-150">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="40593-151">使用設定識別碼設定提取用戶端 (v4)</span><span class="sxs-lookup"><span data-stu-id="40593-151">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="40593-152">使用設定識別碼設定提取用戶端 (v5)</span><span class="sxs-lookup"><span data-stu-id="40593-152">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="40593-153">使用設定名稱設定提取用戶端 (v5)</span><span class="sxs-lookup"><span data-stu-id="40593-153">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="40593-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40593-154">See also</span></span>

- [<span data-ttu-id="40593-155">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="40593-155">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="40593-156">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="40593-156">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="40593-157">封裝資源並上傳到提取伺服器</span><span class="sxs-lookup"><span data-stu-id="40593-157">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
