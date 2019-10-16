---
title: 如何宣告 Cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365677"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="e3365-102">如何宣告 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="e3365-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="e3365-103">這些範例示範如何宣告指名的、位置、必要、選擇性和切換參數。</span><span class="sxs-lookup"><span data-stu-id="e3365-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="e3365-104">這些範例也會示範如何定義參數別名。</span><span class="sxs-lookup"><span data-stu-id="e3365-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="e3365-105">如何宣告具名引數</span><span class="sxs-lookup"><span data-stu-id="e3365-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="e3365-106">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e3365-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e3365-107">當您新增參數屬性時，請省略屬性中的 `Position` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e3365-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e3365-108">如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="e3365-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="e3365-109">如何宣告位置參數</span><span class="sxs-lookup"><span data-stu-id="e3365-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="e3365-110">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e3365-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e3365-111">當您新增參數屬性時，請將 `Position` 關鍵字設定為引數位置。</span><span class="sxs-lookup"><span data-stu-id="e3365-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="e3365-112">值為0表示第一個位置。</span><span class="sxs-lookup"><span data-stu-id="e3365-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e3365-113">如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="e3365-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="e3365-114">如何宣告強制參數</span><span class="sxs-lookup"><span data-stu-id="e3365-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="e3365-115">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e3365-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e3365-116">當您新增參數屬性時，請將 `Mandatory` 關鍵字設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e3365-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e3365-117">如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="e3365-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="e3365-118">如何宣告選擇性參數</span><span class="sxs-lookup"><span data-stu-id="e3365-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="e3365-119">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e3365-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e3365-120">當您新增參數屬性時，請省略 `Mandatory` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e3365-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="e3365-121">如何宣告切換參數</span><span class="sxs-lookup"><span data-stu-id="e3365-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="e3365-122">將公用屬性定義為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，然後宣告參數屬性。</span><span class="sxs-lookup"><span data-stu-id="e3365-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="e3365-123">如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="e3365-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="e3365-124">如何宣告具有別名的參數</span><span class="sxs-lookup"><span data-stu-id="e3365-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="e3365-125">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e3365-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e3365-126">新增別名屬性，其中列出參數的別名。</span><span class="sxs-lookup"><span data-stu-id="e3365-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="e3365-127">在此範例中，會為相同的參數定義三個別名。</span><span class="sxs-lookup"><span data-stu-id="e3365-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="e3365-128">第一個別名提供快捷方式。</span><span class="sxs-lookup"><span data-stu-id="e3365-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="e3365-129">第二個和第三個別名提供可用於不同案例的名稱。</span><span class="sxs-lookup"><span data-stu-id="e3365-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="e3365-130">如需 Alias 屬性的詳細資訊，請參閱[Alias 屬性](./alias-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="e3365-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3365-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3365-131">See Also</span></span>

[<span data-ttu-id="e3365-132">SwitchParameter。</span><span class="sxs-lookup"><span data-stu-id="e3365-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="e3365-133">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="e3365-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="e3365-134">Alias 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="e3365-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="e3365-135">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e3365-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
