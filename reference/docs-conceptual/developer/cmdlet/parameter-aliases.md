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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369587"
---
# <a name="parameter-aliases"></a><span data-ttu-id="a6237-102">參數別名</span><span class="sxs-lookup"><span data-stu-id="a6237-102">Parameter Aliases</span></span>

<span data-ttu-id="a6237-103">Cmdlet 參數也可以有別名。</span><span class="sxs-lookup"><span data-stu-id="a6237-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="a6237-104">當您在命令中輸入或指定參數時，可以使用別名而非參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a6237-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="a6237-105">使用別名的優點</span><span class="sxs-lookup"><span data-stu-id="a6237-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="a6237-106">將別名新增至參數可提供下列優點。</span><span class="sxs-lookup"><span data-stu-id="a6237-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="a6237-107">您可以提供快捷方式，讓使用者在呼叫 Cmdlet 時不需要使用完整的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a6237-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="a6237-108">例如，您可以使用 "CN" 別名，而不是參數名稱 "ComputerName"。</span><span class="sxs-lookup"><span data-stu-id="a6237-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="a6237-109">如果您想要為相同的參數提供不同的名稱，可以定義多個別名。</span><span class="sxs-lookup"><span data-stu-id="a6237-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="a6237-110">如果您必須使用以不同方式參考相同資料的多個使用者群組，您可能會想要定義多個別名。</span><span class="sxs-lookup"><span data-stu-id="a6237-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="a6237-111">如果參數的名稱變更，您可以為現有的腳本提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="a6237-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="a6237-112">藉由使用 Alias 屬性和 ValueFromPipelineByName 屬性，您可以定義參數，讓您的 Cmdlet 系結至不同的物件類型。</span><span class="sxs-lookup"><span data-stu-id="a6237-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="a6237-113">例如，假設您有兩個不同類型的物件，而第一個物件具有寫入器屬性，而第二個物件具有 editor 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6237-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="a6237-114">如果您的 Cmdlet 具有具有寫入器和編輯器別名的參數，且 Cmdlet 接受以屬性名稱為基礎的管線輸入，則您的 Cmdlet 可以使用兩個參數別名系結至這兩個物件。</span><span class="sxs-lookup"><span data-stu-id="a6237-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="a6237-115">如需可搭配特定參數使用之別名的詳細資訊，請參閱[一般參數名稱](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="a6237-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="a6237-116">定義參數別名</span><span class="sxs-lookup"><span data-stu-id="a6237-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="a6237-117">若要定義參數的別名，請宣告 Alias 屬性，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="a6237-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="a6237-118">在此範例中，會為相同的參數定義多個別名。</span><span class="sxs-lookup"><span data-stu-id="a6237-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="a6237-119">（如需詳細資訊，請參閱 how[To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)）。</span><span class="sxs-lookup"><span data-stu-id="a6237-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a6237-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6237-120">See Also</span></span>

[<span data-ttu-id="a6237-121">一般參數名稱</span><span class="sxs-lookup"><span data-stu-id="a6237-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="a6237-122">如何宣告 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="a6237-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="a6237-123">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a6237-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
