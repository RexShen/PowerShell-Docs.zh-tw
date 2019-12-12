---
title: 如何設定 HelpInfo XML 版本號碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360677"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="2fcb0-102">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="2fcb0-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="2fcb0-103">本主題說明如何在可更新的說明資訊檔案（通常稱為「HelpInfo XML 檔案」）中設定並增加版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="2fcb0-104">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="2fcb0-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="2fcb0-105">HelpInfo XML 檔案中的版本號碼對於「可更新的說明」作業而言是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="2fcb0-106">只有當遠端 HelpInfo XML 檔案中 UI 文化特性的版本號碼大於本機 HelpInfo XML 中該 UI 文化特性的版本號碼，或沒有本機 HelpInfo XML 檔案時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[get-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 才會下載新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="2fcb0-107">HelpInfo XML 檔案會使用 Microsoft .NET Framework 的**system.object**類別中定義的4部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="2fcb0-108">格式為 `N1.N2.N3.N4`。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="2fcb0-109">模組作者可以使用**System. version**類別所允許的任何版本編號配置。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="2fcb0-110">「可更新的說明」只需要在該 UI 文化特性的新版 CAB 檔案上傳到 HelpInfo XML 檔案中的**HelpContentURI**元素所指定的位置時，才會增加 ui 文化特性的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="2fcb0-111">下列範例顯示在2.15.0.10 版本時，德文（de） UI 文化特性的 HelpInfo XML 檔案元素。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="2fcb0-112">UI 文化特性的版本號碼會反映該 UI 文化特性的 CAB 檔案版本。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="2fcb0-113">版本號碼會套用至整個 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="2fcb0-114">您無法為 CAB 檔案中的不同檔案設定不同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="2fcb0-115">每個 UI 文化特性的版本號碼會獨立評估，而且不需要與模組支援之其他 UI 文化特性的版本號碼相關。</span><span class="sxs-lookup"><span data-stu-id="2fcb0-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>