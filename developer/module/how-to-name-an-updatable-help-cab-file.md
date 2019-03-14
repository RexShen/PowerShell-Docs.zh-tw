---
title: 如何命名的可更新的說明封包檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794752"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="2f625-102">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="2f625-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="2f625-103">本主題說明可更新說明的封包檔的必要的名稱格式 (。CAB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="2f625-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="2f625-104">如何為可更新說明 CAB 檔案命名</span><span class="sxs-lookup"><span data-stu-id="2f625-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="2f625-105">可更新的封包 (。CAB) 檔案必須具有下列格式的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f625-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="2f625-106">名稱的項目如下所示。</span><span class="sxs-lookup"><span data-stu-id="2f625-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="2f625-107">模組名稱值的**名稱**屬性**ModuleInfo**物件[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 會傳回。</span><span class="sxs-lookup"><span data-stu-id="2f625-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="2f625-108">ModuleGUID 值的**GUID**模組資訊清單中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2f625-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="2f625-109">UICulture UI 文化特性的封包檔中的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2f625-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="2f625-110">此值必須符合其中一個值**UICulture**模組 HelpInfo XML 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="2f625-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="2f625-111">例如，如果模組名稱是"TestModule 」，模組 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，和 UI 文化特性是"EN-US"，封包檔的名稱會是：</span><span class="sxs-lookup"><span data-stu-id="2f625-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`