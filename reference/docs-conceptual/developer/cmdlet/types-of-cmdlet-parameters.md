---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 參數類型
description: Cmdlet 參數類型
ms.openlocfilehash: 8daaa3c778396e06a826de3b93e0610c51160fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660485"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="b5ad0-103">Cmdlet 參數類型</span><span class="sxs-lookup"><span data-stu-id="b5ad0-103">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="b5ad0-104">本主題說明您可以在 Cmdlet 中宣告的不同參數類型。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-104">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="b5ad0-105">Cmdlet 參數可以是位置、命名、必要、選擇性或切換參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-105">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="b5ad0-106">位置和具名引數</span><span class="sxs-lookup"><span data-stu-id="b5ad0-106">Positional and Named Parameters</span></span>

<span data-ttu-id="b5ad0-107">所有 Cmdlet 參數都是命名或位置參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-107">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="b5ad0-108">具名引數需要您在呼叫 Cmdlet 時輸入參數名稱和引數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-108">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="b5ad0-109">位置參數只需要您以相對順序輸入引數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-109">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="b5ad0-110">然後系統會將第一個未命名的引數對應到第一個位置參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-110">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="b5ad0-111">系統會將第二個未命名的引數對應至第二個未命名的參數，依此類推。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-111">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="b5ad0-112">根據預設，所有 Cmdlet 參數都是具名引數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-112">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="b5ad0-113">若要定義具名引數，請省略 `Position` **參數** 屬性宣告中的關鍵字，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-113">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="b5ad0-114">若要定義位置參數，請 `Position` 在參數屬性宣告中加入關鍵字，然後指定位置。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-114">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="b5ad0-115">在下列範例中， `UserName` 會將參數宣告為位置0的位置參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-115">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="b5ad0-116">這表示呼叫的第一個引數會自動系結至此參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-116">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="b5ad0-117">良好的 Cmdlet 設計建議，最常使用的參數會宣告為位置參數，如此一來，當 Cmdlet 執行時，使用者就不需要輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-117">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="b5ad0-118">位置和具名引數接受單一引數，或以逗號分隔的多個引數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-118">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="b5ad0-119">只有在參數接受集合（例如字串陣列）時，才允許使用多個引數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-119">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="b5ad0-120">您可以在相同的 Cmdlet 中混合位置和具名引數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-120">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="b5ad0-121">在此情況下，系統會先抓取指名的引數，然後嘗試將其餘未命名的引數對應到位置參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-121">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="b5ad0-122">下列命令示範您可以針對 Cmdlet 的參數指定單一和多個引數的不同方式 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-122">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="b5ad0-123">請注意，在最後兩個範例中，不需要指定 **-name** ，因為 `Name` 參數定義為位置參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-123">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="b5ad0-124">必要參數和選擇性參數</span><span class="sxs-lookup"><span data-stu-id="b5ad0-124">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="b5ad0-125">您也可以將 Cmdlet 參數定義為強制或選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-125">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="b5ad0-126"> (必須在 Windows PowerShell 執行時間叫用 Cmdlet 之前指定必要參數。 ) 預設會將參數定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-126">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="b5ad0-127">若要定義強制參數，請 `Mandatory` 在參數屬性宣告中加入關鍵字，並將其設定為 `true` ，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-127">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="b5ad0-128">若要定義選擇性參數，請省略 `Mandatory` **參數** 屬性宣告中的關鍵字，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-128">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="b5ad0-129">切換參數</span><span class="sxs-lookup"><span data-stu-id="b5ad0-129">Switch Parameters</span></span>

<span data-ttu-id="b5ad0-130">Windows PowerShell 會提供 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 類型，可讓您定義參數，其值會在 `false` 呼叫 Cmdlet 時未指定參數時，自動設定為。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-130">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="b5ad0-131">可能的話，請使用 switch 參數取代布林值參數。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-131">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="b5ad0-132">請考慮下列範例。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-132">Consider the following sample.</span></span> <span data-ttu-id="b5ad0-133">根據預設，數個 Windows PowerShell Cmdlet 不會將輸出物件沿著管線向下傳遞。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-133">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="b5ad0-134">不過，這些 Cmdlet 有一個 `PassThru` 切換參數，可覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-134">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="b5ad0-135">如果在 `PassThru` 呼叫這些 Cmdlet 時指定參數，Cmdlet 會將輸出物件傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-135">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="b5ad0-136">如果您在 `true` 呼叫中未指定參數時需要參數的預設值，請考慮反轉參數的意義。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-136">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="b5ad0-137">如需範例，請將屬性宣告為 `true` [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 類型，然後將參數的預設值設定為，而不是將參數屬性設定為的布林 `false` 值。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-137">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="b5ad0-138">若要定義切換參數，請將屬性宣告為 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-138">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="b5ad0-139">若要讓 Cmdlet 在指定參數時採取動作，請在其中一個輸入處理方法內使用下列結構。</span><span class="sxs-lookup"><span data-stu-id="b5ad0-139">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b5ad0-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5ad0-140">See Also</span></span>

[<span data-ttu-id="b5ad0-141">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5ad0-141">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
