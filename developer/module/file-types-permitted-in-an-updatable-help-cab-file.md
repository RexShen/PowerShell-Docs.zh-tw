---
title: 允許可更新的檔案類型有助於封包檔 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862834"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="a6b8e-102">可更新的說明 CAB 檔案中允許的檔案類型</span><span class="sxs-lookup"><span data-stu-id="a6b8e-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="a6b8e-103">本主題列出並描述可更新說明的 CAB 檔案內容的需求。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="a6b8e-104">可更新的說明封包檔的需求</span><span class="sxs-lookup"><span data-stu-id="a6b8e-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="a6b8e-105">未壓縮的封包檔案內容是預設限制為 1 GB。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="a6b8e-106">若要略過此限制，使用者必須使用**Force**的參數[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>
<span data-ttu-id="a6b8e-107">未壓縮的封包檔案內容是預設限制為 1 GB。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-107">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="a6b8e-108">若要略過此限制，使用者必須使用**Force**的參數[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-108">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="a6b8e-109">若要確保從網際網路下載說明檔的安全性，可更新說明的 CAB 檔案可以包含僅下面所列的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-109">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="a6b8e-110">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)指令程式會驗證所有的檔案，針對 [說明] 主題的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-110">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="a6b8e-111">如果`Update-Help`cmdlet 發生檔案無效或不允許的型別，它不會安裝無效的檔案，並停止使用者的電腦上封包從安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-111">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>
<span data-ttu-id="a6b8e-112">若要確保從網際網路下載說明檔的安全性，可更新說明的 CAB 檔案可以包含僅下面所列的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-112">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="a6b8e-113">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)指令程式會驗證所有的檔案，針對 [說明] 主題的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-113">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="a6b8e-114">如果`Update-Help`cmdlet 發生檔案無效或不允許的型別，它不會安裝無效的檔案，並停止使用者的電腦上封包從安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-114">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="a6b8e-115">以 XML 為基礎之 cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-115">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="a6b8e-116">以 XML 為基礎的說明主題的指令碼和函式。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-116">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="a6b8e-117">Windows PowerShell 提供者以 XML 為基礎說明主題。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-117">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="a6b8e-118">以文字為基礎的主題，例如說明主題。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-118">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="a6b8e-119">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)驗證封包內容，當它解壓縮封包檔。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-119">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="a6b8e-120">如果`Update-Help`發現不相容的檔案類型的可更新說明的 CAB 檔案中，它會產生終止錯誤並停止作業。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-120">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="a6b8e-121">它不會安裝任何說明檔從封包，甚至是那些相容的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-121">It does not install any help files from the CAB, even those of compliant file types.</span></span>
<span data-ttu-id="a6b8e-122">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)驗證封包內容，當它解壓縮封包檔。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-122">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="a6b8e-123">如果`Update-Help`發現不相容的檔案類型的可更新說明的 CAB 檔案中，它會產生終止錯誤並停止作業。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-123">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="a6b8e-124">它不會安裝任何說明檔從封包，甚至是那些相容的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a6b8e-124">It does not install any help files from the CAB, even those of compliant file types.</span></span>