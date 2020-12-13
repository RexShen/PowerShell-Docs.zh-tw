---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell Cmdlet 概念
description: Windows PowerShell Cmdlet 概念
ms.openlocfilehash: da34d3d229f6d57ee22d84fc024b31eb2ee27ba3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652532"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="76b20-103">Windows PowerShell Cmdlet 概念</span><span class="sxs-lookup"><span data-stu-id="76b20-103">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="76b20-104">本節說明 Cmdlet 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="76b20-104">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="76b20-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="76b20-105">In This Section</span></span>

<span data-ttu-id="76b20-106">本節包含下列主題。</span><span class="sxs-lookup"><span data-stu-id="76b20-106">This section includes the following topics.</span></span>

<span data-ttu-id="76b20-107">[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md) 本主題提供開發指導方針，可用來產生格式正確的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76b20-107">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="76b20-108">[Cmdlet 類別](./cmdlet-class-declaration.md) 宣告本主題說明 Cmdlet 類別宣告。</span><span class="sxs-lookup"><span data-stu-id="76b20-108">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="76b20-109">[Windows PowerShell 命令的已核准動詞](./approved-verbs-for-windows-powershell-commands.md) 本主題列出您可以在宣告 Cmdlet 類別時使用的預先定義 Cmdlet 動詞。</span><span class="sxs-lookup"><span data-stu-id="76b20-109">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="76b20-110">[Cmdlet 輸入處理方法](./cmdlet-input-processing-methods.md) 本主題說明可讓 Cmdlet 執行前置處理作業、輸入處理作業，以及後置處理作業的方法。</span><span class="sxs-lookup"><span data-stu-id="76b20-110">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="76b20-111">[Cmdlet 參數](./cmdlet-parameters.md) 本節說明您可以新增至 Cmdlet 的不同參數類型。</span><span class="sxs-lookup"><span data-stu-id="76b20-111">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="76b20-112">[Cmdlet 屬性](./cmdlet-attributes.md) 本節說明用來將 .NET Framework 類別宣告為 Cmdlet、將欄位宣告為 Cmdlet 參數，以及宣告參數之輸入驗證規則的屬性。</span><span class="sxs-lookup"><span data-stu-id="76b20-112">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="76b20-113">[Cmdlet 別名](./cmdlet-aliases.md) 本主題說明 Cmdlet 別名。</span><span class="sxs-lookup"><span data-stu-id="76b20-113">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="76b20-114">[Cmdlet 輸出](./cmdlet-output.md) 本節說明 Cmdlet 可以傳回的輸出類型，以及如何定義和顯示 Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="76b20-114">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="76b20-115">[註冊 Cmdlet](./modules-and-snap-ins.md) 本節說明如何使用模組和嵌入式管理單元來註冊 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76b20-115">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="76b20-116">[要求確認](./requesting-confirmation-from-cmdlets.md) 本節說明如何在對系統進行變更之前，先向使用者要求確認。</span><span class="sxs-lookup"><span data-stu-id="76b20-116">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="76b20-117">[Windows PowerShell 錯誤報表](./error-reporting-concepts.md) 本節說明 Cmdlet 如何報告終止錯誤和非終止錯誤，並說明如何解讀錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="76b20-117">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="76b20-118">[背景作業](./background-jobs.md) 本主題說明 Cmdlet 如何在背景工作中執行其工作，而不會干擾目前會話中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="76b20-118">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="76b20-119">[在 Cmdlet 中叫用 Cmdlet 和腳本](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) 本主題說明 Cmdlet 如何從其輸入處理方法中叫用其他 Cmdlet 和腳本。</span><span class="sxs-lookup"><span data-stu-id="76b20-119">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="76b20-120">[Cmdlet 集合](./cmdlet-sets.md) 本主題說明如何使用基類來建立一組 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76b20-120">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="76b20-121">[Windows PowerShell 會話狀態](./windows-powershell-session-state.md) 本主題說明 Windows PowerShell 的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="76b20-121">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
