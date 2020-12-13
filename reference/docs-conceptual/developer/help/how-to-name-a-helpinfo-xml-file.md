---
ms.date: 09/12/2016
ms.topic: reference
title: 如何為 HelpInfo XML 檔案命名
description: 如何為 HelpInfo XML 檔案命名
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659035"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="97174-103">如何為 HelpInfo XML 檔案命名</span><span class="sxs-lookup"><span data-stu-id="97174-103">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="97174-104">本主題說明可更新的說明資訊檔案（通常稱為 HelpInfo XML 檔案）所需的名稱格式。</span><span class="sxs-lookup"><span data-stu-id="97174-104">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="97174-105">如何為 HelpInfo XML 檔案命名</span><span class="sxs-lookup"><span data-stu-id="97174-105">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="97174-106">HelpInfo XML 檔案的名稱必須是下列格式。</span><span class="sxs-lookup"><span data-stu-id="97174-106">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="97174-107">名稱的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="97174-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="97174-108">`<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 傳回之 **ModuleInfo** 物件的 **Name** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="97174-108">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="97174-109">`<ModuleGUID>` -模組資訊清單中 **GUID** 索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="97174-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="97174-110">例如，如果模組名稱為 "TestModule"，且模組 GUID 為 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，則模組的 HelpInfo XML 檔案名為：</span><span class="sxs-lookup"><span data-stu-id="97174-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
