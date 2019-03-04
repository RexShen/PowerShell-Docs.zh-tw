---
title: 如何建立及上傳 CAB 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858644"
---
# <a name="how-to-create-and-upload-cab-files"></a><span data-ttu-id="d46db-102">如何建立及上傳 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="d46db-102">How to Create and Upload CAB Files</span></span>

<span data-ttu-id="d46db-103">本主題說明如何建立可更新說明的 CAB 檔案，然後將它們上傳至其中的可更新說明的 cmdlet 可以在其中找到它們的位置。</span><span class="sxs-lookup"><span data-stu-id="d46db-103">This topic explains how to create Updatable Help CAB files and upload them to the location where the Updatable Help cmdlets can find them.</span></span>

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a><span data-ttu-id="d46db-104">如何建立及上傳可更新的說明封包檔</span><span class="sxs-lookup"><span data-stu-id="d46db-104">How to Create and Upload Updatable Help CAB Files</span></span>

<span data-ttu-id="d46db-105">您可以使用 「 可更新的說明 」 功能，提供多種語言和文化特性中的模組的新的或更新的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-105">You can use the Updatable Help feature to deliver new or updated help files for a module in multiple languages and cultures.</span></span> <span data-ttu-id="d46db-106">模組的可更新的說明套件包含一個 HelpInfo XML 檔案和一或多個封包 (。CAB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-106">An Updatable Help package for a module consists of one HelpInfo XML file and one or more cabinet (.CAB) files.</span></span> <span data-ttu-id="d46db-107">每個封包檔包含一個 UI 文化特性中的模組的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-107">Each CAB file contains help files for the module in one UI culture.</span></span> <span data-ttu-id="d46db-108">使用下列程序來建立封包檔的可更新的說明。</span><span class="sxs-lookup"><span data-stu-id="d46db-108">Use the following procedure to create CAB files for Updatable Help.</span></span>

1. <span data-ttu-id="d46db-109">組織的 UI 文化特性之模組的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-109">Organize the help files for the module by UI culture.</span></span> <span data-ttu-id="d46db-110">每個可更新說明的 CAB 檔案包含一個 UI 文化特性中的一個模組的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-110">Each Updatable Help CAB file contains the help files for one module in one UI culture.</span></span> <span data-ttu-id="d46db-111">您可以提供多個說明對於模組，每個不同的 UI 文化特性的封包檔。</span><span class="sxs-lookup"><span data-stu-id="d46db-111">You can deliver multiple help CAB files for the module, each for a different UI culture.</span></span>

2. <span data-ttu-id="d46db-112">確認的說明檔包含只允許可更新說明的檔案類型和驗證的說明檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="d46db-112">Verify that help files include only the file types permitted for Updatable Help and validate them against a help file schema.</span></span> <span data-ttu-id="d46db-113">如果`Update-Help`cmdlet 發生檔案無效或不允許的型別，它不會安裝無效的檔案，並停止封包從安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-113">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB.</span></span> <span data-ttu-id="d46db-114">如需允許的檔案類型的清單，請參閱 <<c0> [ 可更新的說明封包檔中的檔案類型允許](./file-types-permitted-in-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="d46db-114">For a list of permitted file types, see [File Types Permitted in an Updatable Help CAB File](./file-types-permitted-in-an-updatable-help-cab-file.md).</span></span>

3. <span data-ttu-id="d46db-115">數位簽章說明檔。</span><span class="sxs-lookup"><span data-stu-id="d46db-115">Digitally sign the help files.</span></span> <span data-ttu-id="d46db-116">數位簽章是不必要的但最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d46db-116">Digital signatures are not required, but they are a best practice.</span></span>

4. <span data-ttu-id="d46db-117">包含所有文化特性，不只是新的檔案或變更的 UI 中的模組檔案的說明。</span><span class="sxs-lookup"><span data-stu-id="d46db-117">Include all of help files for the module in the UI culture, not only files that are new or have changed.</span></span> <span data-ttu-id="d46db-118">如果封包檔不完整，第一次下載說明檔案，或不要下載每個更新中，使用者不會所有模組的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="d46db-118">If the CAB file is incomplete, users who download help files for the first time or do not download every update, will not have all of the module help files.</span></span>

5. <span data-ttu-id="d46db-119">使用會建立封包檔，例如 MakeCab.exe 公用程式。</span><span class="sxs-lookup"><span data-stu-id="d46db-119">Use a utility that creates cabinet files, such as MakeCab.exe.</span></span> <span data-ttu-id="d46db-120">Windows PowerShell 不包含建立 CAB 檔案的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d46db-120">Windows PowerShell does not include cmdlets that create CAB files.</span></span>

6. <span data-ttu-id="d46db-121">命名封包檔。</span><span class="sxs-lookup"><span data-stu-id="d46db-121">Name the CAB files.</span></span> <span data-ttu-id="d46db-122">如需詳細資訊，請參閱 <<c0> [ 如何命名可更新的說明封包檔](./how-to-name-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="d46db-122">For more information, see [How to Name an Updatable Help CAB File](./how-to-name-an-updatable-help-cab-file.md).</span></span>

7. <span data-ttu-id="d46db-123">將模組的 CAB 檔案上傳到所指定的位置**HelpContentUri**模組 HelpInfo XML 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="d46db-123">Upload the CAB files for the module to the location that is specified by the **HelpContentUri** element in the HelpInfo XML file for the module.</span></span> <span data-ttu-id="d46db-124">然後將 HelpInfo XML 檔案上傳至所指定的位置**HelpInfoUri**模組資訊清單索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d46db-124">Then upload the HelpInfo XML file to the location that is specified by the **HelpInfoUri** key of the module manifest.</span></span> <span data-ttu-id="d46db-125">**HelpContentUri**並**HelpInfoUri**可以指向相同的位置。</span><span class="sxs-lookup"><span data-stu-id="d46db-125">The **HelpContentUri** and **HelpInfoUri** can point to the same location.</span></span>

> [!CAUTION]
> <span data-ttu-id="d46db-126">值**HelpInfoUri**機碼並**HelpContentUri**項目必須以"http"或"https"開頭。</span><span class="sxs-lookup"><span data-stu-id="d46db-126">The value of the **HelpInfoUri** key and the **HelpContentUri** element must begin with "http" or "https".</span></span> <span data-ttu-id="d46db-127">值必須表示網際網路位置，它不能包含檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d46db-127">The value must indicate an Internet location and it must not include a file name.</span></span>