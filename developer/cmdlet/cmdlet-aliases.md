---
title: Cmdlet 別名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860504"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="ad536-102">Cmdlet 別名</span><span class="sxs-lookup"><span data-stu-id="ad536-102">Cmdlet Aliases</span></span>

<span data-ttu-id="ad536-103">您可以使用 cmdlet 別名來改善指令程式使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="ad536-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="ad536-104">您可以經常使用的 cmdlet，以減少輸入並讓您更輕鬆地完成工作快速新增別名。</span><span class="sxs-lookup"><span data-stu-id="ad536-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="ad536-105">您可以納入您的 cmdlet 中的內建的別名或使用者可以定義自己的自訂別名。</span><span class="sxs-lookup"><span data-stu-id="ad536-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="ad536-106">例如， [Get-command](/powershell/module/microsoft.powershell.core/get-command) cmdlet 具有內建`gcm`別名。</span><span class="sxs-lookup"><span data-stu-id="ad536-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="ad536-107">您也可以使用別名新增其他語言的命令名稱，以便使用者不需要學習新的命令。</span><span class="sxs-lookup"><span data-stu-id="ad536-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="ad536-108">別名的指導方針</span><span class="sxs-lookup"><span data-stu-id="ad536-108">Alias Guidelines</span></span>

<span data-ttu-id="ad536-109">當您建立您的 cmdlet 的內建的別名時，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="ad536-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="ad536-110">指派別名之前，啟動 Windows PowerShell，然後再執行[Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet 來查看已使用的別名。</span><span class="sxs-lookup"><span data-stu-id="ad536-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="ad536-111">包含參考的指令程式的名稱和名詞的 cmdlet 名稱所參考的別名後置詞的動詞命令的別名前置詞。</span><span class="sxs-lookup"><span data-stu-id="ad536-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="ad536-112">比方說，別名`Import-Module`cmdlet 是"ipmo"。</span><span class="sxs-lookup"><span data-stu-id="ad536-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="ad536-113">如需所有動詞命令和其別名的清單，請參閱 < [Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="ad536-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="ad536-114">針對具有相同的指令動詞的 cmdlet，包括相同的別名前置詞。</span><span class="sxs-lookup"><span data-stu-id="ad536-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="ad536-115">比方說，其名稱中含有"Get"動詞的所有 Windows PowerShell cmdlet 的別名會使用"g"前置詞。</span><span class="sxs-lookup"><span data-stu-id="ad536-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="ad536-116">針對具有相同名詞的 cmdlet，包含相同別名後置詞。</span><span class="sxs-lookup"><span data-stu-id="ad536-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="ad536-117">例如，具有其名稱中的 「 工作階段 」 名詞的所有 Windows PowerShell cmdlet 的別名會使用"sn"後置詞。</span><span class="sxs-lookup"><span data-stu-id="ad536-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="ad536-118">針對其他語言中的命令對等的 cmdlet，使用命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad536-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="ad536-119">一般情況下，請盡量縮短的別名。</span><span class="sxs-lookup"><span data-stu-id="ad536-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="ad536-120">請確定別名具有至少一個動詞命令的不同字元和一個為名詞的個別字元。</span><span class="sxs-lookup"><span data-stu-id="ad536-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="ad536-121">新增更多的字元，視需要使其成為唯一別名。</span><span class="sxs-lookup"><span data-stu-id="ad536-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad536-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad536-122">See Also</span></span>

[<span data-ttu-id="ad536-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad536-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
