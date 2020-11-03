---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 2ed19d8def95d9c83ae950af263bae5110e3b2f1
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206064"
---
# <span data-ttu-id="bfb9b-103">Get-Location</span><span class="sxs-lookup"><span data-stu-id="bfb9b-103">Get-Location</span></span>

## <span data-ttu-id="bfb9b-104">概要</span><span class="sxs-lookup"><span data-stu-id="bfb9b-104">SYNOPSIS</span></span>
<span data-ttu-id="bfb9b-105">取得目前工作位置或位置堆疊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-105">Gets information about the current working location or a location stack.</span></span>

## <span data-ttu-id="bfb9b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bfb9b-106">SYNTAX</span></span>

### <span data-ttu-id="bfb9b-107">Location (預設值)</span><span class="sxs-lookup"><span data-stu-id="bfb9b-107">Location (Default)</span></span>

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="bfb9b-108">Stack</span><span class="sxs-lookup"><span data-stu-id="bfb9b-108">Stack</span></span>

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="bfb9b-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bfb9b-109">DESCRIPTION</span></span>

<span data-ttu-id="bfb9b-110">`Get-Location`Cmdlet 會取得代表目前目錄的物件，與列印工作目錄 (pwd) 命令很相似。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-110">The `Get-Location` cmdlet gets an object that represents the current directory, much like the print working directory (pwd) command.</span></span>

<span data-ttu-id="bfb9b-111">當您在 PowerShell 磁片磁碟機之間移動時，PowerShell 會保留您在每個磁片磁碟機中的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-111">When you move between PowerShell drives, PowerShell retains your location in each drive.</span></span> <span data-ttu-id="bfb9b-112">您可以使用這個 Cmdlet 來尋找每個磁片磁碟機中的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-112">You can use this cmdlet to find your location in each drive.</span></span>

<span data-ttu-id="bfb9b-113">您可以使用這個指令程式，在執行時間取得目前的目錄，並將它用於函式和腳本中，例如在 PowerShell 提示字元中顯示目前目錄的函式中。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-113">You can use this cmdlet to get the current directory at run time and use it in functions and scripts, such as in a function that displays the current directory in the PowerShell prompt.</span></span>

<span data-ttu-id="bfb9b-114">您也可以使用這個 Cmdlet 來顯示位置堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-114">You can also use this cmdlet to display the locations in a location stack.</span></span> <span data-ttu-id="bfb9b-115">如需詳細資訊，請參閱 **Stack** 和 **StackName** 參數的附注和描述。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-115">For more information, see the Notes and the descriptions of the **Stack** and **StackName** parameters.</span></span>

## <span data-ttu-id="bfb9b-116">範例</span><span class="sxs-lookup"><span data-stu-id="bfb9b-116">EXAMPLES</span></span>

### <span data-ttu-id="bfb9b-117">範例1：顯示目前的磁片磁碟機位置</span><span class="sxs-lookup"><span data-stu-id="bfb9b-117">Example 1: Display your current drive location</span></span>

<span data-ttu-id="bfb9b-118">此命令會在目前的 PowerShell 磁片磁碟機中顯示您的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-118">This command displays your location in the current PowerShell drive.</span></span>

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="bfb9b-119">比方說，如果您在 `Windows` 磁片磁碟機的目錄中 `C:` ，它會顯示該目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-119">For instance, if you are in the `Windows` directory of the `C:` drive, it displays the path to that directory.</span></span>

### <span data-ttu-id="bfb9b-120">範例2：顯示不同磁片磁碟機的目前位置</span><span class="sxs-lookup"><span data-stu-id="bfb9b-120">Example 2: Display your current location for different drives</span></span>

<span data-ttu-id="bfb9b-121">此範例示範 `Get-Location` 如何使用，在不同的 PowerShell 磁片磁碟機中顯示目前的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-121">This example demonstrates the use of `Get-Location` to display your current location in different PowerShell drives.</span></span> <span data-ttu-id="bfb9b-122">`Set-Location` 用來將位置變更為不同 Psdrive 上的數個不同路徑。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-122">`Set-Location` is used to change the location to several different paths on different PSDrives.</span></span>

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### <span data-ttu-id="bfb9b-123">範例3：使用堆疊取得位置</span><span class="sxs-lookup"><span data-stu-id="bfb9b-123">Example 3: Get locations using stacks</span></span>

<span data-ttu-id="bfb9b-124">這個範例會示範如何使用的 **Stack** 和 **StackName** 參數， `Get-Location` 列出目前位置堆疊中的位置和替代的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-124">This example shows how to use the **Stack** and **StackName** parameters of `Get-Location` to list the locations in the current location stack and alternate location stacks.</span></span>

<span data-ttu-id="bfb9b-125">此 `Push-Location` Cmdlet 會用來變更為三個不同的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-125">The `Push-Location` cmdlet is used to change into three different locations.</span></span> <span data-ttu-id="bfb9b-126">第三個推送使用不同的堆疊名稱。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-126">The third push uses a different stack name.</span></span> <span data-ttu-id="bfb9b-127">的 **Stack** 參數會 `Get-Location` 顯示預設堆疊的內容。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-127">The **Stack** parameter of `Get-Location` displays the contents of the default stack.</span></span> <span data-ttu-id="bfb9b-128">的 **StackName** 參數會 `Get-Location` 顯示名為的堆疊內容 `Stack2` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-128">The **StackName** parameter of `Get-Location` displays the contents of the stack named `Stack2`.</span></span>

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### <span data-ttu-id="bfb9b-129">範例4：自訂 PowerShell 提示字元</span><span class="sxs-lookup"><span data-stu-id="bfb9b-129">Example 4: Customize the PowerShell prompt</span></span>

<span data-ttu-id="bfb9b-130">此範例說明如何自訂 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-130">This example shows how to customize the PowerShell prompt.</span></span>

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

<span data-ttu-id="bfb9b-131">定義提示的函式包含 `Get-Location` 命令，每當主控台出現提示時，就會執行此命令。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-131">The function that defines the prompt includes a `Get-Location` command, which is run whenever the prompt appears in the console.</span></span>

<span data-ttu-id="bfb9b-132">預設 PowerShell 提示字元的格式是由名為的特殊函式所定義 `prompt` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-132">The format of the default PowerShell prompt is defined by a special function named `prompt`.</span></span> <span data-ttu-id="bfb9b-133">您可以建立名為的新函式，以變更控制台中的提示 `prompt` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-133">You can change the prompt in your console by creating a new function named `prompt`.</span></span>

<span data-ttu-id="bfb9b-134">若要查看目前的提示字元函式，請輸入下列命令： `Get-Content Function:\prompt`</span><span class="sxs-lookup"><span data-stu-id="bfb9b-134">To see the current prompt function, type the following command: `Get-Content Function:\prompt`</span></span>

## <span data-ttu-id="bfb9b-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bfb9b-135">PARAMETERS</span></span>

### <span data-ttu-id="bfb9b-136">-PSDrive</span><span class="sxs-lookup"><span data-stu-id="bfb9b-136">-PSDrive</span></span>

<span data-ttu-id="bfb9b-137">取得指定之 PowerShell 磁片磁碟機中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-137">Gets the current location in the specified PowerShell drive.</span></span>

<span data-ttu-id="bfb9b-138">比方說，如果您是在 `Cert:` 磁片磁碟機中，您可以使用這個參數來尋找磁片磁碟機中的目前位置 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-138">For instance, if you are in the `Cert:` drive, you can use this parameter to find your current location in the `C:` drive.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfb9b-139">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="bfb9b-139">-PSProvider</span></span>

<span data-ttu-id="bfb9b-140">取得指定 PowerShell 提供者所支援之磁片磁碟機中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-140">Gets the current location in the drive supported by the specified PowerShell provider.</span></span>
<span data-ttu-id="bfb9b-141">如果指定的提供者支援多個磁片磁碟機，此 Cmdlet 會傳回最近存取之磁片磁碟機上的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-141">If the specified provider supports more than one drive, this cmdlet returns the location on the most recently accessed drive.</span></span>

<span data-ttu-id="bfb9b-142">例如，如果您在 `C:` 磁片磁碟機中，您可以使用此參數來尋找 PowerShell 登錄提供者之磁片磁碟機中的目前 **Registry** 位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-142">For example, if you are in the `C:` drive, you can use this parameter to find your current location in the drives of the PowerShell **Registry** provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfb9b-143">-Stack</span><span class="sxs-lookup"><span data-stu-id="bfb9b-143">-Stack</span></span>

<span data-ttu-id="bfb9b-144">指出此 Cmdlet 會顯示新增至目前位置堆疊的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-144">Indicates that this cmdlet displays the locations added to the current location stack.</span></span> <span data-ttu-id="bfb9b-145">您可以使用 Cmdlet 將位置新增至堆疊 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-145">You can add locations to stacks by using the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="bfb9b-146">若要顯示不同位置堆疊中的位置，請使用 **StackName** 參數。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-146">To display the locations in a different location stack, use the **StackName** parameter.</span></span> <span data-ttu-id="bfb9b-147">如需位置堆疊的相關資訊，請參閱 [附注](#notes)。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-147">For information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfb9b-148">-StackName</span><span class="sxs-lookup"><span data-stu-id="bfb9b-148">-StackName</span></span>

<span data-ttu-id="bfb9b-149">以字串陣列的形式指定命名的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-149">Specifies, as a string array, the named location stacks.</span></span> <span data-ttu-id="bfb9b-150">輸入一或多個位置堆疊名稱。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-150">Enter one or more location stack names.</span></span>

<span data-ttu-id="bfb9b-151">若要顯示目前位置堆疊中的位置，請使用 **stack** 參數。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-151">To display the locations in the current location stack, use the **Stack** parameter.</span></span> <span data-ttu-id="bfb9b-152">若要將位置堆疊設為目前的位置堆疊，請使用 `Set-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-152">To make a location stack the current location stack, use the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="bfb9b-153">此 Cmdlet 無法顯示未命名之預設堆疊中的位置，除非它是目前的堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-153">This cmdlet cannot display the locations in the unnamed default stack unless it is the current stack.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfb9b-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bfb9b-154">CommonParameters</span></span>

<span data-ttu-id="bfb9b-155">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bfb9b-156">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bfb9b-157">輸入</span><span class="sxs-lookup"><span data-stu-id="bfb9b-157">INPUTS</span></span>

### <span data-ttu-id="bfb9b-158">無</span><span class="sxs-lookup"><span data-stu-id="bfb9b-158">None</span></span>

<span data-ttu-id="bfb9b-159">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bfb9b-160">輸出</span><span class="sxs-lookup"><span data-stu-id="bfb9b-160">OUTPUTS</span></span>

### <span data-ttu-id="bfb9b-161">System.Management.Automation.PathInfo 或 System.Management.Automation.PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="bfb9b-161">System.Management.Automation.PathInfo or System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="bfb9b-162">如果您使用 **Stack** 或 **StackName** 參數，這個 Cmdlet 會傳回 **PathInfoStack** 物件。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-162">If you use the **Stack** or **StackName** parameters, this cmdlet returns a **PathInfoStack** object.</span></span> <span data-ttu-id="bfb9b-163">否則，它會傳回 **system.management.automation.pathinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-163">Otherwise, it returns a **PathInfo** object.</span></span>

## <span data-ttu-id="bfb9b-164">注意</span><span class="sxs-lookup"><span data-stu-id="bfb9b-164">NOTES</span></span>

<span data-ttu-id="bfb9b-165">PowerShell 支援每個進程有多個空間。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-165">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="bfb9b-166">每個運行空間都有自己的 _目前的目錄_ 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-166">Each runspace has its own _current directory_ .</span></span>
<span data-ttu-id="bfb9b-167">這與不同 `[System.Environment]::CurrentDirectory` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-167">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="bfb9b-168">呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-168">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>
<span data-ttu-id="bfb9b-169">Cmdlet 會傳回 `Get-Location` 目前 PowerShell 運行時的目前目錄。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-169">The `Get-Location` cmdlet returns the current directory of the current PowerShell runspace.</span></span>

<span data-ttu-id="bfb9b-170">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-170">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="bfb9b-171">若要列出會話中的提供者，請輸入 `Get-PSProvider` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-171">To list the providers in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="bfb9b-172">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-172">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="bfb9b-173">**PSProvider** 、 **new-psdrive** 、 **Stack** 及 **StackName** 參數互動的方式取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-173">The ways that the **PSProvider** , **PSDrive** , **Stack** , and **StackName** parameters interact depends on the provider.</span></span> <span data-ttu-id="bfb9b-174">某些組合將會導致錯誤，例如既指定磁碟機又指定未公開該磁碟機的提供者。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-174">Some combinations will result in errors, such as specifying both a drive and a provider that does not expose that drive.</span></span> <span data-ttu-id="bfb9b-175">如果未指定任何參數，此 Cmdlet 會傳回提供者的 **system.management.automation.pathinfo** 物件，其中包含目前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-175">If no parameters are specified, this cmdlet returns the **PathInfo** object for the provider that contains the current working location.</span></span>

<span data-ttu-id="bfb9b-176">堆疊是一個後進先出的清單，其中只有最近新增的專案可供存取。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-176">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span> <span data-ttu-id="bfb9b-177">將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-177">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="bfb9b-178">PowerShell 可讓您將提供者位置儲存在位置堆疊中。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-178">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="bfb9b-179">PowerShell 會建立未命名的預設位置堆疊，而且您可以建立多個命名位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-179">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="bfb9b-180">如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-180">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="bfb9b-181">根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-181">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="bfb9b-182">若要管理位置堆疊，請使用 PowerShell `*-Location` Cmdlet，如下所示。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-182">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows.</span></span>

- <span data-ttu-id="bfb9b-183">若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-183">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="bfb9b-184">若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-184">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="bfb9b-185">若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-185">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="bfb9b-186">若要顯示命名位置堆疊中的位置，請使用 Cmdlet 的 **StackName** 參數 `Get-Location` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-186">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="bfb9b-187">若要建立新的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-187">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span>
  <span data-ttu-id="bfb9b-188">如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-188">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="bfb9b-189">若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-189">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="bfb9b-190">未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-190">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="bfb9b-191">如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用此 Cmdlet 來顯示未命名堆疊中的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-191">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use this cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="bfb9b-192">若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$null` 或 () 的空字串 `""` 。</span><span class="sxs-lookup"><span data-stu-id="bfb9b-192">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="bfb9b-193">相關連結</span><span class="sxs-lookup"><span data-stu-id="bfb9b-193">RELATED LINKS</span></span>

[<span data-ttu-id="bfb9b-194">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="bfb9b-194">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="bfb9b-195">Push-Location</span><span class="sxs-lookup"><span data-stu-id="bfb9b-195">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="bfb9b-196">Set-Location</span><span class="sxs-lookup"><span data-stu-id="bfb9b-196">Set-Location</span></span>](Set-Location.md)
