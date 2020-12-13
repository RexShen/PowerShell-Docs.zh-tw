---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 類別宣告
description: Cmdlet 類別宣告
ms.openlocfilehash: 854b0a4ca9f6c87c4fad3b71ee726beade585e02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653492"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="f2330-103">Cmdlet 類別宣告</span><span class="sxs-lookup"><span data-stu-id="f2330-103">Cmdlet Class Declaration</span></span>

<span data-ttu-id="f2330-104">Microsoft .NET Framework 類別會將 **Cmdlet** 屬性指定為類別的中繼資料，以宣告為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2330-104">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="f2330-105"> (**Cmdlet** 屬性是) 的所有 Cmdlet 唯一必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2330-105">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span>
<span data-ttu-id="f2330-106">當您指定 **Cmdlet** 屬性時，您必須指定用來識別 Cmdlet 給使用者的動詞和名詞配對。</span><span class="sxs-lookup"><span data-stu-id="f2330-106">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="f2330-107">而且，您必須描述 Cmdlet 支援的 Windows PowerShell 功能。</span><span class="sxs-lookup"><span data-stu-id="f2330-107">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="f2330-108">如需用來指定 **Cmdlet** 屬性之宣告語法的詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f2330-108">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f2330-109">**Cmdlet** 屬性是由 [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="f2330-109">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="f2330-110">這個類別的屬性會對應至宣告屬性時所使用的宣告參數。</span><span class="sxs-lookup"><span data-stu-id="f2330-110">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="f2330-111">名詞</span><span class="sxs-lookup"><span data-stu-id="f2330-111">Nouns</span></span>

<span data-ttu-id="f2330-112">指令程式的名詞會指定 Cmdlet 作用的資源。</span><span class="sxs-lookup"><span data-stu-id="f2330-112">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="f2330-113">名詞會區分您的 Cmdlet 與其他 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2330-113">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="f2330-114">Cmdlet 名稱中的名詞必須是特定的，而且如果是一般名詞（例如 *伺服器*），最好新增簡短的前置詞，以區分您的資源與其他類似的資源。</span><span class="sxs-lookup"><span data-stu-id="f2330-114">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="f2330-115">例如，包含具有前置詞之名詞的 Cmdlet 名稱為 `Get-SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="f2330-115">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="f2330-116">具有更一般動詞的特定名片語合可讓使用者透過其動作快速找出 Cmdlet，然後依其資源識別 Cmdlet，同時避免不必要的 Cmdlet 名稱重複。</span><span class="sxs-lookup"><span data-stu-id="f2330-116">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="f2330-117">如需無法在 Cmdlet 名稱中使用的特殊字元清單，請參閱 [必要的開發指導方針](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="f2330-117">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="f2330-118">動詞</span><span class="sxs-lookup"><span data-stu-id="f2330-118">Verbs</span></span>

<span data-ttu-id="f2330-119">當您指定動詞時，開發指導方針會要求您使用 Windows PowerShell 所提供的其中一個預先定義動詞。</span><span class="sxs-lookup"><span data-stu-id="f2330-119">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="f2330-120">藉由使用其中一個預先定義的動詞，您將可確保您所撰寫的 Cmdlet 和由 Microsoft 和其他人撰寫的 Cmdlet 之間的一致性。</span><span class="sxs-lookup"><span data-stu-id="f2330-120">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="f2330-121">例如，"Get" 動詞命令會用於取出資料的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2330-121">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="f2330-122">如需動詞指導方針的詳細資訊，請參閱 [Cmdlet 動詞命令名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="f2330-122">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="f2330-123">如需無法在 Cmdlet 名稱中使用的特殊字元清單，請參閱 [必要的開發指導方針](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="f2330-123">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="f2330-124">支援 Windows PowerShell 功能</span><span class="sxs-lookup"><span data-stu-id="f2330-124">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="f2330-125">**Cmdlet** 屬性也可讓您指定 Cmdlet 支援 Windows PowerShell 所提供的一些常見功能。</span><span class="sxs-lookup"><span data-stu-id="f2330-125">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="f2330-126">這包括對一般功能的支援，例如使用者意見確認 (稱為 ShouldProcess 功能的支援) 和交易支援。</span><span class="sxs-lookup"><span data-stu-id="f2330-126">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="f2330-127">Windows PowerShell 2.0) 引進了 (的交易支援。</span><span class="sxs-lookup"><span data-stu-id="f2330-127">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="f2330-128">如需用來指定 **Cmdlet** 屬性之宣告語法的詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f2330-128">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="f2330-129">Cmdlet 類別定義</span><span class="sxs-lookup"><span data-stu-id="f2330-129">Cmdlet Class Definition</span></span>

<span data-ttu-id="f2330-130">下列程式碼是 GetProc Cmdlet 類別的定義。</span><span class="sxs-lookup"><span data-stu-id="f2330-130">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="f2330-131">請注意，會使用 Pascal 大小寫，而且類別的名稱包括 Cmdlet 的動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="f2330-131">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a><span data-ttu-id="f2330-132">Pascal 大小寫</span><span class="sxs-lookup"><span data-stu-id="f2330-132">Pascal Casing</span></span>

<span data-ttu-id="f2330-133">當您命名 Cmdlet 時，請使用 Pascal 大小寫。</span><span class="sxs-lookup"><span data-stu-id="f2330-133">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="f2330-134">例如， `Get-Item` `Get-ItemProperty` 當您命名 Cmdlet 時，和 Cmdlet 會顯示使用大寫的正確方式。</span><span class="sxs-lookup"><span data-stu-id="f2330-134">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2330-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2330-135">See Also</span></span>

[<span data-ttu-id="f2330-136">CmdletAttribute。</span><span class="sxs-lookup"><span data-stu-id="f2330-136">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="f2330-137">CmdletAttribute 宣告</span><span class="sxs-lookup"><span data-stu-id="f2330-137">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="f2330-138">Cmdlet 動詞名稱</span><span class="sxs-lookup"><span data-stu-id="f2330-138">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="f2330-139">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f2330-139">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="f2330-140">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f2330-140">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
