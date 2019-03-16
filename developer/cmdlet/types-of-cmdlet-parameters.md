---
title: Cmdlet 參數的型別 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059570"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="b1cf9-102">Cmdlet 參數類型</span><span class="sxs-lookup"><span data-stu-id="b1cf9-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="b1cf9-103">本主題說明不同類型的 cmdlet 中，您可以宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="b1cf9-104">Cmdlet 參數可以是位置、 具名、 必要、 選擇性的或切換參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="b1cf9-105">位置和具名參數</span><span class="sxs-lookup"><span data-stu-id="b1cf9-105">Positional and Named Parameters</span></span>

<span data-ttu-id="b1cf9-106">所有的 cmdlet 參數是具名或位置參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="b1cf9-107">具名的參數需要呼叫 cmdlet 時，您輸入的參數名稱和引數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="b1cf9-108">位置參數只要求您輸入的引數，以相對順序。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="b1cf9-109">系統則會對應至第一個位置參數的第一個未命名的引數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="b1cf9-110">系統會將第二個未命名的引數對應到第二個未命名的參數，並依此類推。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="b1cf9-111">根據預設，所有的 cmdlet 參數為具名參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="b1cf9-112">若要定義具名的參數，請省略`Position`中的關鍵字**參數**屬性宣告，如下列的參數宣告中所示。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="b1cf9-113">若要定義位置的參數，新增`Position`參數中的關鍵字屬性宣告，然後再指定 位置。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="b1cf9-114">在下列範例中，`UserName`參數宣告為位置參數與位置 0。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="b1cf9-115">這表示，呼叫的第一個引數會自動繫結至這個參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="b1cf9-116">良好的 cmdlet 的設計建議，最常用的參數可以宣告為位置參數，讓使用者沒有執行此 cmdlet 時輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="b1cf9-117">位置和具名參數接受單一引數或以逗號分隔的多個引數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="b1cf9-118">只有當參數接受字串陣列，例如集合時，才允許多個引數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="b1cf9-119">您可能會混合在相同的 cmdlet 中的位置和具名參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="b1cf9-120">在此情況下，系統第一，擷取具名引數，然後將對應的剩餘的嘗試未命名的位置參數的引數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="b1cf9-121">下列命令會顯示不同的方式，可以指定單一和多個引數的參數`Get-Command`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="b1cf9-122">請注意，在最後兩個範例中， **-名稱**不需要指定因為`Name`參數會定義為位置參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="b1cf9-123">必要和選擇性參數</span><span class="sxs-lookup"><span data-stu-id="b1cf9-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="b1cf9-124">您也可以定義為強制或選擇性參數的 cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="b1cf9-125">（必要的參數必須指定之前，Windows PowerShell 執行階段會叫用此指令程式。）根據預設，參數會定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="b1cf9-126">若要定義必要的參數，請新增`Mandatory`參數中的關鍵字屬性宣告，並將它設定為`true`，如下列的參數宣告中所示。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="b1cf9-127">若要定義的選擇性參數，請省略`Mandatory`中的關鍵字**參數**屬性宣告，如下列的參數宣告中所示。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="b1cf9-128">切換參數</span><span class="sxs-lookup"><span data-stu-id="b1cf9-128">Switch Parameters</span></span>

<span data-ttu-id="b1cf9-129">Windows PowerShell 提供[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)可讓您定義的參數值的型別會自動設為`false`如果 cmdlet 時未指定參數呼叫。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="b1cf9-130">可能的話，使用切換參數來取代布林參數。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="b1cf9-131">請考慮下列的範例。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-131">Consider the following sample.</span></span> <span data-ttu-id="b1cf9-132">根據預設，數個 Windows PowerShell cmdlet 不要傳遞到管線的輸出物件。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="b1cf9-133">不過，這些 cmdlet 有`PassThru`切換參數會覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="b1cf9-134">如果`PassThru`呼叫這些 cmdlet 時指定參數，此 cmdlet 會輸出物件傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="b1cf9-135">如果您需要的參數具有預設值是`true`時呼叫中未指定參數，請考慮將反轉參數的意義。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="b1cf9-136">如需範例，而不是設定參數屬性的布林值`true`，宣告為屬性[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)輸入，並將參數的預設值`false`.</span><span class="sxs-lookup"><span data-stu-id="b1cf9-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="b1cf9-137">若要定義的切換參數，宣告將屬性視為[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="b1cf9-138">若要讓參數在處理時有指定此 cmdlet，使用下列結構的輸入處理方法的其中一個內。</span><span class="sxs-lookup"><span data-stu-id="b1cf9-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="b1cf9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cf9-139">See Also</span></span>

[<span data-ttu-id="b1cf9-140">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b1cf9-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
