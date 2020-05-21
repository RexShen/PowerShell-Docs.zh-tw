---
title: 可更新的說明如何運作 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: e555741185f3d17b4099671d70dbc0545bfd5306
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560231"
---
# <a name="how-updatable-help-works"></a><span data-ttu-id="054a5-102">可更新的說明如何運作</span><span class="sxs-lookup"><span data-stu-id="054a5-102">How Updatable Help Works</span></span>

<span data-ttu-id="054a5-103">本主題說明「可更新的協助」如何處理每個模組的 HelpInfo XML 檔案和封包檔，並為使用者安裝更新的說明。</span><span class="sxs-lookup"><span data-stu-id="054a5-103">This topic explains how Updatable Help processes the HelpInfo XML file and CAB files for each module, and installs updated help for users.</span></span>

## <a name="the-update-help-process"></a><span data-ttu-id="054a5-104">Update-Help 程式</span><span class="sxs-lookup"><span data-stu-id="054a5-104">The Update-Help Process</span></span>

<span data-ttu-id="054a5-105">下列清單說明當使用者執行命令來更新特定 UI 文化特性中模組的說明檔時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 的動作。</span><span class="sxs-lookup"><span data-stu-id="054a5-105">The following list describes the actions of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet when a user runs a command to update the help files for a module in a particular UI culture.</span></span>

1. <span data-ttu-id="054a5-106">`Update-Help`從模組資訊清單中的**HelpInfoURI**索引鍵值所指定的位置取得遠端 HelpInfo XML 檔案，並根據架構來驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-106">`Update-Help` gets the remote HelpInfo XML file from the location specified by the value of the **HelpInfoURI** key in the module manifest and validates the file against the schema.</span></span> <span data-ttu-id="054a5-107">（若要查看架構，請參閱[HELPINFO XML 架構](./helpinfo-xml-schema.md)）。然後 `Update-Help` 在使用者電腦上的模組目錄中尋找模組的本機 HELPINFO XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-107">(To view the schema, see [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Then `Update-Help` looks for a local HelpInfo XML file for the module in the module directory on the user's computer.</span></span>

2. <span data-ttu-id="054a5-108">`Update-Help`比較模組的遠端和本機 HelpInfo XML 檔案中指定的 UI 文化特性之說明檔的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="054a5-108">`Update-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="054a5-109">如果遠端檔案上的版本號碼大於本機檔案上的版本號碼，或如果沒有模組的本機 HelpInfo XML 檔案，則準備下載新的說明檔 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="054a5-109">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file for the module, `Update-Help` prepares to download new help files.</span></span>

3. <span data-ttu-id="054a5-110">`Update-Help`從遠端 HelpInfo XML 檔案中的**HelpContentUri**元素所指定的位置，選取模組的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-110">`Update-Help` selects the CAB file for the module from the location specified by the **HelpContentUri** element in the remote HelpInfo XML file.</span></span> <span data-ttu-id="054a5-111">它會使用模組名稱、模組 GUID 和 UI 文化特性來識別 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-111">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="054a5-112">`Update-Help`下載封包檔、解壓縮它、驗證說明內容檔案，並將說明內容檔案儲存在使用者電腦上模組目錄的特定語言子目錄中。</span><span class="sxs-lookup"><span data-stu-id="054a5-112">`Update-Help` downloads the CAB file, unpacks it, validates the help content files, and saves the help content files in the language-specific subdirectory of the module directory on the user's computer.</span></span>

5. <span data-ttu-id="054a5-113">`Update-Help`藉由複製遠端 HelpInfo XML 檔案來建立本機 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-113">`Update-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="054a5-114">它會編輯本機 HelpInfo XML 檔案，使其只包含其所安裝之 CAB 檔案的元素。</span><span class="sxs-lookup"><span data-stu-id="054a5-114">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it installed.</span></span> <span data-ttu-id="054a5-115">然後，它會將本機 HelpInfo XML 檔案儲存在模組目錄中，並結束更新。</span><span class="sxs-lookup"><span data-stu-id="054a5-115">Then it saves the local HelpInfo XML file in the module directory and concludes the update.</span></span>

## <a name="the-save-help-process"></a><span data-ttu-id="054a5-116">儲存輔助程式</span><span class="sxs-lookup"><span data-stu-id="054a5-116">The Save-Help Process</span></span>

<span data-ttu-id="054a5-117">下列清單說明當使用者執行命令來更新檔案共用中的說明檔，然後使用這些檔案來更新使用者電腦上的說明檔時， [Save Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)和[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 的動作。</span><span class="sxs-lookup"><span data-stu-id="054a5-117">The following list describes the actions of the [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) and [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets when a user runs commands to update the help files in a file share, and then use those files to update the help files on the user's computer.</span></span>

<span data-ttu-id="054a5-118">此 `Save-Help` Cmdlet 會執行下列動作，以回應命令，將模組的說明檔儲存在**DestinationPath**參數所指定的檔案共用中。</span><span class="sxs-lookup"><span data-stu-id="054a5-118">The `Save-Help` cmdlet performs the following actions in response to a command to save the help files for a module in a file share that is specified by the **DestinationPath** parameter.</span></span>

1. <span data-ttu-id="054a5-119">`Save-Help`從模組資訊清單中的**HelpInfoURI**索引鍵值所指定的位置取得遠端 HelpInfo XML 檔案，並根據架構來驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-119">`Save-Help` gets  the remote HelpInfo XML file from the location specified by the value of the **HelpInfoURI** key in the module manifest and validates the file against the schema.</span></span> <span data-ttu-id="054a5-120">（若要查看架構，請參閱[HELPINFO XML 架構](./helpinfo-xml-schema.md)）。然後在 `Save-Help` 命令中的**DestinationPath**參數所指定的目錄中尋找本機 HelpInfo XML 檔案 `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="054a5-120">(To view the schema, see [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Then `Save-Help` looks for a local HelpInfo XML file in the directory that is specified by the **DestinationPath** parameter in the `Save-Help` command.</span></span>

2. <span data-ttu-id="054a5-121">`Save-Help`比較模組的遠端和本機 HelpInfo XML 檔案中指定的 UI 文化特性之說明檔的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="054a5-121">`Save-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="054a5-122">如果遠端檔案上的版本號碼大於本機檔案上的版本號碼，或如果**DestinationPath**目錄中沒有適用于此模組的本機 HelpInfo XML 檔案，則 `Save-Help` 準備下載新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="054a5-122">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file for the module in the **DestinationPath** directory, `Save-Help` prepares to download new help files.</span></span>

3. <span data-ttu-id="054a5-123">`Save-Help`從遠端 HelpInfo XML 檔案中的**HelpContentUri**元素所指定的位置，選取模組的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-123">`Save-Help` selects the CAB file for the module from the location specified by the **HelpContentUri** element in the remote HelpInfo XML file.</span></span> <span data-ttu-id="054a5-124">它會使用模組名稱、模組 GUID 和 UI 文化特性來識別 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-124">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="054a5-125">`Save-Help`下載封包檔，並將它儲存在**DestinationPath**目錄中。</span><span class="sxs-lookup"><span data-stu-id="054a5-125">`Save-Help` downloads the CAB file and saves it in the **DestinationPath** directory.</span></span> <span data-ttu-id="054a5-126">（它不會建立任何語言特定的子目錄）。</span><span class="sxs-lookup"><span data-stu-id="054a5-126">(It does not create any language-specific subdirectories.)</span></span>

5. <span data-ttu-id="054a5-127">`Save-Help`藉由複製遠端 HelpInfo XML 檔案來建立本機 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-127">`Save-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="054a5-128">它會編輯本機 HelpInfo XML 檔案，使其只包含所儲存之 CAB 檔案的元素。</span><span class="sxs-lookup"><span data-stu-id="054a5-128">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it saved.</span></span> <span data-ttu-id="054a5-129">然後，它會將本機 HelpInfo XML 檔案儲存在**DestinationPath**目錄中，並結束更新。</span><span class="sxs-lookup"><span data-stu-id="054a5-129">Then it saves the local HelpInfo XML file in the  **DestinationPath** directory and concludes the update.</span></span>

   <span data-ttu-id="054a5-130">此 `Update-Help` Cmdlet 會執行下列動作，以回應命令，從**SourcePath**參數所指定之檔案共用中的檔案更新使用者電腦上的說明檔。</span><span class="sxs-lookup"><span data-stu-id="054a5-130">The `Update-Help` cmdlet performs the following actions in response to a command to update the help files on a user's computer from the files in a file share that is specified by the **SourcePath** parameter.</span></span>

1. <span data-ttu-id="054a5-131">`Update-Help`從**SourcePath**目錄取得遠端 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-131">`Update-Help` gets the remote HelpInfo XML file from the **SourcePath** directory.</span></span> <span data-ttu-id="054a5-132">然後它會在使用者電腦上的模組目錄中尋找本機 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-132">Then it looks for a local HelpInfo XML file in the module directory on the user's computer.</span></span>

2. <span data-ttu-id="054a5-133">`Update-Help`比較模組的遠端和本機 HelpInfo XML 檔案中指定的 UI 文化特性之說明檔的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="054a5-133">`Update-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="054a5-134">如果遠端檔案上的版本號碼大於本機檔案上的版本號碼，或如果沒有本機 HelpInfo XML 檔案，則 `Update-Help` 準備安裝新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="054a5-134">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file, `Update-Help` prepares to install new help files.</span></span>

3. <span data-ttu-id="054a5-135">`Update-Help`從**SourcePath**目錄選取模組的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-135">`Update-Help` selects the CAB file for the module from **SourcePath** directory.</span></span> <span data-ttu-id="054a5-136">它會使用模組名稱、模組 GUID 和 UI 文化特性來識別 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-136">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="054a5-137">`Update-Help`解壓縮封包檔、驗證說明內容檔案，並將說明內容檔案儲存在使用者電腦上模組目錄的特定語言子目錄中。</span><span class="sxs-lookup"><span data-stu-id="054a5-137">`Update-Help` unpacks the CAB file, validates the help content files, and saves the help content files in the language-specific subdirectory of the module directory on the user's computer.</span></span>

5. <span data-ttu-id="054a5-138">`Update-Help`藉由複製遠端 HelpInfo XML 檔案來建立本機 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="054a5-138">`Update-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="054a5-139">它會編輯本機 HelpInfo XML 檔案，使其只包含其所安裝之 CAB 檔案的元素。</span><span class="sxs-lookup"><span data-stu-id="054a5-139">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it installed.</span></span> <span data-ttu-id="054a5-140">然後，它會將本機 HelpInfo XML 檔案儲存在模組目錄中，並結束更新。</span><span class="sxs-lookup"><span data-stu-id="054a5-140">Then it saves the local HelpInfo XML file in the module directory and concludes the update.</span></span>
