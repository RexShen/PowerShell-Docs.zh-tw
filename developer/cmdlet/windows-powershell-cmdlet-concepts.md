---
title: Windows PowerShell Cmdlet 概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855784"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="4259a-102">Windows PowerShell Cmdlet 概念</span><span class="sxs-lookup"><span data-stu-id="4259a-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="4259a-103">本章節描述 cmdlet 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="4259a-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4259a-104">在本節中</span><span class="sxs-lookup"><span data-stu-id="4259a-104">In This Section</span></span>

<span data-ttu-id="4259a-105">本節包含下列主題。</span><span class="sxs-lookup"><span data-stu-id="4259a-105">This section includes the following topics.</span></span>

<span data-ttu-id="4259a-106">[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)本主題提供可用來產生格式正確的指令程式的開發指導方針。</span><span class="sxs-lookup"><span data-stu-id="4259a-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="4259a-107">[Cmdlet 類別宣告](./cmdlet-class-declaration.md)本主題說明 cmdlet 類別宣告。</span><span class="sxs-lookup"><span data-stu-id="4259a-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="4259a-108">[核准 Windows PowerShell 命令的指令動詞](./approved-verbs-for-windows-powershell-commands.md)本主題列出當您宣告 cmdlet 類別時，您可以使用的預先定義的 cmdlet 動詞命令。</span><span class="sxs-lookup"><span data-stu-id="4259a-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="4259a-109">[Cmdlet 的輸入處理方法](./cmdlet-input-processing-methods.md)本主題說明的方法，可讓 cmdlet 來執行前置處理的作業、 輸入處理作業，以及張貼處理作業。</span><span class="sxs-lookup"><span data-stu-id="4259a-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="4259a-110">[Cmdlet 參數](./cmdlet-parameters.md)本章節描述您可以將它新增至 cmdlet 的參數不同型別。</span><span class="sxs-lookup"><span data-stu-id="4259a-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="4259a-111">[Cmdlet 屬性](./cmdlet-attributes.md)本章節描述用來將.NET Framework 類別宣告為 cmdlet，宣告為 cmdlet 參數的欄位，並宣告參數的輸入的驗證規則的屬性。</span><span class="sxs-lookup"><span data-stu-id="4259a-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="4259a-112">[Cmdlet 別名](./cmdlet-aliases.md)本主題描述 cmdlet 的別名。</span><span class="sxs-lookup"><span data-stu-id="4259a-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="4259a-113">[Cmdlet 輸出](./cmdlet-output.md)本章節描述的指令程式可傳回的輸出，以及如何定義，並顯示由 cmdlet 所傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="4259a-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="4259a-114">[註冊 Cmdlet](./modules-and-snap-ins.md)本章節描述如何使用模組和嵌入式管理單元來註冊 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4259a-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="4259a-115">[要求確認](./requesting-confirmation-from-cmdlets.md)本章節描述如何 cmdlet 確認向使用者要求它們對系統進行變更之前。</span><span class="sxs-lookup"><span data-stu-id="4259a-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="4259a-116">[Windows PowerShell 錯誤報告](./error-reporting-concepts.md)本章節描述如何 cmdlet 會將報告的終止錯誤和非終止錯誤，並說明如何解譯錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="4259a-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="4259a-117">[背景工作](./background-jobs.md)本主題描述如何 cmdlet 可以執行其工作內不會干擾目前的工作階段中執行的命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="4259a-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="4259a-118">[叫用 Cmdlet 與 Cmdlet 中的指令碼](./invoking-cmdlets-and-scripts-within-a-cmdlet.md)本主題描述如何 cmdlet 可以叫用其他 cmdlet 和指令碼，從其輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="4259a-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="4259a-119">[Cmdlet 會設定](./cmdlet-sets.md)本主題描述如何使用基底類別來建立 cmdlet 的集合。</span><span class="sxs-lookup"><span data-stu-id="4259a-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="4259a-120">[Windows PowerShell 工作階段狀態](./windows-powershell-session-state.md)本主題描述 Windows PowerShell 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="4259a-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
