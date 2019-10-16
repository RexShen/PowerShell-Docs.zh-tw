---
title: 如何更新說明檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367137"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="0653c-102">如何更新說明檔</span><span class="sxs-lookup"><span data-stu-id="0653c-102">How to Update Help Files</span></span>

<span data-ttu-id="0653c-103">本主題說明如何更新支援「可更新的說明」之模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="0653c-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="0653c-104">更新說明檔</span><span class="sxs-lookup"><span data-stu-id="0653c-104">Updating Help Files</span></span>

<span data-ttu-id="0653c-105">更新說明檔的原因有很多，例如更正錯誤、闡明概念、回答常見問題、新增檔案，或加入新的更好的範例。</span><span class="sxs-lookup"><span data-stu-id="0653c-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="0653c-106">若要更新說明檔：</span><span class="sxs-lookup"><span data-stu-id="0653c-106">To update a help file:</span></span>

1. <span data-ttu-id="0653c-107">變更檔案。</span><span class="sxs-lookup"><span data-stu-id="0653c-107">Change the files.</span></span>

2. <span data-ttu-id="0653c-108">將檔案轉譯為其他 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="0653c-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="0653c-109">針對每個 UI 文化特性中的模組，收集所有說明檔（新的、已變更和不變）。</span><span class="sxs-lookup"><span data-stu-id="0653c-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="0653c-110">針對 XML 架構驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="0653c-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="0653c-111">重建每個 UI 文化特性的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="0653c-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="0653c-112">在 HelpInfo XML 檔案中，將每個 UI 文化特性的 CAB 檔案版本號碼遞增。</span><span class="sxs-lookup"><span data-stu-id="0653c-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="0653c-113">將新的 CAB 檔案上傳到 HelpInfo XML 檔案中**HelpContentUri**元素的值所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="0653c-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="0653c-114">以新的 CAB 檔案取代舊版的封包檔。</span><span class="sxs-lookup"><span data-stu-id="0653c-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="0653c-115">將更新的 HelpInfo XML 檔案上傳至模組資訊清單中的**HelpInfoUri**索引鍵所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="0653c-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="0653c-116">以新的檔案取代舊版的 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="0653c-116">Replace the older HelpInfo XML file with the new file.</span></span>