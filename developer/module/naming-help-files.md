---
title: 命名的說明檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795346"
---
# <a name="naming-help-files"></a><span data-ttu-id="ed059-102">為說明檔案命名</span><span class="sxs-lookup"><span data-stu-id="ed059-102">Naming Help Files</span></span>

<span data-ttu-id="ed059-103">本主題說明如何以 XML 為基礎的說明檔命名以便[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help)指令程式可以找到它。</span><span class="sxs-lookup"><span data-stu-id="ed059-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="ed059-104">針對每個命令類型，不同的名稱需求。</span><span class="sxs-lookup"><span data-stu-id="ed059-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="ed059-105">指令程式說明檔</span><span class="sxs-lookup"><span data-stu-id="ed059-105">Cmdlet Help Files</span></span>

<span data-ttu-id="ed059-106">說明檔，以C#cmdlet 必須命名為 cmdlet 定義所在的組件。</span><span class="sxs-lookup"><span data-stu-id="ed059-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="ed059-107">使用下列的檔案名稱格式：</span><span class="sxs-lookup"><span data-stu-id="ed059-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ed059-108">即使在組件為巢狀的模組時，才需要的組件名稱格式。</span><span class="sxs-lookup"><span data-stu-id="ed059-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ed059-109">比方說， [Get-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Microsoft.PowerShell.Diagnostics.dll 組件中所定義的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ed059-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="ed059-110">`Get-Help` Cmdlet 會尋找說明主題`Get-WinEvent`只存在於 Microsoft.PowerShell.Diagnostics.dll help.xml 檔案，在模組目錄中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ed059-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="ed059-111">提供者的說明檔</span><span class="sxs-lookup"><span data-stu-id="ed059-111">Provider Help files</span></span>

<span data-ttu-id="ed059-112">定義提供者所在的組件名稱必須為 Windows PowerShell 提供者的說明檔。</span><span class="sxs-lookup"><span data-stu-id="ed059-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="ed059-113">使用下列的檔案名稱格式：</span><span class="sxs-lookup"><span data-stu-id="ed059-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ed059-114">即使在組件為巢狀的模組時，才需要的組件名稱格式。</span><span class="sxs-lookup"><span data-stu-id="ed059-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ed059-115">例如，憑證提供者會定義 Microsoft.PowerShell.Security.dll 組件中。</span><span class="sxs-lookup"><span data-stu-id="ed059-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="ed059-116">`Get-Help` Cmdlet 尋找說明主題的憑證提供者只存在於 Microsoft.PowerShell.Security.dll help.xml 檔案，在模組目錄中。</span><span class="sxs-lookup"><span data-stu-id="ed059-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="ed059-117">函式的說明檔</span><span class="sxs-lookup"><span data-stu-id="ed059-117">Function Help Files</span></span>

<span data-ttu-id="ed059-118">可以使用記錄函式[註解型說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)或 XML 說明檔案中所述。</span><span class="sxs-lookup"><span data-stu-id="ed059-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="ed059-119">當函式會記載在 XML 檔案時，此函式必須`.ExternalHelp`註解關聯的 XML 檔案中的函式的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ed059-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="ed059-120">否則， `Get-Help` cmdlet 找不到說明檔。</span><span class="sxs-lookup"><span data-stu-id="ed059-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="ed059-121">沒有名稱的函式的說明檔的技術需求。</span><span class="sxs-lookup"><span data-stu-id="ed059-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="ed059-122">不過，最佳的作法是在其中定義函式的指令碼模組的說明檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed059-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="ed059-123">例如，下列函式定義 MyModule.psm1 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ed059-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="ed059-124">CIM 命令的說明檔</span><span class="sxs-lookup"><span data-stu-id="ed059-124">CIM Command Help Files</span></span>

<span data-ttu-id="ed059-125">在其中定義 CIM 命令的 CDXML 檔案名稱必須為 CIM 命令的說明檔。</span><span class="sxs-lookup"><span data-stu-id="ed059-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="ed059-126">使用下列的檔案名稱格式：</span><span class="sxs-lookup"><span data-stu-id="ed059-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="ed059-127">CIM 命令可以包含做為巢狀模組的模組中的 CDXML 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="ed059-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="ed059-128">為函式的工作階段匯入 CIM 命令時，Windows PowerShell 會將新增`.ExternalHelp`定義 CIM 命令的 CDXML 檔案命名為關聯的 XML 說明中的函式的函式定義的關鍵字檔案的註解。</span><span class="sxs-lookup"><span data-stu-id="ed059-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="ed059-129">指令碼工作流程說明檔</span><span class="sxs-lookup"><span data-stu-id="ed059-129">Script Workflow Help Files</span></span>

<span data-ttu-id="ed059-130">在模組中包含的指令碼工作流程可以記錄以 XML 為基礎的說明檔案中。</span><span class="sxs-lookup"><span data-stu-id="ed059-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="ed059-131">沒有名稱的說明檔的技術需求。</span><span class="sxs-lookup"><span data-stu-id="ed059-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="ed059-132">不過，最佳的作法是在其中定義指令碼工作流程的指令碼模組的說明檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed059-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="ed059-133">例如：</span><span class="sxs-lookup"><span data-stu-id="ed059-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="ed059-134">不需要其他指令碼與命令不同，指令碼工作流程`.ExternalHelp`註解將關聯的說明檔的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ed059-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="ed059-135">相反地，Windows PowerShell 搜尋 XML 為基礎的說明檔的模組目錄的 UI 文化特性專屬子目錄，並尋找指令碼中的工作流程的所有檔案的說明。</span><span class="sxs-lookup"><span data-stu-id="ed059-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="ed059-136">`.ExternalHelp` 註解的關鍵字會被忽略。</span><span class="sxs-lookup"><span data-stu-id="ed059-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="ed059-137">因為`.ExternalHelp`註解的關鍵字會被忽略，`Get-Help`指令程式可以尋找說明指令碼工作流程可以包含在模組時，才。</span><span class="sxs-lookup"><span data-stu-id="ed059-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>