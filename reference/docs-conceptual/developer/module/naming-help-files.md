---
title: 命名說明檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367007"
---
# <a name="naming-help-files"></a><span data-ttu-id="06830-102">為說明檔案命名</span><span class="sxs-lookup"><span data-stu-id="06830-102">Naming Help Files</span></span>

<span data-ttu-id="06830-103">本主題說明如何命名以 XML 為基礎的說明檔，讓[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 可以找到它。</span><span class="sxs-lookup"><span data-stu-id="06830-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="06830-104">每個命令類型的名稱需求都不同。</span><span class="sxs-lookup"><span data-stu-id="06830-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="06830-105">Cmdlet 說明檔</span><span class="sxs-lookup"><span data-stu-id="06830-105">Cmdlet Help Files</span></span>

<span data-ttu-id="06830-106">C# Cmdlet 的說明檔必須命名為定義 Cmdlet 所在的元件。</span><span class="sxs-lookup"><span data-stu-id="06830-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="06830-107">使用下列檔案名格式：</span><span class="sxs-lookup"><span data-stu-id="06830-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="06830-108">即使元件是一個嵌套模組，也需要元件名稱格式。</span><span class="sxs-lookup"><span data-stu-id="06830-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="06830-109">例如， [new-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)Cmdlet 定義于 Microsoft. PowerShell 元件中。</span><span class="sxs-lookup"><span data-stu-id="06830-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="06830-110">`Get-Help` Cmdlet 只會在模組目錄中的 dll-help 檔案中尋找 `Get-WinEvent` Cmdlet 的說明主題，。</span><span class="sxs-lookup"><span data-stu-id="06830-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="06830-111">提供者說明檔</span><span class="sxs-lookup"><span data-stu-id="06830-111">Provider Help files</span></span>

<span data-ttu-id="06830-112">Windows PowerShell 提供者的說明檔必須針對定義提供者的元件命名。</span><span class="sxs-lookup"><span data-stu-id="06830-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="06830-113">使用下列檔案名格式：</span><span class="sxs-lookup"><span data-stu-id="06830-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="06830-114">即使元件是一個嵌套模組，也需要元件名稱格式。</span><span class="sxs-lookup"><span data-stu-id="06830-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="06830-115">例如，憑證提供者是在 Microsoft. PowerShell. .dll 元件中定義。</span><span class="sxs-lookup"><span data-stu-id="06830-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="06830-116">`Get-Help` Cmdlet 只會在模組目錄中的 dll-help 檔案中尋找憑證提供者的說明主題。</span><span class="sxs-lookup"><span data-stu-id="06830-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="06830-117">函數說明檔</span><span class="sxs-lookup"><span data-stu-id="06830-117">Function Help Files</span></span>

<span data-ttu-id="06830-118">您可以使用以[批註為基礎的說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)來記載函式，或在 XML 說明檔中記載函數。</span><span class="sxs-lookup"><span data-stu-id="06830-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="06830-119">當函式記載于 XML 檔案時，函式必須有一個 `.ExternalHelp` comment 關鍵字，才能將此函數與 XML 檔案產生關聯。</span><span class="sxs-lookup"><span data-stu-id="06830-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="06830-120">否則，`Get-Help` Cmdlet 就找不到說明檔。</span><span class="sxs-lookup"><span data-stu-id="06830-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="06830-121">函數說明檔的名稱沒有任何技術需求。</span><span class="sxs-lookup"><span data-stu-id="06830-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="06830-122">不過，最佳作法是為定義函數的腳本模組命名說明檔。</span><span class="sxs-lookup"><span data-stu-id="06830-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="06830-123">例如，下列函式定義于 MyModule. .psm1 檔案中。</span><span class="sxs-lookup"><span data-stu-id="06830-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="06830-124">CIM 命令說明檔</span><span class="sxs-lookup"><span data-stu-id="06830-124">CIM Command Help Files</span></span>

<span data-ttu-id="06830-125">CIM 命令的說明檔必須針對定義 CIM 命令的 CDXML 檔案命名。</span><span class="sxs-lookup"><span data-stu-id="06830-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="06830-126">使用下列檔案名格式：</span><span class="sxs-lookup"><span data-stu-id="06830-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="06830-127">CIM 命令定義于 CDXML 檔案中，這些檔案可以包含在模組中當做嵌套模組。</span><span class="sxs-lookup"><span data-stu-id="06830-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="06830-128">當 CIM 命令以函式的形式匯入到會話時，Windows PowerShell 會將 `.ExternalHelp` comment 關鍵字新增至函式定義，將函式與為定義 CIM 命令的 CDXML 檔案所命名的 XML 說明檔產生關聯。</span><span class="sxs-lookup"><span data-stu-id="06830-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="06830-129">編寫工作流程說明檔的腳本</span><span class="sxs-lookup"><span data-stu-id="06830-129">Script Workflow Help Files</span></span>

<span data-ttu-id="06830-130">模組中所含的腳本工作流程可以記錄在以 XML 為基礎的說明檔中。</span><span class="sxs-lookup"><span data-stu-id="06830-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="06830-131">說明檔的名稱沒有任何技術需求。</span><span class="sxs-lookup"><span data-stu-id="06830-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="06830-132">不過，最佳作法是為定義腳本工作流程的腳本模組命名說明檔。</span><span class="sxs-lookup"><span data-stu-id="06830-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="06830-133">例如：</span><span class="sxs-lookup"><span data-stu-id="06830-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="06830-134">與其他已編寫腳本的命令不同，腳本工作流程並不需要 `.ExternalHelp` comment 關鍵字，就能將它們與說明檔產生關聯。</span><span class="sxs-lookup"><span data-stu-id="06830-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="06830-135">相反地，Windows PowerShell 會搜尋模組目錄的 UI 文化特性特定子目錄，以取得以 XML 為基礎的說明檔，並在所有檔案中尋找腳本工作流程的說明。</span><span class="sxs-lookup"><span data-stu-id="06830-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="06830-136">已忽略 `.ExternalHelp` comment 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="06830-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="06830-137">由於會忽略 `.ExternalHelp` comment 關鍵字，因此 `Get-Help` Cmdlet 只有在模組中包含腳本工作流程時，才可以找到其說明。</span><span class="sxs-lookup"><span data-stu-id="06830-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>