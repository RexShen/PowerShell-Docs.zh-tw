---
title: Cmdlet 別名 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fed4055f09e01c5f3fa87584d48551918606f4eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784532"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="d868d-102">Cmdlet 別名</span><span class="sxs-lookup"><span data-stu-id="d868d-102">Cmdlet Aliases</span></span>

<span data-ttu-id="d868d-103">您可以使用 Cmdlet 別名來改善 Cmdlet 的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="d868d-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="d868d-104">您可以將別名新增至常用的 Cmdlet 以減少輸入，並可讓您更輕鬆地快速完成工作。</span><span class="sxs-lookup"><span data-stu-id="d868d-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="d868d-105">您可以在 Cmdlet 中包含內建別名，或使用者可以定義自己的自訂別名。</span><span class="sxs-lookup"><span data-stu-id="d868d-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="d868d-106">例如， [Get-Command](/powershell/module/microsoft.powershell.core/get-command) Cmdlet 具有內建的 `gcm` 別名。</span><span class="sxs-lookup"><span data-stu-id="d868d-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="d868d-107">您也可以使用別名來新增其他語言的命令名稱，讓使用者不必學習新的命令。</span><span class="sxs-lookup"><span data-stu-id="d868d-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="d868d-108">別名指導方針</span><span class="sxs-lookup"><span data-stu-id="d868d-108">Alias Guidelines</span></span>

<span data-ttu-id="d868d-109">當您建立 Cmdlet 的內建別名時，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="d868d-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="d868d-110">指派別名之前，請先啟動 Windows PowerShell，然後執行[取得別名](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias)Cmdlet，以查看已經使用的別名。</span><span class="sxs-lookup"><span data-stu-id="d868d-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="d868d-111">包含別名前置詞，此首碼會參考 Cmdlet 名稱的動詞，以及參考 Cmdlet 名稱名詞的別名尾碼。</span><span class="sxs-lookup"><span data-stu-id="d868d-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="d868d-112">例如，Cmdlet 的別名是「 `Import-Module` ipmo」。</span><span class="sxs-lookup"><span data-stu-id="d868d-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="d868d-113">如需所有動詞和其別名的清單，請參閱[Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="d868d-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="d868d-114">對於具有相同動詞的 Cmdlet，請包含相同的別名前置詞。</span><span class="sxs-lookup"><span data-stu-id="d868d-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="d868d-115">例如，名稱中含有 "Get" 動詞的所有 Windows PowerShell Cmdlet 的別名都會使用 "g" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="d868d-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="d868d-116">對於具有相同名詞的 Cmdlet，請包含相同的別名尾碼。</span><span class="sxs-lookup"><span data-stu-id="d868d-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="d868d-117">例如，名稱中包含 "Session" 名詞的所有 Windows PowerShell Cmdlet 的別名都會使用 "sn.exe" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="d868d-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="d868d-118">對於相當於其他語言之命令的 Cmdlet，請使用命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="d868d-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="d868d-119">一般來說，請儘量縮短別名。</span><span class="sxs-lookup"><span data-stu-id="d868d-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="d868d-120">請確定別名至少有一個用於動詞的相異字元，以及一個代表名詞的相異字元。</span><span class="sxs-lookup"><span data-stu-id="d868d-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="d868d-121">視需要新增更多字元，讓別名成為唯一的。</span><span class="sxs-lookup"><span data-stu-id="d868d-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="d868d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d868d-122">See Also</span></span>

[<span data-ttu-id="d868d-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d868d-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
