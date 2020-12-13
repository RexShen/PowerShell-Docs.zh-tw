---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 別名
description: Cmdlet 別名
ms.openlocfilehash: 734553a9911aef256df563afa6abcdb23d7a62e6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660796"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="ffced-103">Cmdlet 別名</span><span class="sxs-lookup"><span data-stu-id="ffced-103">Cmdlet Aliases</span></span>

<span data-ttu-id="ffced-104">您可以使用 Cmdlet 別名來改善 Cmdlet 使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="ffced-104">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="ffced-105">您可以將別名新增到常用的 Cmdlet 來減少輸入，並讓您更輕鬆地快速完成工作。</span><span class="sxs-lookup"><span data-stu-id="ffced-105">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="ffced-106">您可以在 Cmdlet 中包含內建的別名，或是使用者可以定義自己的自訂別名。</span><span class="sxs-lookup"><span data-stu-id="ffced-106">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="ffced-107">例如， [Get 命令](/powershell/module/microsoft.powershell.core/get-command) Cmdlet 有內建的 `gcm` 別名。</span><span class="sxs-lookup"><span data-stu-id="ffced-107">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="ffced-108">您也可以使用別名來新增其他語言的命令名稱，讓使用者不需要學習新的命令。</span><span class="sxs-lookup"><span data-stu-id="ffced-108">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="ffced-109">別名指導方針</span><span class="sxs-lookup"><span data-stu-id="ffced-109">Alias Guidelines</span></span>

<span data-ttu-id="ffced-110">當您建立 Cmdlet 的內建別名時，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="ffced-110">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="ffced-111">指派別名之前，請先開始 Windows PowerShell，然後執行「 [取得別名](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) 」 Cmdlet 以查看已使用的別名。</span><span class="sxs-lookup"><span data-stu-id="ffced-111">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="ffced-112">包含別名前置詞，其參考 Cmdlet 名稱的動詞，以及參考 Cmdlet 名稱名詞的別名尾碼。</span><span class="sxs-lookup"><span data-stu-id="ffced-112">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="ffced-113">例如，Cmdlet 的別名是「 `Import-Module` ipmo」。</span><span class="sxs-lookup"><span data-stu-id="ffced-113">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="ffced-114">如需所有動詞及其別名的清單，請參閱 [Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)命令。</span><span class="sxs-lookup"><span data-stu-id="ffced-114">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="ffced-115">針對具有相同動詞的 Cmdlet，請包含相同的別名前置詞。</span><span class="sxs-lookup"><span data-stu-id="ffced-115">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="ffced-116">例如，在其名稱中有 "Get" 動詞的所有 Windows PowerShell Cmdlet 的別名會使用 "g" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="ffced-116">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="ffced-117">若為具有相同名詞的 Cmdlet，請包含相同的別名尾碼。</span><span class="sxs-lookup"><span data-stu-id="ffced-117">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="ffced-118">例如，其名稱中有 "Session" 名詞的所有 Windows PowerShell Cmdlet 的別名會使用 "sn" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="ffced-118">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="ffced-119">針對相當於其他語言命令的 Cmdlet，請使用命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffced-119">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="ffced-120">一般情況下，請盡可能縮短別名。</span><span class="sxs-lookup"><span data-stu-id="ffced-120">In general, make aliases as short as possible.</span></span> <span data-ttu-id="ffced-121">請確定別名至少有一個用於動詞的相異字元和一個不同的名詞字元。</span><span class="sxs-lookup"><span data-stu-id="ffced-121">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="ffced-122">視需要新增更多字元，使別名成為唯一的。</span><span class="sxs-lookup"><span data-stu-id="ffced-122">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffced-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffced-123">See Also</span></span>

[<span data-ttu-id="ffced-124">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ffced-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
