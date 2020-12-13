---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立及上傳 CAB 檔案
description: 如何建立及上傳 CAB 檔案
ms.openlocfilehash: bdcf534f48cff27b403d82440ad4ec6a3212b67d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653892"
---
# <a name="how-to-create-and-upload-cab-files"></a><span data-ttu-id="bf70a-103">如何建立及上傳 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="bf70a-103">How to Create and Upload CAB Files</span></span>

<span data-ttu-id="bf70a-104">本主題說明如何建立可更新的說明 CAB 檔案，並將它們上傳至可更新的說明 Cmdlet 可以找到這些檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="bf70a-104">This topic explains how to create Updatable Help CAB files and upload them to the location where the Updatable Help cmdlets can find them.</span></span>

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a><span data-ttu-id="bf70a-105">如何建立及上傳可更新的說明 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="bf70a-105">How to Create and Upload Updatable Help CAB Files</span></span>

<span data-ttu-id="bf70a-106">您可以使用「可更新的說明」功能，以多種語言和文化特性為模組提供新的或已更新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-106">You can use the Updatable Help feature to deliver new or updated help files for a module in multiple languages and cultures.</span></span> <span data-ttu-id="bf70a-107">模組的可更新說明套件包含一個 HelpInfo XML 檔案，以及一個或多個封包 (`.CAB`) 檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-107">An Updatable Help package for a module consists of one HelpInfo XML file and one or more cabinet (`.CAB`) files.</span></span> <span data-ttu-id="bf70a-108">每個 CAB 檔案都包含一個 UI 文化特性中模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-108">Each CAB file contains help files for the module in one UI culture.</span></span> <span data-ttu-id="bf70a-109">使用下列程式建立 CAB 檔案以取得可更新的說明。</span><span class="sxs-lookup"><span data-stu-id="bf70a-109">Use the following procedure to create CAB files for Updatable Help.</span></span>

1. <span data-ttu-id="bf70a-110">依 UI 文化特性組織模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-110">Organize the help files for the module by UI culture.</span></span> <span data-ttu-id="bf70a-111">每個可更新的說明 CAB 檔案都包含一個 UI 文化特性中某個模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-111">Each Updatable Help CAB file contains the help files for one module in one UI culture.</span></span> <span data-ttu-id="bf70a-112">您可以為模組傳遞多個說明 CAB 檔案，每個都有不同的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="bf70a-112">You can deliver multiple help CAB files for the module, each for a different UI culture.</span></span>

1. <span data-ttu-id="bf70a-113">確認說明檔僅包含可更新的說明所允許的檔案類型，並針對說明檔架構進行驗證。</span><span class="sxs-lookup"><span data-stu-id="bf70a-113">Verify that help files include only the file types permitted for Updatable Help and validate them against a help file schema.</span></span> <span data-ttu-id="bf70a-114">如果 `Update-Help` Cmdlet 遇到無效或不是允許類型的檔案，則不會安裝不正確檔案，並會停止從 CAB 安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="bf70a-114">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB.</span></span> <span data-ttu-id="bf70a-115">如需允許的檔案類型清單，請參閱 [可更新的說明 CAB 檔案中允許的檔案類型](./file-types-permitted-in-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="bf70a-115">For a list of permitted file types, see [File Types Permitted in an Updatable Help CAB File](./file-types-permitted-in-an-updatable-help-cab-file.md).</span></span>

1. <span data-ttu-id="bf70a-116">以數位方式簽署說明檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-116">Digitally sign the help files.</span></span> <span data-ttu-id="bf70a-117">數位簽章並非必要，但它們是最佳作法。</span><span class="sxs-lookup"><span data-stu-id="bf70a-117">Digital signatures are not required, but they are a best practice.</span></span>

1. <span data-ttu-id="bf70a-118">在 UI 文化特性中包含模組的所有說明檔，而不只是新的或已變更的檔案。</span><span class="sxs-lookup"><span data-stu-id="bf70a-118">Include all of help files for the module in the UI culture, not only files that are new or have changed.</span></span> <span data-ttu-id="bf70a-119">如果 CAB 檔案不完整，則第一次下載說明檔或未下載每個更新的使用者，將不會有所有模組說明檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-119">If the CAB file is incomplete, users who download help files for the first time or do not download every update, will not have all of the module help files.</span></span>

1. <span data-ttu-id="bf70a-120">使用可建立封包檔的公用程式，例如 `MakeCab.exe` 。</span><span class="sxs-lookup"><span data-stu-id="bf70a-120">Use a utility that creates cabinet files, such as `MakeCab.exe`.</span></span> <span data-ttu-id="bf70a-121">PowerShell 不包含可建立 CAB 檔案的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf70a-121">PowerShell does not include cmdlets that create CAB files.</span></span>

1. <span data-ttu-id="bf70a-122">為 CAB 檔案命名。</span><span class="sxs-lookup"><span data-stu-id="bf70a-122">Name the CAB files.</span></span> <span data-ttu-id="bf70a-123">如需詳細資訊，請參閱 [如何命名可更新的說明 CAB](./how-to-name-an-updatable-help-cab-file.md)檔。</span><span class="sxs-lookup"><span data-stu-id="bf70a-123">For more information, see [How to Name an Updatable Help CAB File](./how-to-name-an-updatable-help-cab-file.md).</span></span>

1. <span data-ttu-id="bf70a-124">將模組的 CAB 檔案上傳至模組的 HelpInfo XML 檔案中 **HelpContentUri** 元素所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="bf70a-124">Upload the CAB files for the module to the location that is specified by the **HelpContentUri** element in the HelpInfo XML file for the module.</span></span> <span data-ttu-id="bf70a-125">然後，將 HelpInfo XML 檔案上傳至模組資訊清單的 **HelpInfoUri** 索引鍵所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="bf70a-125">Then upload the HelpInfo XML file to the location that is specified by the **HelpInfoUri** key of the module manifest.</span></span> <span data-ttu-id="bf70a-126">**HelpContentUri** 和 **HelpInfoUri** 可指向相同的位置。</span><span class="sxs-lookup"><span data-stu-id="bf70a-126">The **HelpContentUri** and **HelpInfoUri** can point to the same location.</span></span>

> [!CAUTION]
> <span data-ttu-id="bf70a-127">**HelpInfoUri** 索引鍵的值和 **HelpContentUri** 元素的開頭必須是 `http` 或 `https` 。</span><span class="sxs-lookup"><span data-stu-id="bf70a-127">The value of the **HelpInfoUri** key and the **HelpContentUri** element must begin with `http` or `https`.</span></span> <span data-ttu-id="bf70a-128">值必須指出網際網路位置，而且不得包含檔案名。</span><span class="sxs-lookup"><span data-stu-id="bf70a-128">The value must indicate an Internet location and it must not include a filename.</span></span>
