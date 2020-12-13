---
ms.date: 09/12/2016
ms.topic: reference
title: 如何設定 HelpInfo XML 版本號碼
description: 如何設定 HelpInfo XML 版本號碼
ms.openlocfilehash: 9ef1940ca05d8aa9b04770013287490b71c8065a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658836"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="339ba-103">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="339ba-103">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="339ba-104">本主題說明如何在可更新的說明資訊檔案（通常稱為「HelpInfo XML 檔案」）中設定及增加版本號碼。</span><span class="sxs-lookup"><span data-stu-id="339ba-104">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="339ba-105">如何設定 HelpInfo XML 版本號碼</span><span class="sxs-lookup"><span data-stu-id="339ba-105">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="339ba-106">HelpInfo XML 檔案中的版本號碼對「可更新的說明」作業而言是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="339ba-106">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="339ba-107">只有當遠端 HelpInfo XML 檔案中的 UI 文化特性版本號碼大於本機 HelpInfo XML 中該 UI 文化特性的版本號碼，或沒有本機 HelpInfo XML 檔案時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 和 [Save Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 才會下載新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="339ba-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="339ba-108">HelpInfo XML 檔案會使用 Microsoft .NET Framework 的 **system.object** 類別中定義的四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="339ba-108">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="339ba-109">格式為 `N1.N2.N3.N4`。</span><span class="sxs-lookup"><span data-stu-id="339ba-109">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="339ba-110">模組作者可以使用 **System. version** 類別所允許的任何版本編號配置。</span><span class="sxs-lookup"><span data-stu-id="339ba-110">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="339ba-111">可更新的說明只需要當該 UI 文化特性的新版 CAB 檔上傳至 HelpInfo XML 檔案中的 **HelpContentURI** 元素所指定的位置時，ui 文化特性的版本號碼才會增加。</span><span class="sxs-lookup"><span data-stu-id="339ba-111">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="339ba-112">下列範例顯示在2.15.0.10 版本時，德文 (de) UI 文化特性的 HelpInfo XML 檔案元素。</span><span class="sxs-lookup"><span data-stu-id="339ba-112">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="339ba-113">UI 文化特性的版本號碼會反映該 UI 文化特性的 CAB 檔案版本。</span><span class="sxs-lookup"><span data-stu-id="339ba-113">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="339ba-114">版本號碼會套用至整個 CAB 檔。</span><span class="sxs-lookup"><span data-stu-id="339ba-114">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="339ba-115">您無法為 CAB 檔案中的不同檔案設定不同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="339ba-115">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="339ba-116">每個 UI 文化特性的版本號碼會獨立進行評估，而且不需要與模組所支援之其他 UI 文化特性的版本號碼相關。</span><span class="sxs-lookup"><span data-stu-id="339ba-116">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>
