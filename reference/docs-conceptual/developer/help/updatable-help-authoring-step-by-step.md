---
title: 可更新的說明撰寫-逐步解說
ms.date: 09/13/2016
ms.openlocfilehash: c9214be3c3363a4e6354595b50cf76a17d49aa67
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893113"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="c20fa-102">可更新的說明撰寫：逐步</span><span class="sxs-lookup"><span data-stu-id="c20fa-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="c20fa-103">本檔列出撰寫可更新的說明程式中的步驟。</span><span class="sxs-lookup"><span data-stu-id="c20fa-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="c20fa-104">撰寫可更新的說明：逐步解說</span><span class="sxs-lookup"><span data-stu-id="c20fa-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="c20fa-105">「可更新的說明」是針對一般使用者所設計，但它也為「課程模組」和「協助」撰寫者提供顯著的好處，包括新增內容、修正錯誤、在多個 UI 文化特性中提供，以及回應使用者意見和要求的時間（在模組出貨之後）。</span><span class="sxs-lookup"><span data-stu-id="c20fa-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="c20fa-106">本主題說明如何封裝和上傳說明檔，讓使用者可以使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 來下載並安裝這些檔案。</span><span class="sxs-lookup"><span data-stu-id="c20fa-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="c20fa-107">下列步驟提供支援「可更新的說明」之程式的總覽。</span><span class="sxs-lookup"><span data-stu-id="c20fa-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="c20fa-108">步驟1：尋找您的說明檔案的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="c20fa-108">Step 1: Find an internet site for your help files</span></span>

<span data-ttu-id="c20fa-109">建立「可更新的說明」的第一個步驟是尋找模組的說明檔案的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-109">The first step in creating updatable help is to find an internet location for your module's help files.</span></span> <span data-ttu-id="c20fa-110">實際上，您可以使用兩個不同的位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="c20fa-111">您可以將模組的說明資訊檔案（如下所述的 HelpInfo XML）保留在一個網際網路位置，並將說明內容封包檔保存在另一個網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-111">You can keep your module's help information file (HelpInfo XML - described below) at one internet location and the help content CAB files at another internet location.</span></span> <span data-ttu-id="c20fa-112">模組的所有說明內容 CAB 檔案都必須位於相同的位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="c20fa-113">您可以將不同模組的說明內容 CAB 檔案放在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="c20fa-114">步驟2：將 HelpInfoURI 索引鍵新增至您的模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="c20fa-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="c20fa-115">在模組資訊清單中新增**HelpInfoURI**鍵。</span><span class="sxs-lookup"><span data-stu-id="c20fa-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="c20fa-116">索引鍵的值是模組之 HelpInfo XML 資訊檔案位置的統一資源識別元（URI）。</span><span class="sxs-lookup"><span data-stu-id="c20fa-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="c20fa-117">針對安全性，位址必須以 "HTTP" 或 "HTTPs" 開頭。</span><span class="sxs-lookup"><span data-stu-id="c20fa-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="c20fa-118">URI 應該指定網際網路位置，但不能包含 HelpInfo XML 檔案名。</span><span class="sxs-lookup"><span data-stu-id="c20fa-118">The URI should specify an internet location, but must not include the HelpInfo XML filename.</span></span>

<span data-ttu-id="c20fa-119">例如：</span><span class="sxs-lookup"><span data-stu-id="c20fa-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="c20fa-120">步驟3：建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="c20fa-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="c20fa-121">HelpInfo XML 資訊檔案包含您的說明檔的網際網路位置 URI，以及模組中每個支援的 UI 文化特性的最新說明檔案版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c20fa-121">The HelpInfo XML information file contains the URI of the internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="c20fa-122">每個 Windows PowerShell 模組都有一個 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c20fa-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="c20fa-123">當您更新說明檔時，可以編輯或取代 HelpInfo XML 檔案;您不會再新增另一個。</span><span class="sxs-lookup"><span data-stu-id="c20fa-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="c20fa-124">如需詳細資訊，請參閱 how [To Create a HELPINFO XML File](./how-to-create-a-helpinfo-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="c20fa-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-create-cab-files"></a><span data-ttu-id="c20fa-125">步驟4：建立 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="c20fa-125">Step 4: Create CAB files</span></span>

<span data-ttu-id="c20fa-126">使用可建立封包（）檔案（例如）的工具， `.cab` `MakeCab.exe` 建立包含模組說明檔的 cab 檔。</span><span class="sxs-lookup"><span data-stu-id="c20fa-126">Use a tool that creates cabinet (`.cab`) files, such as `MakeCab.exe`, to create a CAB file that contains the help files for your module.</span></span> <span data-ttu-id="c20fa-127">針對每個支援的 UI 文化特性中的說明檔，建立個別的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="c20fa-127">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="c20fa-128">如需詳細資訊，請參閱[如何準備可更新的說明 CAB](./how-to-prepare-updatable-help-cab-files.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="c20fa-128">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-5-upload-your-files"></a><span data-ttu-id="c20fa-129">步驟5：上傳您的檔案</span><span class="sxs-lookup"><span data-stu-id="c20fa-129">Step 5: Upload your files</span></span>

<span data-ttu-id="c20fa-130">若要發佈新的或已更新的說明檔案，請將 CAB 檔案上傳到 HelpInfo XML 檔案中**HelpContentUri**元素所指定的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-130">To publish new or updated help files, upload the CAB files to the internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="c20fa-131">然後，將 HelpInfo XML 檔案上傳至模組資訊清單中**HelpInfoUri**機碼的值所指定的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="c20fa-131">Then, upload the HelpInfo XML file to the internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
