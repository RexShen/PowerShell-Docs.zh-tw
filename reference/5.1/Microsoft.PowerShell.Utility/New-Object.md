---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: a21fadd58ba566edfc6e484d753b53548f2b519b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203191"
---
# <span data-ttu-id="85c2e-103">New-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-103">New-Object</span></span>

## <span data-ttu-id="85c2e-104">概要</span><span class="sxs-lookup"><span data-stu-id="85c2e-104">SYNOPSIS</span></span>
<span data-ttu-id="85c2e-105">建立 Microsoft .NET Framework 或 COM 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="85c2e-105">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="85c2e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="85c2e-106">SYNTAX</span></span>

### <span data-ttu-id="85c2e-107">Net (預設值)</span><span class="sxs-lookup"><span data-stu-id="85c2e-107">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="85c2e-108">Com</span><span class="sxs-lookup"><span data-stu-id="85c2e-108">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="85c2e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="85c2e-109">DESCRIPTION</span></span>

<span data-ttu-id="85c2e-110">`New-Object`Cmdlet 會建立 .NET Framework 或 COM 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="85c2e-110">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="85c2e-111">您可以指定 .NET Framework 類別的類型或 COM 物件的 ProgID。</span><span class="sxs-lookup"><span data-stu-id="85c2e-111">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="85c2e-112">根據預設，您需要輸入 .NET Framework 類別的完整名稱，而這個 Cmdlet 會傳回該類別執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="85c2e-112">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="85c2e-113">若要建立 COM 物件的實例，請使用 **ComObject** 參數，並指定物件的 ProgID 做為其值。</span><span class="sxs-lookup"><span data-stu-id="85c2e-113">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="85c2e-114">範例</span><span class="sxs-lookup"><span data-stu-id="85c2e-114">EXAMPLES</span></span>

### <span data-ttu-id="85c2e-115">範例1：建立 System. Version 物件</span><span class="sxs-lookup"><span data-stu-id="85c2e-115">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="85c2e-116">此範例會使用 "1.2.3.4" 字串做為函式，建立 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="85c2e-116">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="85c2e-117">範例2：建立 Internet Explorer COM 物件</span><span class="sxs-lookup"><span data-stu-id="85c2e-117">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="85c2e-118">這個範例會建立代表 Internet Explorer 應用程式之 COM 物件的兩個實例。</span><span class="sxs-lookup"><span data-stu-id="85c2e-118">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="85c2e-119">第一個實例使用 **屬性** 參數雜湊表來呼叫 **Navigate2** 方法，並將物件的 **Visible** 屬性設定為， `$True` 讓應用程式成為可見的。</span><span class="sxs-lookup"><span data-stu-id="85c2e-119">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="85c2e-120">第二個實例會使用個別命令取得相同的結果。</span><span class="sxs-lookup"><span data-stu-id="85c2e-120">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="85c2e-121">範例3：使用 Strict 參數來產生非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="85c2e-121">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="85c2e-122">這個範例示範新增 **Strict** 參數會導致 `New-Object` Cmdlet 在 COM 物件使用 interop 元件時產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="85c2e-122">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### <span data-ttu-id="85c2e-123">範例4：建立 COM 物件來管理 Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="85c2e-123">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="85c2e-124">這個範例示範如何建立和使用 COM 物件來管理您的 Windows 桌面。</span><span class="sxs-lookup"><span data-stu-id="85c2e-124">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="85c2e-125">第一個命令會使用 Cmdlet 的 **ComObject** 參數 `New-Object` ，以 **Shell. 應用程式** ProgID 來建立 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="85c2e-125">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="85c2e-126">它會將產生的物件儲存在 `$ObjShell` 變數中。</span><span class="sxs-lookup"><span data-stu-id="85c2e-126">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="85c2e-127">第二個命令會 `$ObjShell` 以管道將變數傳送至 `Get-Member` Cmdlet，此 Cmdlet 會顯示 COM 物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="85c2e-127">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="85c2e-128">在這些方法中，方法是 **ToggleDesktop** 方法。</span><span class="sxs-lookup"><span data-stu-id="85c2e-128">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="85c2e-129">第三個命令呼叫物件的 **ToggleDesktop** 方法，將桌面上開啟的視窗最小化。</span><span class="sxs-lookup"><span data-stu-id="85c2e-129">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### <span data-ttu-id="85c2e-130">範例5：傳遞多個引數給函式</span><span class="sxs-lookup"><span data-stu-id="85c2e-130">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="85c2e-131">這個範例示範如何使用接受多個參數的函式來建立物件。</span><span class="sxs-lookup"><span data-stu-id="85c2e-131">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="85c2e-132">使用 **ArgumentList** 參數時，必須將參數放在陣列中。</span><span class="sxs-lookup"><span data-stu-id="85c2e-132">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="85c2e-133">PowerShell 會將陣列的每個成員系結至函式的參數。</span><span class="sxs-lookup"><span data-stu-id="85c2e-133">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="85c2e-134">這個範例會使用參數展開來提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="85c2e-134">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="85c2e-135">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="85c2e-135">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="85c2e-136">範例6：呼叫採用陣列作為單一參數的函式</span><span class="sxs-lookup"><span data-stu-id="85c2e-136">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="85c2e-137">這個範例示範如何使用接受陣列或集合參數的函式來建立物件。</span><span class="sxs-lookup"><span data-stu-id="85c2e-137">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="85c2e-138">陣列參數必須放在另一個陣列內。</span><span class="sxs-lookup"><span data-stu-id="85c2e-138">The array parameter must be put in wrapped inside another array.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

<span data-ttu-id="85c2e-139">在此範例中，第一次嘗試建立物件失敗。</span><span class="sxs-lookup"><span data-stu-id="85c2e-139">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="85c2e-140">PowerShell 嘗試將的三個成員系結至函式的 `$array` 參數，但此函式不會採用三個參數。</span><span class="sxs-lookup"><span data-stu-id="85c2e-140">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="85c2e-141">`$array`在另一個陣列中換行，可防止 PowerShell 嘗試將的三個成員系結至函式的 `$array` 參數。</span><span class="sxs-lookup"><span data-stu-id="85c2e-141">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="85c2e-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="85c2e-142">PARAMETERS</span></span>

### <span data-ttu-id="85c2e-143">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="85c2e-143">-ArgumentList</span></span>

<span data-ttu-id="85c2e-144">指定要傳遞給 .NET Framework 類別之函式的引數陣列。</span><span class="sxs-lookup"><span data-stu-id="85c2e-144">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="85c2e-145">如果此函式採用屬於陣列的單一參數，則您必須將該參數包裝在另一個陣列中。</span><span class="sxs-lookup"><span data-stu-id="85c2e-145">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="85c2e-146">例如：</span><span class="sxs-lookup"><span data-stu-id="85c2e-146">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="85c2e-147">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="85c2e-147">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="85c2e-148">**ArgumentList** 的別名是 **Args** 。</span><span class="sxs-lookup"><span data-stu-id="85c2e-148">The alias for **ArgumentList** is **Args** .</span></span>

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c2e-149">-ComObject</span><span class="sxs-lookup"><span data-stu-id="85c2e-149">-ComObject</span></span>

<span data-ttu-id="85c2e-150">指定 COM 物件的程式設計識別碼 (ProgID)。</span><span class="sxs-lookup"><span data-stu-id="85c2e-150">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c2e-151">-Property</span><span class="sxs-lookup"><span data-stu-id="85c2e-151">-Property</span></span>

<span data-ttu-id="85c2e-152">設定屬性值，並叫用新物件的方法。</span><span class="sxs-lookup"><span data-stu-id="85c2e-152">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="85c2e-153">輸入雜湊表，其中索引鍵為屬性或方法的名稱，而值為屬性值或方法引數。</span><span class="sxs-lookup"><span data-stu-id="85c2e-153">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="85c2e-154">`New-Object` 建立物件並設定每個屬性值，並依其在雜湊表中出現的順序來叫用每個方法。</span><span class="sxs-lookup"><span data-stu-id="85c2e-154">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="85c2e-155">如果新的物件衍生自 **PSObject** 類別，而且您指定了不存在於物件上的屬性，則會 `New-Object` 將指定的屬性加入至物件做為 NoteProperty。</span><span class="sxs-lookup"><span data-stu-id="85c2e-155">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="85c2e-156">如果物件不是 **PSObject** ，命令就會產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="85c2e-156">If the object is not a **PSObject** , the command generates a non-terminating error.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c2e-157">-Strict</span><span class="sxs-lookup"><span data-stu-id="85c2e-157">-Strict</span></span>

<span data-ttu-id="85c2e-158">指出當您嘗試建立的 COM 物件使用 interop 元件時，此 Cmdlet 會產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="85c2e-158">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="85c2e-159">這個功能可以區分真正的 COM 物件與使用 COM 可呼叫包裝函式的 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="85c2e-159">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c2e-160">-TypeName</span><span class="sxs-lookup"><span data-stu-id="85c2e-160">-TypeName</span></span>

<span data-ttu-id="85c2e-161">指定 .NET Framework 類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="85c2e-161">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="85c2e-162">您無法同時指定 **TypeName** 參數和 **ComObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="85c2e-162">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c2e-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85c2e-163">CommonParameters</span></span>

<span data-ttu-id="85c2e-164">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="85c2e-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85c2e-165">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="85c2e-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85c2e-166">輸入</span><span class="sxs-lookup"><span data-stu-id="85c2e-166">INPUTS</span></span>

### <span data-ttu-id="85c2e-167">無</span><span class="sxs-lookup"><span data-stu-id="85c2e-167">None</span></span>

<span data-ttu-id="85c2e-168">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="85c2e-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="85c2e-169">輸出</span><span class="sxs-lookup"><span data-stu-id="85c2e-169">OUTPUTS</span></span>

### <span data-ttu-id="85c2e-170">Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-170">Object</span></span>

<span data-ttu-id="85c2e-171">`New-Object` 傳回所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="85c2e-171">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="85c2e-172">注意</span><span class="sxs-lookup"><span data-stu-id="85c2e-172">NOTES</span></span>

- <span data-ttu-id="85c2e-173">`New-Object` 提供 VBScript CreateObject 函式最常使用的功能。</span><span class="sxs-lookup"><span data-stu-id="85c2e-173">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="85c2e-174">`Set objShell = CreateObject("Shell.Application")`VBScript 中的語句可 `$objShell = New-Object -COMObject "Shell.Application"` 在 PowerShell 中轉譯為。</span><span class="sxs-lookup"><span data-stu-id="85c2e-174">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="85c2e-175">`New-Object` 利用 Windows Script Host 環境中的可用功能，輕鬆地從命令列和腳本內使用 .NET Framework 物件，以擴充其功能。</span><span class="sxs-lookup"><span data-stu-id="85c2e-175">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="85c2e-176">相關連結</span><span class="sxs-lookup"><span data-stu-id="85c2e-176">RELATED LINKS</span></span>

[<span data-ttu-id="85c2e-177">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="85c2e-177">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="85c2e-178">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-178">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="85c2e-179">Group-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-179">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="85c2e-180">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-180">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="85c2e-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-181">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="85c2e-182">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-182">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="85c2e-183">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="85c2e-183">Tee-Object</span></span>](Tee-Object.md)
