---
title: 如何為可更新說明 CAB 檔案命名
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892994"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="635c4-102">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="635c4-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="635c4-103">本主題說明可更新的說明封包（）檔案的必要名稱格式 `.CAB` 。</span><span class="sxs-lookup"><span data-stu-id="635c4-103">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="635c4-104">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="635c4-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="635c4-105">可更新的封包（ `.CAB` ）檔案必須具有下列格式的名稱。</span><span class="sxs-lookup"><span data-stu-id="635c4-105">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="635c4-106">名稱的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="635c4-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="635c4-107">`<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 所傳回之**ModuleInfo**物件的**Name**屬性值。</span><span class="sxs-lookup"><span data-stu-id="635c4-107">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="635c4-108">`<ModuleGUID>`-模組資訊清單中**GUID**索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="635c4-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="635c4-109">`<UICulture>`-CAB 檔案中說明檔的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="635c4-109">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="635c4-110">這個值必須符合模組的 HelpInfo XML 檔案中其中一個**UICulture**元素的值。</span><span class="sxs-lookup"><span data-stu-id="635c4-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="635c4-111">例如，如果模組名稱是 "TestModule"，則模組 GUID 為 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，而 UI 文化特性為 "en-us"，則 CAB 檔案的名稱會是：</span><span class="sxs-lookup"><span data-stu-id="635c4-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
