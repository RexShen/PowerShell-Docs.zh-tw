---
ms.date: 09/13/2016
ms.topic: reference
title: 可更新的說明撰寫-逐步解說
description: 可更新的說明撰寫-逐步解說
ms.openlocfilehash: c4aecdb801cac16c9cb07853317835fd87e6a0a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658818"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="6114e-103">可更新的說明撰寫：逐步</span><span class="sxs-lookup"><span data-stu-id="6114e-103">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="6114e-104">這份檔列出撰寫可更新的說明之程式中的步驟。</span><span class="sxs-lookup"><span data-stu-id="6114e-104">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="6114e-105">撰寫可更新的說明：逐步解說</span><span class="sxs-lookup"><span data-stu-id="6114e-105">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="6114e-106">「可更新的說明」是專為使用者所設計，但也為模組作者和說明作者提供顯著的優點，包括新增內容、修正錯誤、在多個 UI 文化特性中提供的功能，以及回應使用者批註和要求，但在課程模組寄送之後。</span><span class="sxs-lookup"><span data-stu-id="6114e-106">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="6114e-107">本主題說明如何封裝和上傳說明檔，讓使用者可以使用 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 和 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 來下載和安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="6114e-107">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="6114e-108">下列步驟提供支援「可更新的說明」之程式的總覽。</span><span class="sxs-lookup"><span data-stu-id="6114e-108">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="6114e-109">步驟1：尋找您的說明檔的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="6114e-109">Step 1: Find an internet site for your help files</span></span>

<span data-ttu-id="6114e-110">建立可更新的說明的第一個步驟是尋找您模組說明檔的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="6114e-110">The first step in creating updatable help is to find an internet location for your module's help files.</span></span> <span data-ttu-id="6114e-111">實際上，您可以使用兩個不同的位置。</span><span class="sxs-lookup"><span data-stu-id="6114e-111">Actually, you can use two different locations.</span></span> <span data-ttu-id="6114e-112">您可以將模組的說明資訊檔案 (HelpInfo XML，如下所述) 在一個網際網路位置，以及位於另一個網際網路位置的說明內容封包檔。</span><span class="sxs-lookup"><span data-stu-id="6114e-112">You can keep your module's help information file (HelpInfo XML - described below) at one internet location and the help content CAB files at another internet location.</span></span> <span data-ttu-id="6114e-113">模組的所有說明內容 CAB 檔案都必須位於相同的位置。</span><span class="sxs-lookup"><span data-stu-id="6114e-113">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="6114e-114">您可以將不同模組的說明內容封包檔放在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="6114e-114">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="6114e-115">步驟2：將 HelpInfoURI 索引鍵新增至您的模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="6114e-115">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="6114e-116">將 **HelpInfoURI** 索引鍵新增至您的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="6114e-116">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="6114e-117">索引鍵的值是您模組的 HelpInfo XML 資訊檔位置 (URI) 的統一資源識別項。</span><span class="sxs-lookup"><span data-stu-id="6114e-117">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="6114e-118">基於安全性，位址必須以 "HTTP" 或 "HTTPs" 開頭。</span><span class="sxs-lookup"><span data-stu-id="6114e-118">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="6114e-119">URI 應該指定網際網路位置，但不能包含 HelpInfo XML 檔案名。</span><span class="sxs-lookup"><span data-stu-id="6114e-119">The URI should specify an internet location, but must not include the HelpInfo XML filename.</span></span>

<span data-ttu-id="6114e-120">例如：</span><span class="sxs-lookup"><span data-stu-id="6114e-120">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="6114e-121">步驟3：建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="6114e-121">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="6114e-122">HelpInfo XML 資訊檔包含說明檔的網際網路位置 URI，以及模組中每個支援的 UI 文化特性的最新說明檔案版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6114e-122">The HelpInfo XML information file contains the URI of the internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="6114e-123">每個 Windows PowerShell 模組都有一個 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6114e-123">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="6114e-124">當您更新說明檔時，您可以編輯或取代 HelpInfo XML 檔案。您不會新增另一個。</span><span class="sxs-lookup"><span data-stu-id="6114e-124">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="6114e-125">如需詳細資訊，請參閱 [如何建立 HELPINFO XML](./how-to-create-a-helpinfo-xml-file.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="6114e-125">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-create-cab-files"></a><span data-ttu-id="6114e-126">步驟4：建立 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="6114e-126">Step 4: Create CAB files</span></span>

<span data-ttu-id="6114e-127">使用可建立封包 () 檔（例如）的工具， `.cab` `MakeCab.exe` 建立包含模組說明檔的封包檔。</span><span class="sxs-lookup"><span data-stu-id="6114e-127">Use a tool that creates cabinet (`.cab`) files, such as `MakeCab.exe`, to create a CAB file that contains the help files for your module.</span></span> <span data-ttu-id="6114e-128">針對每個支援的 UI 文化特性中的說明檔建立個別的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="6114e-128">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="6114e-129">如需詳細資訊，請參閱 [如何準備可更新](./how-to-prepare-updatable-help-cab-files.md)的說明 CAB 檔。</span><span class="sxs-lookup"><span data-stu-id="6114e-129">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-5-upload-your-files"></a><span data-ttu-id="6114e-130">步驟5：上傳您的檔案</span><span class="sxs-lookup"><span data-stu-id="6114e-130">Step 5: Upload your files</span></span>

<span data-ttu-id="6114e-131">若要發佈新的或更新的說明檔，請將 CAB 檔案上傳至 HelpInfo XML 檔案中 **HelpContentUri** 元素所指定的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="6114e-131">To publish new or updated help files, upload the CAB files to the internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="6114e-132">然後，將 HelpInfo XML 檔案上傳至模組資訊清單中 **HelpInfoUri** 索引鍵值所指定的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="6114e-132">Then, upload the HelpInfo XML file to the internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
