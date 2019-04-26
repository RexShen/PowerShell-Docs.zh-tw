---
title: Cmdlet 類別宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068635"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="b824d-102">Cmdlet 類別宣告</span><span class="sxs-lookup"><span data-stu-id="b824d-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="b824d-103">Microsoft.NET Framework 類別，會藉由指定宣告為 cmdlet **Cmdlet**做為中繼資料類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="b824d-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="b824d-104">( **Cmdlet**屬性是唯一的必要的屬性，針對所有的 cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="b824d-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="b824d-105">當您指定**Cmdlet**屬性，您必須指定可識別使用者 cmdlet 動詞和名詞 」 組。</span><span class="sxs-lookup"><span data-stu-id="b824d-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="b824d-106">而且，您必須描述 cmdlet 支援 Windows PowerShell 功能。</span><span class="sxs-lookup"><span data-stu-id="b824d-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="b824d-107">如需有關用來指定的宣告語法**Cmdlet**屬性，請參閱[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b824d-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b824d-108">**Cmdlet**屬性由定義[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="b824d-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="b824d-109">此類別的屬性對應到宣告屬性時所使用的宣告參數。</span><span class="sxs-lookup"><span data-stu-id="b824d-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="b824d-110">名詞</span><span class="sxs-lookup"><span data-stu-id="b824d-110">Nouns</span></span>

<span data-ttu-id="b824d-111">Cmdlet 名詞會指定此 cmdlet 所處理的資源。</span><span class="sxs-lookup"><span data-stu-id="b824d-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="b824d-112">名詞會區分您的 cmdlet 與其他 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b824d-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="b824d-113">Cmdlet 名稱中的名詞必須是特有的而且在一般的名詞，例如*server*，建議您最好將簡短的前置詞不同之處來自其他類似的資源的資源。</span><span class="sxs-lookup"><span data-stu-id="b824d-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="b824d-114">例如，包含具有前置詞的名詞的 cmdlet 名稱是`Get-SQLServer`。</span><span class="sxs-lookup"><span data-stu-id="b824d-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="b824d-115">一個特定名詞與更多一般動詞命令的組合可讓使用者快速找出其動作的 cmdlet，然後依其資源識別指令程式，同時還能避免不必要的 cmdlet 名稱重複。</span><span class="sxs-lookup"><span data-stu-id="b824d-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="b824d-116">如需不使用 cmdlet 名稱中的特殊字元的清單，請參閱 <<c0> [ 所需的開發指導方針](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="b824d-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="b824d-117">動詞</span><span class="sxs-lookup"><span data-stu-id="b824d-117">Verbs</span></span>

<span data-ttu-id="b824d-118">當您指定的動詞命令時，開發指導方針會要求您使用其中一個預先定義 Windows PowerShell 所提供的指令動詞。</span><span class="sxs-lookup"><span data-stu-id="b824d-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="b824d-119">藉由使用其中一個這些預先定義的指令動詞，您可確保您所撰寫的 cmdlet 與 cmdlet 所撰寫，由 Microsoft 和其他項目之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="b824d-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="b824d-120">例如，"Get"動詞命令用於擷取資料的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b824d-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="b824d-121">如需詳細的指導方針的動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="b824d-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="b824d-122">如需不使用 cmdlet 名稱中的特殊字元的清單，請參閱 <<c0> [ 所需的開發指導方針](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="b824d-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="b824d-123">支援的 Windows PowerShell 功能</span><span class="sxs-lookup"><span data-stu-id="b824d-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="b824d-124">**Cmdlet**屬性也可讓您指定您的指令程式支援的一些常見功能所提供的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b824d-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="b824d-125">這包括支援常見的功能，例如使用者意見反應確認 （又稱為 ShouldProcess 功能的支援） 和交易支援。</span><span class="sxs-lookup"><span data-stu-id="b824d-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="b824d-126">（交易的支援是在 Windows PowerShell 2.0 中推出）。</span><span class="sxs-lookup"><span data-stu-id="b824d-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="b824d-127">如需有關用來指定的宣告語法**Cmdlet**屬性，請參閱[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="b824d-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="b824d-128">Cmdlet 類別定義</span><span class="sxs-lookup"><span data-stu-id="b824d-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="b824d-129">下列程式碼是 GetProc cmdlet 類別定義。</span><span class="sxs-lookup"><span data-stu-id="b824d-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="b824d-130">請注意，依照 pascal 命名法大小寫會使用與類別的名稱，包含動詞和名詞的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b824d-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="b824d-131">Pascal 命名法大小寫</span><span class="sxs-lookup"><span data-stu-id="b824d-131">Pascal Casing</span></span>

<span data-ttu-id="b824d-132">當您命名 cmdlet 時，使用 pascal 命名法大小寫。</span><span class="sxs-lookup"><span data-stu-id="b824d-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="b824d-133">例如，`Get-Item`和`Get-ItemProperty`cmdlet 顯示當您命名為 cmdlet 時，請使用大小寫的正確方式。</span><span class="sxs-lookup"><span data-stu-id="b824d-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="b824d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b824d-134">See Also</span></span>

[<span data-ttu-id="b824d-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="b824d-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="b824d-136">CmdletAttribute Declaration</span><span class="sxs-lookup"><span data-stu-id="b824d-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="b824d-137">Cmdlet 動詞名稱</span><span class="sxs-lookup"><span data-stu-id="b824d-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="b824d-138">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b824d-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b824d-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b824d-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
