---
ms.date: 09/12/2016
ms.topic: reference
title: 如何為可更新說明 CAB 檔案命名
description: 如何為可更新說明 CAB 檔案命名
ms.openlocfilehash: 57ea188d07a382d1a986a49c9ae22c5919dafa8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658912"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="565d4-103">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="565d4-103">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="565d4-104">本主題說明可更新的說明封包 () 檔案的必要名稱格式 `.CAB` 。</span><span class="sxs-lookup"><span data-stu-id="565d4-104">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="565d4-105">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="565d4-105">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="565d4-106">可更新的封包 (`.CAB`) 檔必須具有下列格式的名稱。</span><span class="sxs-lookup"><span data-stu-id="565d4-106">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="565d4-107">名稱的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="565d4-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="565d4-108">`<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 傳回之 **ModuleInfo** 物件的 **Name** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="565d4-108">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="565d4-109">`<ModuleGUID>` -模組資訊清單中 **GUID** 索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="565d4-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="565d4-110">`<UICulture>` -CAB 檔案中說明檔的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="565d4-110">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="565d4-111">此值必須符合模組之 HelpInfo XML 檔案中其中一個 **UICulture** 元素的值。</span><span class="sxs-lookup"><span data-stu-id="565d4-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="565d4-112">例如，如果模組名稱為 "TestModule"，則模組 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，而 UI 文化特性為 "en-us"，CAB 檔案的名稱會是：</span><span class="sxs-lookup"><span data-stu-id="565d4-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
