---
ms.date: 09/12/2016
ms.topic: reference
title: 為說明檔案命名
description: 為說明檔案命名
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667584"
---
# <a name="naming-help-files"></a><span data-ttu-id="74af5-103">為說明檔案命名</span><span class="sxs-lookup"><span data-stu-id="74af5-103">Naming Help Files</span></span>

<span data-ttu-id="74af5-104">本主題說明如何命名以 XML 為基礎的說明檔，讓 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 可以找到它。</span><span class="sxs-lookup"><span data-stu-id="74af5-104">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="74af5-105">每個命令類型的名稱需求各不相同。</span><span class="sxs-lookup"><span data-stu-id="74af5-105">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="74af5-106">Cmdlet 說明檔</span><span class="sxs-lookup"><span data-stu-id="74af5-106">Cmdlet Help Files</span></span>

<span data-ttu-id="74af5-107">C # Cmdlet 的說明檔必須針對已定義 Cmdlet 的元件命名。</span><span class="sxs-lookup"><span data-stu-id="74af5-107">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="74af5-108">使用下列檔案名格式：</span><span class="sxs-lookup"><span data-stu-id="74af5-108">Use the following filename format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="74af5-109">即使元件是嵌套模組，也需要元件名稱格式。</span><span class="sxs-lookup"><span data-stu-id="74af5-109">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="74af5-110">例如， [new-winevent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) 指令程式是在 Microsoft.PowerShell.Diagnostics.dll 元件中定義。</span><span class="sxs-lookup"><span data-stu-id="74af5-110">For example, the [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="74af5-111">此 `Get-Help` Cmdlet `Get-WinEvent` 只會在模組目錄的檔案中尋找 Cmdlet 的說明主題 `Microsoft.PowerShell.Diagnostics.dll-help.xml` 。</span><span class="sxs-lookup"><span data-stu-id="74af5-111">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the `Microsoft.PowerShell.Diagnostics.dll-help.xml` file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="74af5-112">提供者說明檔</span><span class="sxs-lookup"><span data-stu-id="74af5-112">Provider Help files</span></span>

<span data-ttu-id="74af5-113">PowerShell 提供者的說明檔必須針對定義提供者的元件進行命名。</span><span class="sxs-lookup"><span data-stu-id="74af5-113">The help file for a PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="74af5-114">使用下列檔案名格式：</span><span class="sxs-lookup"><span data-stu-id="74af5-114">Use the following filename format:</span></span>

`<AssemblyName>.dll-help.xml`

<span data-ttu-id="74af5-115">即使元件是嵌套模組，也需要元件名稱格式。</span><span class="sxs-lookup"><span data-stu-id="74af5-115">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="74af5-116">例如，憑證提供者是在元件中定義 `Microsoft.PowerShell.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="74af5-116">For example, the Certificate provider is defined in the `Microsoft.PowerShell.Security.dll` assembly.</span></span> <span data-ttu-id="74af5-117">此 `Get-Help` Cmdlet 只會在模組目錄的檔案中尋找憑證提供者的說明主題 `Microsoft.PowerShell.Security.dll-help.xml` 。</span><span class="sxs-lookup"><span data-stu-id="74af5-117">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the `Microsoft.PowerShell.Security.dll-help.xml` file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="74af5-118">函數說明檔</span><span class="sxs-lookup"><span data-stu-id="74af5-118">Function Help Files</span></span>

<span data-ttu-id="74af5-119">您可以使用以 [批註為基礎的說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 或 XML 說明檔中記載的功能來記錄函式。</span><span class="sxs-lookup"><span data-stu-id="74af5-119">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="74af5-120">當函式記載于 XML 檔案時，函式必須有 `.ExternalHelp` 批註關鍵字，才能將函式與 xml 檔案產生關聯。</span><span class="sxs-lookup"><span data-stu-id="74af5-120">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="74af5-121">否則，此 Cmdlet 找不到說明檔 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="74af5-121">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="74af5-122">函數說明檔的名稱沒有任何技術需求。</span><span class="sxs-lookup"><span data-stu-id="74af5-122">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="74af5-123">不過，最佳作法是為定義函數的腳本模組命名說明檔。</span><span class="sxs-lookup"><span data-stu-id="74af5-123">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="74af5-124">例如，在檔案中定義了下列函數 `MyModule.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="74af5-124">For example, the following function is defined in the `MyModule.psm1` file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="74af5-125">CIM 命令說明檔</span><span class="sxs-lookup"><span data-stu-id="74af5-125">CIM Command Help Files</span></span>

<span data-ttu-id="74af5-126">CIM 命令的說明檔必須針對已定義 CIM 命令的 CDXML 檔案命名。</span><span class="sxs-lookup"><span data-stu-id="74af5-126">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="74af5-127">使用下列檔案名格式：</span><span class="sxs-lookup"><span data-stu-id="74af5-127">Use the following filename format:</span></span>

`<FileName>.cdxml-help.xml`

<span data-ttu-id="74af5-128">CIM 命令會定義在可包含在模組中做為嵌套模組的 CDXML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="74af5-128">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="74af5-129">當 CIM 命令以函式的形式匯入會話時，PowerShell 會將 `.ExternalHelp` comment 關鍵字加入至函式定義，此定義會將函式與 XML 說明檔建立關聯，該檔案是針對定義 CIM 命令的 CDXML 檔案命名。</span><span class="sxs-lookup"><span data-stu-id="74af5-129">When the CIM command is imported into the session as a function, PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="74af5-130">編寫工作流程說明檔的腳本</span><span class="sxs-lookup"><span data-stu-id="74af5-130">Script Workflow Help Files</span></span>

<span data-ttu-id="74af5-131">模組中所包含的腳本工作流程可以記錄在以 XML 為基礎的說明檔中。</span><span class="sxs-lookup"><span data-stu-id="74af5-131">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="74af5-132">說明檔的名稱沒有技術需求。</span><span class="sxs-lookup"><span data-stu-id="74af5-132">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="74af5-133">不過，最佳作法是為腳本模組命名定義腳本工作流程的說明檔。</span><span class="sxs-lookup"><span data-stu-id="74af5-133">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="74af5-134">例如：</span><span class="sxs-lookup"><span data-stu-id="74af5-134">For example:</span></span>

`<ScriptModule>.psm1-help.xml`

<span data-ttu-id="74af5-135">不同于其他已編寫腳本的命令，腳本工作流程不需要 `.ExternalHelp` comment 關鍵字，就可以將它們與說明檔產生關聯。</span><span class="sxs-lookup"><span data-stu-id="74af5-135">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="74af5-136">相反地，PowerShell 會在模組目錄的 UI 文化特性特定子目錄中搜尋 XML 的說明檔，並在所有檔案中尋找腳本工作流程的說明。</span><span class="sxs-lookup"><span data-stu-id="74af5-136">Instead, PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="74af5-137">`.ExternalHelp` 忽略批註關鍵字。</span><span class="sxs-lookup"><span data-stu-id="74af5-137">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="74af5-138">因為 `.ExternalHelp` 會忽略 comment 關鍵字，所以 `Get-Help` 只有當腳本包含在模組中時，Cmdlet 才可以找到腳本工作流程的說明。</span><span class="sxs-lookup"><span data-stu-id="74af5-138">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
