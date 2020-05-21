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
ms.openlocfilehash: 1f09146a9e6456584f67edb52407193d8a9330ce
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564784"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="a47aa-102">如何建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="a47aa-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="a47aa-103">本節中的此主題說明如何建立和填入說明資訊檔案（通常稱為「HelpInfo XML 檔案」），以取得 Windows PowerShell 可更新的說明功能。</span><span class="sxs-lookup"><span data-stu-id="a47aa-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="a47aa-104">HelpInfo XML 檔案總覽</span><span class="sxs-lookup"><span data-stu-id="a47aa-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="a47aa-105">HelpInfo XML 檔案是模組之可更新說明的主要資訊來源。</span><span class="sxs-lookup"><span data-stu-id="a47aa-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="a47aa-106">其中包含模組的說明檔位置、支援的 UI 文化特性，以及可更新的說明用來判斷使用者是否有最新說明檔案的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a47aa-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="a47aa-107">每個模組只有一個 HelpInfo XML 檔案，即使模組包含多個 UI 文化特性的多個說明檔案也一樣。</span><span class="sxs-lookup"><span data-stu-id="a47aa-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="a47aa-108">模組作者會建立 HelpInfo XML 檔案，並將它放在模組資訊清單中**HelpInfoUri**機碼所指定的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="a47aa-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="a47aa-109">當模組說明檔案更新並上傳時，模組作者會更新 HelpInfo XML 檔案，並以新版本取代原始 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a47aa-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="a47aa-110">請務必小心維護 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a47aa-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="a47aa-111">如果您上傳新檔案，但忘了遞增版本號碼，可更新的說明將不會將新的檔案下載到使用者的電腦。</span><span class="sxs-lookup"><span data-stu-id="a47aa-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="a47aa-112">如果您加入新 UI 文化特性的說明檔，但未更新 HelpInfo XML 檔案，或將它放在正確的位置，可更新的說明將不會下載新的檔案。</span><span class="sxs-lookup"><span data-stu-id="a47aa-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a47aa-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="a47aa-113">In this section</span></span>

<span data-ttu-id="a47aa-114">本節包含下列主題。</span><span class="sxs-lookup"><span data-stu-id="a47aa-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="a47aa-115">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="a47aa-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="a47aa-116">HelpInfo XML 範例檔案</span><span class="sxs-lookup"><span data-stu-id="a47aa-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="a47aa-117">如何為 HelpInfo XML 檔案命名</span><span class="sxs-lookup"><span data-stu-id="a47aa-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="a47aa-118">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="a47aa-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="a47aa-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a47aa-119">See Also</span></span>

[<span data-ttu-id="a47aa-120">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="a47aa-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
