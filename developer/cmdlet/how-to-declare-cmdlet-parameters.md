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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067906"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="df757-102">如何宣告 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="df757-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="df757-103">這些範例示範如何宣告具名、 位置、 必要、 選擇性的以及切換參數。</span><span class="sxs-lookup"><span data-stu-id="df757-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="df757-104">這些範例也顯示如何定義參數的別名。</span><span class="sxs-lookup"><span data-stu-id="df757-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="df757-105">如何宣告具名的參數</span><span class="sxs-lookup"><span data-stu-id="df757-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="df757-106">定義的公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="df757-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="df757-107">當您新增的參數屬性時，略過`Position`關鍵字的屬性。</span><span class="sxs-lookup"><span data-stu-id="df757-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="df757-108">如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="df757-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="df757-109">如何宣告位置參數</span><span class="sxs-lookup"><span data-stu-id="df757-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="df757-110">定義的公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="df757-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="df757-111">當您新增的參數屬性時，設定`Position`關鍵字引數位置。</span><span class="sxs-lookup"><span data-stu-id="df757-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="df757-112">值為 0 表示第一個位置。</span><span class="sxs-lookup"><span data-stu-id="df757-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="df757-113">如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="df757-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="df757-114">如何宣告的必要參數</span><span class="sxs-lookup"><span data-stu-id="df757-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="df757-115">定義的公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="df757-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="df757-116">當您新增的參數屬性時，設定`Mandatory`關鍵字來`true`。</span><span class="sxs-lookup"><span data-stu-id="df757-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="df757-117">如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="df757-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="df757-118">如何宣告選擇性參數</span><span class="sxs-lookup"><span data-stu-id="df757-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="df757-119">定義的公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="df757-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="df757-120">當您新增的參數屬性時，略過`Mandatory`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="df757-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="df757-121">如何宣告參數的參數</span><span class="sxs-lookup"><span data-stu-id="df757-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="df757-122">定義的公用屬性，為型別[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)，然後將宣告參數屬性。</span><span class="sxs-lookup"><span data-stu-id="df757-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="df757-123">如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="df757-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="df757-124">如何宣告具有別名的參數</span><span class="sxs-lookup"><span data-stu-id="df757-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="df757-125">定義的公用屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="df757-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="df757-126">新增別名屬性，其中列出參數的別名。</span><span class="sxs-lookup"><span data-stu-id="df757-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="df757-127">在此範例中，針對相同的參數定義三個別名。</span><span class="sxs-lookup"><span data-stu-id="df757-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="df757-128">第一個別名提供捷徑。</span><span class="sxs-lookup"><span data-stu-id="df757-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="df757-129">第二個和第三個別名會提供您可以針對不同的案例中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="df757-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="df757-130">如需別名屬性的詳細資訊，請參閱[別名屬性宣告](./alias-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="df757-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df757-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df757-131">See Also</span></span>

[<span data-ttu-id="df757-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="df757-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="df757-133">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="df757-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="df757-134">別名屬性宣告</span><span class="sxs-lookup"><span data-stu-id="df757-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="df757-135">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df757-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
