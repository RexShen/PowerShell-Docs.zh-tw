---
title: Cmdlet 參數的類型 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e704aae6e23568be9935e228752f652929863a98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786368"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="ea595-102">Cmdlet 參數類型</span><span class="sxs-lookup"><span data-stu-id="ea595-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="ea595-103">本主題說明您可以在 Cmdlet 中宣告的不同參數類型。</span><span class="sxs-lookup"><span data-stu-id="ea595-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="ea595-104">Cmdlet 參數可以是位置、命名、必要、選擇性或切換參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="ea595-105">位置和具名引數</span><span class="sxs-lookup"><span data-stu-id="ea595-105">Positional and Named Parameters</span></span>

<span data-ttu-id="ea595-106">所有 Cmdlet 參數都是命名或位置參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="ea595-107">呼叫 Cmdlet 時，會要求您輸入參數名稱和引數。</span><span class="sxs-lookup"><span data-stu-id="ea595-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="ea595-108">位置參數只需要您以相對順序輸入引數。</span><span class="sxs-lookup"><span data-stu-id="ea595-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="ea595-109">然後，系統會將第一個未命名的引數對應到第一個位置參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="ea595-110">系統會將第二個未命名的引數對應到第二個未命名的參數，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ea595-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="ea595-111">根據預設，所有 Cmdlet 參數都會命名為參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="ea595-112">若要定義名為的參數，請省略 `Position` **參數**屬性宣告中的關鍵字，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="ea595-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ea595-113">若要定義位置參數，請 `Position` 在參數屬性宣告中新增關鍵字，然後指定位置。</span><span class="sxs-lookup"><span data-stu-id="ea595-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="ea595-114">在下列範例中， `UserName` 會將參數宣告為位置參數，其位置為0。</span><span class="sxs-lookup"><span data-stu-id="ea595-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="ea595-115">這表示呼叫的第一個引數會自動系結至此參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="ea595-116">良好的 Cmdlet 設計建議將最常使用的參數宣告為位置參數，如此一來，當 Cmdlet 執行時，使用者就不需要輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="ea595-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="ea595-117">位置和具名引數接受單一引數或以逗號分隔的多個引數。</span><span class="sxs-lookup"><span data-stu-id="ea595-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="ea595-118">只有當參數接受集合（例如字串陣列）時，才允許使用多個引數。</span><span class="sxs-lookup"><span data-stu-id="ea595-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="ea595-119">您可以在相同的 Cmdlet 中混合位置和具名引數。</span><span class="sxs-lookup"><span data-stu-id="ea595-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="ea595-120">在此情況下，系統會先抓取具名引數，然後再嘗試將其餘未命名的引數對應到位置參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="ea595-121">下列命令會顯示您可以為 Cmdlet 的參數指定單一和多個引數的不同方式 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="ea595-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="ea595-122">請注意，在最後兩個範例中，不需要指定 **-name** ，因為 `Name` 參數定義為位置參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="ea595-123">必要和選擇性參數</span><span class="sxs-lookup"><span data-stu-id="ea595-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="ea595-124">您也可以將 Cmdlet 參數定義為強制或選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="ea595-125"> (必須先指定必要參數，Windows PowerShell 執行時間才會叫用 Cmdlet。 ) 預設會將參數定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="ea595-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="ea595-126">若要定義強制參數，請 `Mandatory` 在參數屬性宣告中新增關鍵字，並將它設定為 `true` ，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="ea595-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ea595-127">若要定義選擇性參數，請省略 `Mandatory` **參數**屬性宣告中的關鍵字，如下列參數宣告所示。</span><span class="sxs-lookup"><span data-stu-id="ea595-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="ea595-128">切換參數</span><span class="sxs-lookup"><span data-stu-id="ea595-128">Switch Parameters</span></span>

<span data-ttu-id="ea595-129">Windows PowerShell 提供[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，可讓您定義參數，其值會自動設定為， `false` 如果在呼叫 Cmdlet 時未指定參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="ea595-130">盡可能使用切換參數來取代布林值參數。</span><span class="sxs-lookup"><span data-stu-id="ea595-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="ea595-131">請考慮下列範例。</span><span class="sxs-lookup"><span data-stu-id="ea595-131">Consider the following sample.</span></span> <span data-ttu-id="ea595-132">根據預設，數個 Windows PowerShell Cmdlet 不會將輸出物件沿著管線向下傳遞。</span><span class="sxs-lookup"><span data-stu-id="ea595-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="ea595-133">不過，這些 Cmdlet 具有 `PassThru` 切換參數，會覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="ea595-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="ea595-134">如果在 `PassThru` 呼叫這些 Cmdlet 時指定參數，Cmdlet 會將輸出物件傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="ea595-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="ea595-135">如果您需要參數 `true` 在呼叫中未指定參數時具有預設值，請考慮反轉參數的意義。</span><span class="sxs-lookup"><span data-stu-id="ea595-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="ea595-136">如需範例，請將 `true` 屬性宣告為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，然後將參數的預設值設定為，而不是將參數屬性設定為的布林 `false` 值。</span><span class="sxs-lookup"><span data-stu-id="ea595-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="ea595-137">若要定義切換參數，請將屬性宣告為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea595-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="ea595-138">若要讓 Cmdlet 在指定時對參數採取動作，請在其中一個輸入處理方法內使用下列結構。</span><span class="sxs-lookup"><span data-stu-id="ea595-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ea595-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea595-139">See Also</span></span>

[<span data-ttu-id="ea595-140">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea595-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
