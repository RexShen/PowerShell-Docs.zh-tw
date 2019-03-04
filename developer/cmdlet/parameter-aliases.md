---
title: 參數別名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853314"
---
# <a name="parameter-aliases"></a><span data-ttu-id="45e98-102">參數別名</span><span class="sxs-lookup"><span data-stu-id="45e98-102">Parameter Aliases</span></span>

<span data-ttu-id="45e98-103">Cmdlet 參數也可以有別名。</span><span class="sxs-lookup"><span data-stu-id="45e98-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="45e98-104">當您輸入，或在命令中指定的參數，您可以使用別名而不是參數名稱。</span><span class="sxs-lookup"><span data-stu-id="45e98-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="45e98-105">使用別名的優點</span><span class="sxs-lookup"><span data-stu-id="45e98-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="45e98-106">將別名加入至參數提供下列優點。</span><span class="sxs-lookup"><span data-stu-id="45e98-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="45e98-107">您可以提供捷徑，讓使用者不必呼叫此指令程式時，請使用完整的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="45e98-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="45e98-108">例如，您可以使用"CN"別名，而不是參數名稱的電腦 「 名稱 」。</span><span class="sxs-lookup"><span data-stu-id="45e98-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="45e98-109">如果您想要提供不同的名稱相同的參數，您可以定義多個別名。</span><span class="sxs-lookup"><span data-stu-id="45e98-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="45e98-110">您可以定義多個別名，如果您必須使用不同的方式參考相同資料的多個使用者群組。</span><span class="sxs-lookup"><span data-stu-id="45e98-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="45e98-111">您可以提供回溯相容性的現有指令碼參數的名稱變更時。</span><span class="sxs-lookup"><span data-stu-id="45e98-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="45e98-112">藉由使用別名屬性，以及 ValueFromPipelineByName 屬性，您可以定義使用參數，讓您將繫結至不同的物件類型的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45e98-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="45e98-113">例如，假設您有兩個不同類型的物件和第一個物件擁有寫入器屬性，第二個物件擁有編輯器屬性。</span><span class="sxs-lookup"><span data-stu-id="45e98-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="45e98-114">如果您的 cmdlet 的參數，必須接受管線輸入屬性名稱的寫入器和編輯器的別名和 cmdlet，cmdlet 可以將繫結至這兩種使用兩個參數別名的物件。</span><span class="sxs-lookup"><span data-stu-id="45e98-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="45e98-115">如需有關可以搭配特定參數的別名的詳細資訊，請參閱[常見的參數名稱](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="45e98-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="45e98-116">定義參數別名</span><span class="sxs-lookup"><span data-stu-id="45e98-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="45e98-117">若要定義參數的別名，宣告別名屬性，如下列的參數宣告中所示。</span><span class="sxs-lookup"><span data-stu-id="45e98-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="45e98-118">在此範例中，針對相同的參數定義多個別名。</span><span class="sxs-lookup"><span data-stu-id="45e98-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="45e98-119">(如需詳細資訊，請參閱 <<c0> [ 如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。)</span><span class="sxs-lookup"><span data-stu-id="45e98-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="45e98-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45e98-120">See Also</span></span>

[<span data-ttu-id="45e98-121">常見的參數名稱</span><span class="sxs-lookup"><span data-stu-id="45e98-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="45e98-122">如何宣告 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="45e98-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="45e98-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="45e98-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
