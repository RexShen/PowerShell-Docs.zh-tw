---
title: 如何命名 HelpInfo XML 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794802"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="1b185-102">如何為 HelpInfo XML 檔案命名</span><span class="sxs-lookup"><span data-stu-id="1b185-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="1b185-103">本主題說明可更新的說明資訊檔案，通常稱為 HelpInfo XML 檔案的必要的名稱格式。</span><span class="sxs-lookup"><span data-stu-id="1b185-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="1b185-104">如何為 HelpInfo XML 檔案命名</span><span class="sxs-lookup"><span data-stu-id="1b185-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="1b185-105">HelpInfo XML 檔案必須具有下列格式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b185-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="1b185-106">名稱的項目如下所示。</span><span class="sxs-lookup"><span data-stu-id="1b185-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="1b185-107">模組名稱值的**名稱**屬性**ModuleInfo**物件[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 會傳回。</span><span class="sxs-lookup"><span data-stu-id="1b185-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="1b185-108">ModuleGUID 值的**GUID**模組資訊清單中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1b185-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="1b185-109">比方說，如果模組名稱是"TestModule 」，此模組的 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 模組 HelpInfo XML 檔案的名稱將會是：</span><span class="sxs-lookup"><span data-stu-id="1b185-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`