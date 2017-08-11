---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "建立 .NET 和 COM 物件 New Object"
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 534e1a9a759d67cfc62ce658a7abddf02f767212
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="ee86f-103">建立 .NET 和 COM 物件 (New-Object)</span><span class="sxs-lookup"><span data-stu-id="ee86f-103">Creating .NET and COM Objects (New-Object)</span></span>
<span data-ttu-id="ee86f-104">您可以透過具有 .NET Framework 和 COM 介面的軟體元件，來執行許多系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="ee86f-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="ee86f-105">Windows PowerShell 可讓您使用這些元件，因此您不再僅限於使用 Cmdlet 執行工作。</span><span class="sxs-lookup"><span data-stu-id="ee86f-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="ee86f-106">Windows PowerShell 的初始版本中有許多 Cmdlet 無法對遠端電腦執行。</span><span class="sxs-lookup"><span data-stu-id="ee86f-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="ee86f-107">我們將示範如何從 Windows PowerShell 直接使用 .NET Framework **System.Diagnostics.EventLog** 類別，以克服管理事件記錄檔時的這項限制。</span><span class="sxs-lookup"><span data-stu-id="ee86f-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="ee86f-108">使用 New-Object 存取事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="ee86f-108">Using New-Object for Event Log Access</span></span>
<span data-ttu-id="ee86f-109">.NET Framework 類別庫包含名為 **System.Diagnostics.EventLog** 的類別，可用來管理事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ee86f-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="ee86f-110">您可以使用 **New-Object** Cmdlet 搭配 **TypeName** 參數，建立 .NET Framework 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee86f-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="ee86f-111">例如，下列命令會建立事件記錄檔參考：</span><span class="sxs-lookup"><span data-stu-id="ee86f-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="ee86f-112">雖然此命令已建立 EventLog 類別的執行個體，但是該執行個體不會包含任何資料。</span><span class="sxs-lookup"><span data-stu-id="ee86f-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="ee86f-113">這是因為我們並未指定特定事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ee86f-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="ee86f-114">如何取得實際事件記錄檔？</span><span class="sxs-lookup"><span data-stu-id="ee86f-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="ee86f-115">搭配使用建構函式和 New-Object</span><span class="sxs-lookup"><span data-stu-id="ee86f-115">Using Constructors with New-Object</span></span>
<span data-ttu-id="ee86f-116">若要參考特定事件記錄檔，您需要指定記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ee86f-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="ee86f-117">**New-Object** 具有 **ArgumentList** 參數。</span><span class="sxs-lookup"><span data-stu-id="ee86f-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="ee86f-118">物件的特殊啟動方法會使用您以值傳遞給這個參數的引數。</span><span class="sxs-lookup"><span data-stu-id="ee86f-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="ee86f-119">該方法稱為*建構函式*，因為它可用來建構物件。</span><span class="sxs-lookup"><span data-stu-id="ee86f-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="ee86f-120">例如，若要取得應用程式記錄檔參考，您會將字串 'Application' 指定為引數︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="ee86f-121">由於大部分的 .NET Framework 核心類別都包含在 System 命名空間中，因此如果 Windows PowerShell 找不到您指定之 typename 的相符項目，就會自動嘗試尋找您在 System 命名空間中指定的類別。</span><span class="sxs-lookup"><span data-stu-id="ee86f-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="ee86f-122">這表示您可以指定 Diagnostics.EventLog，而不是 System.Diagnostics.EventLog。</span><span class="sxs-lookup"><span data-stu-id="ee86f-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="ee86f-123">將物件儲存在變數中</span><span class="sxs-lookup"><span data-stu-id="ee86f-123">Storing Objects in Variables</span></span>
<span data-ttu-id="ee86f-124">您可能想要儲存物件參考，以便在目前的殼層中使用。</span><span class="sxs-lookup"><span data-stu-id="ee86f-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="ee86f-125">雖然 Windows PowerShell 可讓您執行許多管線工作，因而降低變數的需要，但是有時將物件參考儲存在變數中，可以更方便管理這些物件。</span><span class="sxs-lookup"><span data-stu-id="ee86f-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="ee86f-126">Windows PowerShell 可讓您建立基本上為具名物件的變數。</span><span class="sxs-lookup"><span data-stu-id="ee86f-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="ee86f-127">任何有效的 Windows PowerShell 命令輸出都能儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="ee86f-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="ee86f-128">變數名稱一律會以 $ 開頭。</span><span class="sxs-lookup"><span data-stu-id="ee86f-128">Variable names always begin with $.</span></span> <span data-ttu-id="ee86f-129">如果您想要將應用程式記錄檔參考儲存在名為 $AppLog 的變數中，請輸入變數的名稱，後面接著等號，然後輸入用來建立應用程式記錄檔物件的命令︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="ee86f-130">如果您接著輸入 $AppLog，您可以看到它包含了應用程式記錄檔︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="ee86f-131">使用 New-Object 存取遠端事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="ee86f-131">Accessing a Remote Event Log with New-Object</span></span>
<span data-ttu-id="ee86f-132">上一節所使用的命令是以本機電腦為目標；**Get-EventLog** Cmdlet 可以執行該作業。</span><span class="sxs-lookup"><span data-stu-id="ee86f-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="ee86f-133">若要存取遠端電腦上的應用程式記錄檔，您必須同時提供記錄檔名稱和電腦名稱 (或 IP 位址) 作為引數。</span><span class="sxs-lookup"><span data-stu-id="ee86f-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="ee86f-134">將事件記錄檔參考儲存在 $RemoteAppLog 變數之後，可對其執行哪些工作？</span><span class="sxs-lookup"><span data-stu-id="ee86f-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="ee86f-135">使用物件方法清除事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="ee86f-135">Clearing an Event Log with Object Methods</span></span>
<span data-ttu-id="ee86f-136">物件通常具有可呼叫以執行工作的方法。</span><span class="sxs-lookup"><span data-stu-id="ee86f-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="ee86f-137">您可以使用 **Get-Member**，顯示與物件相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="ee86f-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="ee86f-138">下列命令和選取的輸出顯示 EventLog 類別的一些方法︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="ee86f-139">**Clear()** 方法可用來清除事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ee86f-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="ee86f-140">呼叫方法時，您必須一律在方法名稱後面加上括弧，即使方法不需要引數亦然。</span><span class="sxs-lookup"><span data-stu-id="ee86f-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="ee86f-141">這可讓 Windows PowerShell 在此方法與具有相同名稱的潛在屬性之間進行區別。</span><span class="sxs-lookup"><span data-stu-id="ee86f-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="ee86f-142">輸入下列命令呼叫 **Clear** 方法︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="ee86f-143">輸入下列命令顯示記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ee86f-143">Type the following to display the log.</span></span> <span data-ttu-id="ee86f-144">您會看到事件記錄檔已清除，現在有 0 個而不是 262 個項目：</span><span class="sxs-lookup"><span data-stu-id="ee86f-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="ee86f-145">使用 New-Object 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="ee86f-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="ee86f-146">您可以使用 **New-Object** 來處理元件物件模型 (COM) 元件。</span><span class="sxs-lookup"><span data-stu-id="ee86f-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="ee86f-147">元件範圍從 Windows Script Host (WSH) 隨附的各種程式庫，到安裝在大多數系統上的 ActiveX 應用程式 (例如 Internet Explorer)。</span><span class="sxs-lookup"><span data-stu-id="ee86f-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="ee86f-148">**New-Object** 使用 .NET Framework 執行階段可呼叫包裝函式來建立 COM 物件，因此與呼叫 COM 物件時具有相同的 .NET Framework 限制。</span><span class="sxs-lookup"><span data-stu-id="ee86f-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="ee86f-149">若要建立 COM 物件，您需要指定 **ComObject** 參數，並提供所要使用之 COM 類別的程式設計識別碼 (或 *ProgID*)。</span><span class="sxs-lookup"><span data-stu-id="ee86f-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="ee86f-150">COM 使用限制及判斷系統上可用 ProgID 的完整探討不在本使用者指南的討論範圍內，但 WSH 等環境中的大部分已知物件都可以在 Windows PowerShell 中使用。</span><span class="sxs-lookup"><span data-stu-id="ee86f-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="ee86f-151">您可以透過指定下列 ProgID 來建立 WSH 物件︰**WScript.Shell**、**WScript.Network**、**Scripting.Dictionary** 和 **Scripting.FileSystemObject**。</span><span class="sxs-lookup"><span data-stu-id="ee86f-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="ee86f-152">下列命令會建立這些物件：</span><span class="sxs-lookup"><span data-stu-id="ee86f-152">The following commands create these objects:</span></span>

```
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="ee86f-153">雖然這些類別的大部分功能都可以利用 Windows PowerShell 的其他方式提供，但針對建立捷徑等一些工作，使用 WSH 類別還是比較容易進行。</span><span class="sxs-lookup"><span data-stu-id="ee86f-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="ee86f-154">使用 WScript.Shell 建立桌面捷徑</span><span class="sxs-lookup"><span data-stu-id="ee86f-154">Creating a Desktop Shortcut with WScript.Shell</span></span>
<span data-ttu-id="ee86f-155">您可以透過 COM 物件快速執行的一項工作就是建立捷徑。</span><span class="sxs-lookup"><span data-stu-id="ee86f-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="ee86f-156">假設您想要在桌面上建立捷徑，以連結到 Windows PowerShell 的主資料夾。</span><span class="sxs-lookup"><span data-stu-id="ee86f-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="ee86f-157">您必須先建立 **WScript.Shell** 的參考，我們將儲存在名為 **$WshShell** 的變數中：</span><span class="sxs-lookup"><span data-stu-id="ee86f-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="ee86f-158">Get-Member 可用於 COM 物件，因此您可以輸入下列命令瀏覽物件成員︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="ee86f-159">**Get-Member** 具有選擇性 **InputObject** 參數，您可以改用此參數提供輸入而不是傳送到 **Get-Member**。</span><span class="sxs-lookup"><span data-stu-id="ee86f-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="ee86f-160">如果您改用命令 **Get-Member -InputObject $WshShell**，會得到如上所示的相同輸出。</span><span class="sxs-lookup"><span data-stu-id="ee86f-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="ee86f-161">如果您使用 **InputObject**，它會將其引數視為單一項目。</span><span class="sxs-lookup"><span data-stu-id="ee86f-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="ee86f-162">這表示如果您在變數中有數個物件，**Get-Member** 會將其視為物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="ee86f-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="ee86f-163">例如：</span><span class="sxs-lookup"><span data-stu-id="ee86f-163">For example:</span></span>


```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="ee86f-164">**WScript.Shell CreateShortcut** 方法接受單一引數，也就是要建立的捷徑檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="ee86f-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="ee86f-165">我們可以輸入桌面的完整路徑，但還有更簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="ee86f-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="ee86f-166">桌面通常會以目前使用者的主資料夾內名為 [桌面] 的資料夾來表示。</span><span class="sxs-lookup"><span data-stu-id="ee86f-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="ee86f-167">Windows PowerShell 有一個包含此資料夾路徑的變數 **$Home**。</span><span class="sxs-lookup"><span data-stu-id="ee86f-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="ee86f-168">我們可以使用此變數指定主資料夾的路徑，然後加入 [桌面] 資料夾的名稱及要建立的捷徑名稱，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="ee86f-169">當您使用類似雙引號內的變數名稱時，Windows PowerShell 會嘗試取代為相符的值。</span><span class="sxs-lookup"><span data-stu-id="ee86f-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="ee86f-170">如果您使用單引號，Windows PowerShell 不會嘗試取代變數值。</span><span class="sxs-lookup"><span data-stu-id="ee86f-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="ee86f-171">例如，嘗試輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ee86f-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="ee86f-172">我們現在有一個名為 **$lnk** 的變數，其中包含新的捷徑參考。</span><span class="sxs-lookup"><span data-stu-id="ee86f-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="ee86f-173">如果您想要查看其成員，您可以將其傳送到 **Get-Member**。</span><span class="sxs-lookup"><span data-stu-id="ee86f-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="ee86f-174">以下的輸出顯示完成建立捷徑所需使用的成員︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="ee86f-175">我們需要指定 Windows PowerShell 的應用程式資料夾 **TargetPath**，然後再呼叫 **Save** 方法來儲存捷徑 **$lnk**。</span><span class="sxs-lookup"><span data-stu-id="ee86f-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="ee86f-176">Windows PowerShell 應用程式資料夾路徑儲存在變數 **$PSHome** 中，因此我們可以輸入下列命令來執行此作業︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="ee86f-177">從 Windows PowerShell 使用 Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="ee86f-177">Using Internet Explorer from Windows PowerShell</span></span>
<span data-ttu-id="ee86f-178">許多應用程式 (包括 Microsoft Office 系列應用程式和 Internet Explorer) 都可以透過 COM 自動化。</span><span class="sxs-lookup"><span data-stu-id="ee86f-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="ee86f-179">Internet Explorer 說明一些與使用 COM 應用程式相關的典型技術和問題。</span><span class="sxs-lookup"><span data-stu-id="ee86f-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="ee86f-180">您可以指定 Internet Explorer ProgID **InternetExplorer.Application** 來建立 Internet Explorer 執行個體：</span><span class="sxs-lookup"><span data-stu-id="ee86f-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="ee86f-181">此命令會啟動但不會顯示 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="ee86f-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="ee86f-182">如果您輸入 Get-Process，您可以看到名為 iexplore 的處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="ee86f-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="ee86f-183">事實上，如果您結束 Windows PowerShell，該處理序會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="ee86f-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="ee86f-184">您必須重新啟動電腦或使用工作管理員等工具，才能結束 iexplore 處理序。</span><span class="sxs-lookup"><span data-stu-id="ee86f-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="ee86f-185">以個別處理序啟動的 COM 物件通常稱為*ActiveX 可執行檔*，啟動時不一定會顯示使用者介面視窗。</span><span class="sxs-lookup"><span data-stu-id="ee86f-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="ee86f-186">像是 Internet Explorer，如果建立但未顯示視窗，通常會將焦點移至 Windows 桌面，而您必須顯示視窗才能與其互動。</span><span class="sxs-lookup"><span data-stu-id="ee86f-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="ee86f-187">您可以輸入 **$ie | Get-Member**，以檢視 Internet Explorer 的內容和方法。</span><span class="sxs-lookup"><span data-stu-id="ee86f-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="ee86f-188">若要看到 Internet Explorer 視窗，請輸入下列命令將 Visible 屬性設定為 $true︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```
$ie.Visible = $true
```

<span data-ttu-id="ee86f-189">您接著可以使用 Navigate 方法瀏覽至特定網址︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="ee86f-190">透過 Internet Explorer 物件模型的其他成員，您可以從網頁擷取文字內容。</span><span class="sxs-lookup"><span data-stu-id="ee86f-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="ee86f-191">下列命令會顯示目前網頁內文中的 HTML 文字 ︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```
$ie.Document.Body.InnerText
```

<span data-ttu-id="ee86f-192">若要從 PowerShell 關閉 Internet Explorer，請呼叫其 Quit() 方法︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```
$ie.Quit()
```

<span data-ttu-id="ee86f-193">這會強制關閉。</span><span class="sxs-lookup"><span data-stu-id="ee86f-193">This will force it to close.</span></span> <span data-ttu-id="ee86f-194">$Ie 變數雖然仍會顯示為 COM 物件，但已不再包含有效的參考。</span><span class="sxs-lookup"><span data-stu-id="ee86f-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="ee86f-195">如果您嘗試使用，您會收到自動化錯誤︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="ee86f-196">您可以使用 $ie = $null 等命令移除其餘參考，或輸入下列命令完全移除變數︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="ee86f-197">當您移除 ActiveX 可執行檔參考時，ActiveX 可執行檔會結束或繼續執行，並沒有通用標準。</span><span class="sxs-lookup"><span data-stu-id="ee86f-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="ee86f-198">根據應用程式是否顯示、其中是否正在執行編輯的文件，甚至是根據 Windows PowerShell 是否仍在執行等情況，應用程式可能結束，也可能不會結束。</span><span class="sxs-lookup"><span data-stu-id="ee86f-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="ee86f-199">因此，您應該針對要在 Windows PowerShell 中使用的每個 ActiveX 可執行檔，測試其終止行為。</span><span class="sxs-lookup"><span data-stu-id="ee86f-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="ee86f-200">取得 .NET Framework 包裝之 COM 物件的相關警告</span><span class="sxs-lookup"><span data-stu-id="ee86f-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>
<span data-ttu-id="ee86f-201">在某些情況下，COM 物件可能會有相關聯的 .NET Framework *執行階段可呼叫包裝函式* (或 RCW)，**New-Object** 將會使用此包裝函式。</span><span class="sxs-lookup"><span data-stu-id="ee86f-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="ee86f-202">因為 RCW 的行為可能與一般 COM 物件的行為不同，所以 **New-Object** 提供了 **Strict** 參數，以警告您 RCW 的存取。</span><span class="sxs-lookup"><span data-stu-id="ee86f-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="ee86f-203">如果您指定 **Strict** 參數，然後建立使用 RCW 的 COM 物件，您會收到警告訊息︰</span><span class="sxs-lookup"><span data-stu-id="ee86f-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="ee86f-204">雖然物件仍會建立，但您會收到警告，指出該物件不是標準 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="ee86f-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>

