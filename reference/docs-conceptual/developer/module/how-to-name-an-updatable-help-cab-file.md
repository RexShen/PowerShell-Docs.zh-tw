---
title: 如何命名可更新的說明 CAB 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367157"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="b5fb1-102">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="b5fb1-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="b5fb1-103">本主題說明可更新的說明封包（的必要名稱格式。CAB）檔案。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="b5fb1-104">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="b5fb1-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="b5fb1-105">可更新的封包（。CAB）檔案的名稱必須是下列格式。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="b5fb1-106">名稱的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="b5fb1-107">ModuleName **ModuleInfo**物件的**Name**屬性值，以[取得模組](/powershell/module/Microsoft.PowerShell.Core/Get-Module)Cmdlet 傳回。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="b5fb1-108">ModuleGUID 模組資訊清單中**GUID**金鑰的值。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="b5fb1-109">UICulture CAB 檔案中說明檔的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="b5fb1-110">這個值必須符合模組的 HelpInfo XML 檔案中其中一個**UICulture**元素的值。</span><span class="sxs-lookup"><span data-stu-id="b5fb1-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="b5fb1-111">例如，如果模組名稱是 "TestModule"，則模組 GUID 為 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，而 UI 文化特性為 "en-us"，則 CAB 檔案的名稱會是：</span><span class="sxs-lookup"><span data-stu-id="b5fb1-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`