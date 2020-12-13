---
ms.date: 09/13/2016
ms.topic: reference
title: 如何宣告 Cmdlet 參數
description: 如何宣告 Cmdlet 參數
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667091"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="65f22-103">如何宣告 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="65f22-103">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="65f22-104">這些範例示範如何宣告指名的、位置、必要、選擇性和切換參數。</span><span class="sxs-lookup"><span data-stu-id="65f22-104">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="65f22-105">這些範例也會示範如何定義參數別名。</span><span class="sxs-lookup"><span data-stu-id="65f22-105">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="65f22-106">如何宣告具名引數</span><span class="sxs-lookup"><span data-stu-id="65f22-106">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="65f22-107">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="65f22-107">Define a public property as shown in the following code.</span></span> <span data-ttu-id="65f22-108">當您加入參數屬性時，請省略 `Position` 屬性中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="65f22-108">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="65f22-109">如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="65f22-109">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="65f22-110">如何宣告位置參數</span><span class="sxs-lookup"><span data-stu-id="65f22-110">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="65f22-111">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="65f22-111">Define a public property as shown in the following code.</span></span> <span data-ttu-id="65f22-112">當您加入參數屬性時，請將 `Position` 關鍵字設定為引數位置。</span><span class="sxs-lookup"><span data-stu-id="65f22-112">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="65f22-113">值為0表示第一個位置。</span><span class="sxs-lookup"><span data-stu-id="65f22-113">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="65f22-114">如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="65f22-114">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="65f22-115">如何宣告強制參數</span><span class="sxs-lookup"><span data-stu-id="65f22-115">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="65f22-116">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="65f22-116">Define a public property as shown in the following code.</span></span> <span data-ttu-id="65f22-117">當您加入參數屬性時，請將 `Mandatory` 關鍵字設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="65f22-117">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="65f22-118">如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="65f22-118">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="65f22-119">如何宣告選擇性參數</span><span class="sxs-lookup"><span data-stu-id="65f22-119">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="65f22-120">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="65f22-120">Define a public property as shown in the following code.</span></span> <span data-ttu-id="65f22-121">當您加入參數屬性時，請省略 `Mandatory` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="65f22-121">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="65f22-122">如何宣告切換參數</span><span class="sxs-lookup"><span data-stu-id="65f22-122">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="65f22-123">將公用屬性定義為 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，然後宣告參數屬性。</span><span class="sxs-lookup"><span data-stu-id="65f22-123">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="65f22-124">如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="65f22-124">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="65f22-125">如何使用別名宣告參數</span><span class="sxs-lookup"><span data-stu-id="65f22-125">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="65f22-126">定義公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="65f22-126">Define a public property as shown in the following code.</span></span> <span data-ttu-id="65f22-127">新增可列出參數別名的別名屬性。</span><span class="sxs-lookup"><span data-stu-id="65f22-127">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="65f22-128">在此範例中，會針對相同參數定義三個別名。</span><span class="sxs-lookup"><span data-stu-id="65f22-128">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="65f22-129">第一個別名提供快捷方式。</span><span class="sxs-lookup"><span data-stu-id="65f22-129">The first alias provides a shortcut.</span></span> <span data-ttu-id="65f22-130">第二個和第三個別名提供可在不同案例中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="65f22-130">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="65f22-131">如需別名屬性的詳細資訊，請參閱 [別名屬性聲明](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="65f22-131">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65f22-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f22-132">See Also</span></span>

[<span data-ttu-id="65f22-133">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="65f22-133">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="65f22-134">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="65f22-134">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="65f22-135">別名屬性宣告</span><span class="sxs-lookup"><span data-stu-id="65f22-135">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="65f22-136">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="65f22-136">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
