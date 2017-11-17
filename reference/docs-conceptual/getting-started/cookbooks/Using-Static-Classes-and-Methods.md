---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用靜態類別和方法"
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="75fed-103">使用靜態類別和方法</span><span class="sxs-lookup"><span data-stu-id="75fed-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="75fed-104">並非所有的 .NET Framework 類別都能使用 **New-Object** 建立。</span><span class="sxs-lookup"><span data-stu-id="75fed-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="75fed-105">例如，如果您嘗試使用 **New-Object** 來建立 **System.Environment** 或 **System.Math** 物件，則會收到下列錯誤訊息︰</span><span class="sxs-lookup"><span data-stu-id="75fed-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment
PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="75fed-106">這些錯誤的發生原因是沒有方法可透過這些類別建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="75fed-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="75fed-107">這些類別是未變更狀態之方法和屬性的參考程式庫。</span><span class="sxs-lookup"><span data-stu-id="75fed-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="75fed-108">您不需要建立它們，而只需要使用它們。</span><span class="sxs-lookup"><span data-stu-id="75fed-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="75fed-109">這類類別和方法稱為*靜態類別*，因為不會建立、破壞或變更它們。</span><span class="sxs-lookup"><span data-stu-id="75fed-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="75fed-110">為了讓這個概念更為清楚，我們將提供使用靜態類別的範例。</span><span class="sxs-lookup"><span data-stu-id="75fed-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="75fed-111">使用 System.Environment 取得環境資料</span><span class="sxs-lookup"><span data-stu-id="75fed-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="75fed-112">通常，在 Windows PowerShell 中使用物件的第一個步驟是使用 Get-Member 來找出它包含的成員。</span><span class="sxs-lookup"><span data-stu-id="75fed-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="75fed-113">運用靜態類別時，處理方式會有些不同，因為實際類別不是物件。</span><span class="sxs-lookup"><span data-stu-id="75fed-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="75fed-114">參考靜態 System.Environment 類別</span><span class="sxs-lookup"><span data-stu-id="75fed-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="75fed-115">使用方括弧括住類別名稱，即可參考靜態類別。</span><span class="sxs-lookup"><span data-stu-id="75fed-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="75fed-116">例如，在方括弧內輸入名稱，即可參考 **System.Environment**。</span><span class="sxs-lookup"><span data-stu-id="75fed-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="75fed-117">這麼做會顯示一些泛型類型資訊︰</span><span class="sxs-lookup"><span data-stu-id="75fed-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="75fed-118">如前所述，Windows PowerShell 會自動將 '**System.**'</span><span class="sxs-lookup"><span data-stu-id="75fed-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="75fed-119">加到類型名稱的前面 (使用 **New-Object** 時)。</span><span class="sxs-lookup"><span data-stu-id="75fed-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="75fed-120">使用以方括弧括住的類型名稱時會發生相同的作業，因此您可以將 **\[System.Environment]** 指定為 **\[Environment]**。</span><span class="sxs-lookup"><span data-stu-id="75fed-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="75fed-121">**System.Environment** 類別包含目前處理處序之運作環境的一般資訊 (在 Windows PowerShell 內運作時為 powershell.exe)。</span><span class="sxs-lookup"><span data-stu-id="75fed-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="75fed-122">如果您輸入 **\[System.Environment] | Get-Member** 來嘗試檢視這個類別的詳細資訊，則物件類型會回報為 **System.RuntimeType**，而非 **System.Environment**：</span><span class="sxs-lookup"><span data-stu-id="75fed-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="75fed-123">若要使用 Get-Member 來檢視靜態成員，請指定 **Static** 參數︰</span><span class="sxs-lookup"><span data-stu-id="75fed-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="75fed-124">我們現在可以從 System.Environment 中選取要檢視的屬性。</span><span class="sxs-lookup"><span data-stu-id="75fed-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="75fed-125">顯示 System.Environment 的靜態屬性</span><span class="sxs-lookup"><span data-stu-id="75fed-125">Displaying Static Properties of System.Environment</span></span>
<span data-ttu-id="75fed-126">System.Environment 的屬性也是靜態的，而且指定的方式必須與一般屬性不同。</span><span class="sxs-lookup"><span data-stu-id="75fed-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="75fed-127">我們使用 **::** 向 Windows PowerShell 表示我們想要使用靜態方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="75fed-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="75fed-128">若要查看已用來啟動 Windows PowerShell 的命令，我們會檢查 **CommandLine** 屬性，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="75fed-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="75fed-129">若要檢查作業系統版本，請顯示 OSVersion 屬性，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="75fed-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="75fed-130">顯示 **HasShutdownStarted** 屬性，即可檢查電腦是否正在進行關機：</span><span class="sxs-lookup"><span data-stu-id="75fed-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="75fed-131">使用 System.Math 執行數學運算</span><span class="sxs-lookup"><span data-stu-id="75fed-131">Doing Math with System.Math</span></span>
<span data-ttu-id="75fed-132">System.Math 靜態類別適用於執行一些數學運算。</span><span class="sxs-lookup"><span data-stu-id="75fed-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="75fed-133">**System.Math** 的重要成員主要是方法，而使用 **Get-Member** 即可顯示這些方法。</span><span class="sxs-lookup"><span data-stu-id="75fed-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="75fed-134">System.Math 有數種同名的方法，但透過其參數的類型予以區分。</span><span class="sxs-lookup"><span data-stu-id="75fed-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="75fed-135">輸入下列命令來列出 **System.Math** 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="75fed-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="75fed-136">這會顯示數個數學方法。</span><span class="sxs-lookup"><span data-stu-id="75fed-136">This displays several mathematical methods.</span></span> <span data-ttu-id="75fed-137">以下是示範一些常見方法之運作方式的命令清單 ︰</span><span class="sxs-lookup"><span data-stu-id="75fed-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```

