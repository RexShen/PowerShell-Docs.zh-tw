---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立 HelpInfo XML 檔案
description: 如何建立 HelpInfo XML 檔案
ms.openlocfilehash: d5a24306aa6488fdefad0b7b1ea9e2978a93a7b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647719"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="8623b-103">如何建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="8623b-103">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="8623b-104">本章節中的主題說明如何建立和填入說明資訊檔（通常稱為 "HelpInfo XML file"），以取得 PowerShell 可更新的說明功能。</span><span class="sxs-lookup"><span data-stu-id="8623b-104">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="8623b-105">HelpInfo XML 檔案總覽</span><span class="sxs-lookup"><span data-stu-id="8623b-105">HelpInfo XML File Overview</span></span>

<span data-ttu-id="8623b-106">HelpInfo XML 檔案是有關模組可更新說明的主要資訊來源。</span><span class="sxs-lookup"><span data-stu-id="8623b-106">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="8623b-107">它包含模組的說明檔位置、支援的 UI 文化特性，以及可更新的說明用來判斷使用者是否有最新說明檔案的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8623b-107">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="8623b-108">即使模組包含多個 UI 文化特性的多個說明檔，每個模組都只會有一個 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8623b-108">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="8623b-109">模組作者會建立 HelpInfo XML 檔案，並將它放在模組資訊清單中 **HelpInfoUri** 索引鍵所指定的網際網路位置。</span><span class="sxs-lookup"><span data-stu-id="8623b-109">The module author creates the HelpInfo XML file and places it in the internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="8623b-110">當模組說明檔案更新並上傳時，模組作者會更新 HelpInfo XML 檔案，並以新版本取代原始的 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8623b-110">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="8623b-111">務必小心維護 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8623b-111">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="8623b-112">如果您上傳新檔案，但忘記遞增版本號碼，可更新的說明將不會將新檔案下載至使用者的電腦。</span><span class="sxs-lookup"><span data-stu-id="8623b-112">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="8623b-113">如果您加入新 UI 文化特性的說明檔，但未更新 HelpInfo XML 檔案，或將它放在正確的位置，可更新的說明將不會下載新的檔案。</span><span class="sxs-lookup"><span data-stu-id="8623b-113">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8623b-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="8623b-114">In this section</span></span>

<span data-ttu-id="8623b-115">本節包含下列主題。</span><span class="sxs-lookup"><span data-stu-id="8623b-115">This section includes the following topics.</span></span>

- [<span data-ttu-id="8623b-116">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="8623b-116">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="8623b-117">HelpInfo XML 範例檔案</span><span class="sxs-lookup"><span data-stu-id="8623b-117">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="8623b-118">如何為 HelpInfo XML 檔案命名</span><span class="sxs-lookup"><span data-stu-id="8623b-118">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="8623b-119">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="8623b-119">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="8623b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8623b-120">See Also</span></span>

[<span data-ttu-id="8623b-121">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="8623b-121">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
