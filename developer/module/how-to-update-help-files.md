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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082303"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="d8339-102">如何更新說明檔</span><span class="sxs-lookup"><span data-stu-id="d8339-102">How to Update Help Files</span></span>

<span data-ttu-id="d8339-103">本主題說明如何更新為支援 Updatable Help 的模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="d8339-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="d8339-104">更新說明檔</span><span class="sxs-lookup"><span data-stu-id="d8339-104">Updating Help Files</span></span>

<span data-ttu-id="d8339-105">有許多原因可更新說明檔，例如更正錯誤、 釐清概念、 回答常見問題集、 加入新的檔案，或加入新的和更好的範例。</span><span class="sxs-lookup"><span data-stu-id="d8339-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="d8339-106">若要更新的說明檔：</span><span class="sxs-lookup"><span data-stu-id="d8339-106">To update a help file:</span></span>

1. <span data-ttu-id="d8339-107">變更的檔案。</span><span class="sxs-lookup"><span data-stu-id="d8339-107">Change the files.</span></span>

2. <span data-ttu-id="d8339-108">檔案轉譯為其他的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="d8339-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="d8339-109">收集所有說明檔 （新增、 變更和未變更） 的每個 UI 文化特性中的模組。</span><span class="sxs-lookup"><span data-stu-id="d8339-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="d8339-110">驗證 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="d8339-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="d8339-111">重新建置各 UI 文化特性的封包檔。</span><span class="sxs-lookup"><span data-stu-id="d8339-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="d8339-112">在 HelpInfo XML 檔案中，遞增版本號碼的每個 UI 文化特性的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8339-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="d8339-113">新的 CAB 檔案上傳至的值所指定的位置**HelpContentUri** HelpInfo XML 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="d8339-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="d8339-114">較舊的 CAB 檔案取代成新的封包檔。</span><span class="sxs-lookup"><span data-stu-id="d8339-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="d8339-115">已更新的 HelpInfo XML 檔案上傳至所指定的位置**HelpInfoUri**模組資訊清單中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d8339-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="d8339-116">使用新的檔案取代較舊的 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8339-116">Replace the older HelpInfo XML file with the new file.</span></span>