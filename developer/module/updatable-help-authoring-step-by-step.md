---
title: 可更新的說明撰寫：Step-by-Step | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082119"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="62160-102">可更新的說明撰寫：逐步</span><span class="sxs-lookup"><span data-stu-id="62160-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="62160-103">此文件列出的程序撰寫可更新說明的步驟。</span><span class="sxs-lookup"><span data-stu-id="62160-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="62160-104">撰寫可更新的說明：逐步</span><span class="sxs-lookup"><span data-stu-id="62160-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="62160-105">可更新的說明專為一般使用者，但它也提供重要的優點模組作者和說明的寫入器，包括能夠加入的內容，修正錯誤、 提供多個 UI 文化特性，並回應使用者註解和要求，長時間之後模組已出貨。</span><span class="sxs-lookup"><span data-stu-id="62160-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="62160-106">本主題說明如何封裝的位置，並上傳的說明檔案，讓使用者可以下載並安裝它們使用[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62160-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="62160-107">下列步驟提供的支援更新說明的程序的概觀。</span><span class="sxs-lookup"><span data-stu-id="62160-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="62160-108">步驟 1：尋找說明檔中的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="62160-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="62160-109">建立可更新的說明的第一個步驟是尋找模組的說明檔案的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="62160-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="62160-110">實際上，您可以使用兩個不同的位置。</span><span class="sxs-lookup"><span data-stu-id="62160-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="62160-111">您可以在一個網際網路位置和說明內容封包檔在另一個網際網路位置保留模組的說明資訊檔 (HelpInfo XML-如下所述)。</span><span class="sxs-lookup"><span data-stu-id="62160-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="62160-112">所有說明內容封包檔的模組必須位於相同的位置。</span><span class="sxs-lookup"><span data-stu-id="62160-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="62160-113">您可以將不同模組的說明內容封包檔放在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="62160-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="62160-114">步驟 2：將 HelpInfoURI 金鑰新增至您的模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="62160-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="62160-115">新增**HelpInfoURI**到您的模組資訊清單索引鍵。</span><span class="sxs-lookup"><span data-stu-id="62160-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="62160-116">索引鍵的值是位置的 HelpInfo XML 檔案資訊的模組統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="62160-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="62160-117">為了安全性，位址必須以"http"或"https"開頭。</span><span class="sxs-lookup"><span data-stu-id="62160-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="62160-118">URI 應指定網際網路位置，但不是能包含 HelpInfo XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="62160-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="62160-119">例如：</span><span class="sxs-lookup"><span data-stu-id="62160-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="62160-120">步驟 3：建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="62160-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="62160-121">HelpInfo XML 資訊檔案包含說明檔案，以及您在每個支援的 UI 文化特性中的模組最新說明檔案的版本號碼的網際網路位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="62160-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="62160-122">每個 Windows PowerShell 模組具有一個 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="62160-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="62160-123">當您更新說明檔案時，編輯或取代 HelpInfo XML 檔案;您沒有加入另一個。</span><span class="sxs-lookup"><span data-stu-id="62160-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="62160-124">如需詳細資訊，請參閱 <<c0> [ 如何建立 HelpInfo XML 檔案](./how-to-create-a-helpinfo-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="62160-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="62160-125">步驟 4:登入您的說明檔</span><span class="sxs-lookup"><span data-stu-id="62160-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="62160-126">數位簽章是不必要的但它們是最佳做法建議，每當您共用檔案。</span><span class="sxs-lookup"><span data-stu-id="62160-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="62160-127">步驟 5:建立 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="62160-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="62160-128">使用會建立封包 (.cab) 檔案，例如 MakeCab.exe，若要建立的工具。包含您的模組的說明檔案的封包檔。</span><span class="sxs-lookup"><span data-stu-id="62160-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="62160-129">在每個支援的 UI 文化特性說明檔案的個別封包檔。</span><span class="sxs-lookup"><span data-stu-id="62160-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="62160-130">如需詳細資訊，請參閱 <<c0> [ 如何準備可更新的說明封包檔](./how-to-prepare-updatable-help-cab-files.md)。</span><span class="sxs-lookup"><span data-stu-id="62160-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="62160-131">步驟 6:將檔案上傳</span><span class="sxs-lookup"><span data-stu-id="62160-131">Step 6: Upload your files</span></span>

<span data-ttu-id="62160-132">若要發佈新的或更新的說明檔，將檔案上傳封包到所指定的網際網路位置**HelpContentUri** HelpInfo XML 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="62160-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="62160-133">然後，將 HelpInfo XML 檔案上傳至的值所指定的網際網路位置**HelpInfoUri**模組資訊清單中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="62160-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
