---
title: 如何建立 HelpInfo XML 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082408"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="2d913-102">如何建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="2d913-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="2d913-103">在本節中的此主題說明如何建立並填入說明資訊檔案，通常稱為 「 HelpInfo XML 檔案 」 的 Windows PowerShell 可更新說明的功能。</span><span class="sxs-lookup"><span data-stu-id="2d913-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="2d913-104">HelpInfo XML 檔案的概觀</span><span class="sxs-lookup"><span data-stu-id="2d913-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="2d913-105">HelpInfo XML 檔案是主要資訊來源可更新的說明模組。</span><span class="sxs-lookup"><span data-stu-id="2d913-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="2d913-106">它包含模組、 支援的 UI 文化特性和版本號碼可更新的說明用來判斷使用者是否有最新說明檔案的說明檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="2d913-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="2d913-107">每個模組會有一個 HelpInfo XML 檔案，即使模組包含多重 UI 文化特性的多個說明檔。</span><span class="sxs-lookup"><span data-stu-id="2d913-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="2d913-108">模組作者建立 HelpInfo XML 檔案，並將它放在所指定的網際網路位置**HelpInfoUri**模組資訊清單中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2d913-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="2d913-109">當模組的說明檔會更新，並上傳時，模組作者更新 HelpInfo XML 檔案，並以新版本取代原始的 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d913-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="2d913-110">請務必仔細維護的 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d913-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="2d913-111">如果您上傳新的檔案，但忘記要遞增版本號碼，可更新的說明不會下載新的檔案至使用者的電腦。</span><span class="sxs-lookup"><span data-stu-id="2d913-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="2d913-112">如果您加入新的 UI 文化特性的說明檔案，但不更新 HelpInfo XML 檔案或將它放在正確的位置，可更新的說明將不會下載新的檔案。</span><span class="sxs-lookup"><span data-stu-id="2d913-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2d913-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="2d913-113">In this section</span></span>

<span data-ttu-id="2d913-114">本節包含下列主題。</span><span class="sxs-lookup"><span data-stu-id="2d913-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="2d913-115">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="2d913-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="2d913-116">HelpInfo XML 範例檔案</span><span class="sxs-lookup"><span data-stu-id="2d913-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="2d913-117">如何命名 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="2d913-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="2d913-118">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="2d913-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="2d913-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d913-119">See Also</span></span>

[<span data-ttu-id="2d913-120">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="2d913-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)