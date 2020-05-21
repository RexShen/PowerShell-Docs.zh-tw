---
title: 如何建立和上傳 CAB 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 37b31aa77dde23c1bd57a9af67e2232ef0827005
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557579"
---
# <a name="how-to-create-and-upload-cab-files"></a><span data-ttu-id="14ee0-102">如何建立及上傳 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="14ee0-102">How to Create and Upload CAB Files</span></span>

<span data-ttu-id="14ee0-103">本主題說明如何建立可更新的說明 CAB 檔案，並將其上傳至可更新的說明 Cmdlet 可以找到它們的位置。</span><span class="sxs-lookup"><span data-stu-id="14ee0-103">This topic explains how to create Updatable Help CAB files and upload them to the location where the Updatable Help cmdlets can find them.</span></span>

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a><span data-ttu-id="14ee0-104">如何建立和上傳可更新的說明 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="14ee0-104">How to Create and Upload Updatable Help CAB Files</span></span>

<span data-ttu-id="14ee0-105">您可以使用「可更新的說明」功能，以多種語言和文化特性為模組傳遞新的或更新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="14ee0-105">You can use the Updatable Help feature to deliver new or updated help files for a module in multiple languages and cultures.</span></span> <span data-ttu-id="14ee0-106">模組的可更新說明套件包含一個 HelpInfo XML 檔案和一或多個封包（。CAB）檔案。</span><span class="sxs-lookup"><span data-stu-id="14ee0-106">An Updatable Help package for a module consists of one HelpInfo XML file and one or more cabinet (.CAB) files.</span></span> <span data-ttu-id="14ee0-107">每個封包檔都包含一個 UI 文化特性中模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="14ee0-107">Each CAB file contains help files for the module in one UI culture.</span></span> <span data-ttu-id="14ee0-108">使用下列程式來建立可更新說明的封包檔。</span><span class="sxs-lookup"><span data-stu-id="14ee0-108">Use the following procedure to create CAB files for Updatable Help.</span></span>

1. <span data-ttu-id="14ee0-109">依 UI 文化特性來組織模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="14ee0-109">Organize the help files for the module by UI culture.</span></span> <span data-ttu-id="14ee0-110">每個可更新的說明封包檔都包含一個 UI 文化特性中某個模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="14ee0-110">Each Updatable Help CAB file contains the help files for one module in one UI culture.</span></span> <span data-ttu-id="14ee0-111">您可以為模組傳遞多個說明 CAB 檔案，每個檔案都適用于不同的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="14ee0-111">You can deliver multiple help CAB files for the module, each for a different UI culture.</span></span>

2. <span data-ttu-id="14ee0-112">確認說明檔只包含 [可更新的說明] 所允許的檔案類型，並根據說明檔案架構來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="14ee0-112">Verify that help files include only the file types permitted for Updatable Help and validate them against a help file schema.</span></span> <span data-ttu-id="14ee0-113">如果 `Update-Help` Cmdlet 遇到無效或不是允許類型的檔案，則不會安裝不正確檔案，而且會停止從 CAB 安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="14ee0-113">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB.</span></span> <span data-ttu-id="14ee0-114">如需允許的檔案類型清單，請參閱[可更新的說明 CAB 檔案中允許的檔案類型](./file-types-permitted-in-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="14ee0-114">For a list of permitted file types, see [File Types Permitted in an Updatable Help CAB File](./file-types-permitted-in-an-updatable-help-cab-file.md).</span></span>

3. <span data-ttu-id="14ee0-115">以數位方式簽署說明檔。</span><span class="sxs-lookup"><span data-stu-id="14ee0-115">Digitally sign the help files.</span></span> <span data-ttu-id="14ee0-116">數位簽章不是必要的，但它們是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="14ee0-116">Digital signatures are not required, but they are a best practice.</span></span>

4. <span data-ttu-id="14ee0-117">以 UI 文化特性包含模組的所有說明檔，而不只是新的或已變更的檔案。</span><span class="sxs-lookup"><span data-stu-id="14ee0-117">Include all of help files for the module in the UI culture, not only files that are new or have changed.</span></span> <span data-ttu-id="14ee0-118">如果 CAB 檔案不完整，則第一次下載說明檔案或未下載每個更新的使用者，將不會有所有模組說明檔案。</span><span class="sxs-lookup"><span data-stu-id="14ee0-118">If the CAB file is incomplete, users who download help files for the first time or do not download every update, will not have all of the module help files.</span></span>

5. <span data-ttu-id="14ee0-119">使用可建立封包檔的公用程式，例如 Makecab.exe。</span><span class="sxs-lookup"><span data-stu-id="14ee0-119">Use a utility that creates cabinet files, such as MakeCab.exe.</span></span> <span data-ttu-id="14ee0-120">Windows PowerShell 不包含建立 CAB 檔案的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14ee0-120">Windows PowerShell does not include cmdlets that create CAB files.</span></span>

6. <span data-ttu-id="14ee0-121">為 CAB 檔案命名。</span><span class="sxs-lookup"><span data-stu-id="14ee0-121">Name the CAB files.</span></span> <span data-ttu-id="14ee0-122">如需詳細資訊，請參閱[如何命名可更新的說明 CAB](./how-to-name-an-updatable-help-cab-file.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="14ee0-122">For more information, see [How to Name an Updatable Help CAB File](./how-to-name-an-updatable-help-cab-file.md).</span></span>

7. <span data-ttu-id="14ee0-123">將模組的 CAB 檔案上傳到模組的 HelpInfo XML 檔案中**HelpContentUri**元素所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="14ee0-123">Upload the CAB files for the module to the location that is specified by the **HelpContentUri** element in the HelpInfo XML file for the module.</span></span> <span data-ttu-id="14ee0-124">然後，將 HelpInfo XML 檔案上傳至模組資訊清單的**HelpInfoUri**索引鍵所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="14ee0-124">Then upload the HelpInfo XML file to the location that is specified by the **HelpInfoUri** key of the module manifest.</span></span> <span data-ttu-id="14ee0-125">**HelpContentUri**和**HelpInfoUri**可以指向相同的位置。</span><span class="sxs-lookup"><span data-stu-id="14ee0-125">The **HelpContentUri** and **HelpInfoUri** can point to the same location.</span></span>

> [!CAUTION]
> <span data-ttu-id="14ee0-126">**HelpInfoUri**索引鍵和**HelpContentUri**元素的值必須以 "HTTP" 或 "HTTPs" 開頭。</span><span class="sxs-lookup"><span data-stu-id="14ee0-126">The value of the **HelpInfoUri** key and the **HelpContentUri** element must begin with "http" or "https".</span></span> <span data-ttu-id="14ee0-127">此值必須指出網際網路位置，而且不能包含檔案名。</span><span class="sxs-lookup"><span data-stu-id="14ee0-127">The value must indicate an Internet location and it must not include a file name.</span></span>
