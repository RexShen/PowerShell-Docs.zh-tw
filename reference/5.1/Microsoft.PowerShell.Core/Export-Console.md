---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202316"
---
# <span data-ttu-id="8e3d8-103">Export-Console</span><span class="sxs-lookup"><span data-stu-id="8e3d8-103">Export-Console</span></span>

## <span data-ttu-id="8e3d8-104">概要</span><span class="sxs-lookup"><span data-stu-id="8e3d8-104">SYNOPSIS</span></span>
<span data-ttu-id="8e3d8-105">將目前工作階段中的嵌入式管理單元名稱匯出到主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-105">Exports the names of snap-ins in the current session to a console file.</span></span>

## <span data-ttu-id="8e3d8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8e3d8-106">SYNTAX</span></span>

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8e3d8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8e3d8-107">DESCRIPTION</span></span>
<span data-ttu-id="8e3d8-108">**匯出主控台** Cmdlet 會將目前會話中 Windows PowerShell 嵌入式管理單元的名稱匯出至 Windows PowerShell 主控台檔案 (. console01.psc1) 。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-108">The **Export-Console** cmdlet exports the names of the Windows PowerShell snap-ins in the current session to a Windows PowerShell console file (.psc1).</span></span>
<span data-ttu-id="8e3d8-109">您可以使用這個 Cmdlet 來儲存嵌入式管理單元，以供未來的工作階段使用。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-109">You can use this cmdlet to save the snap-ins for use in future sessions.</span></span>

<span data-ttu-id="8e3d8-110">若要將 console01.psc1 主控台檔案中的嵌入式管理單元新增至會話，請使用 Cmd.exe 或另一個 Windows PowerShell 會話，在命令列啟動 Windows PowerShell ( # A0) ，然後使用 Powershell.exe 的 *PSConsoleFile* 參數來指定主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-110">To add the snap-ins in the .psc1 console file to a session, start Windows PowerShell (Powershell.exe) at the command line by using Cmd.exe or another Windows PowerShell session, and then use the *PSConsoleFile* parameter of Powershell.exe to specify the console file.</span></span>

<span data-ttu-id="8e3d8-111">如需有關 Windows PowerShell 嵌入式管理單元的詳細資訊，請參閱 about_PSSnapins。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-111">For more information about Windows PowerShell snap-ins, see about_PSSnapins.</span></span>

## <span data-ttu-id="8e3d8-112">範例</span><span class="sxs-lookup"><span data-stu-id="8e3d8-112">EXAMPLES</span></span>

### <span data-ttu-id="8e3d8-113">範例1：匯出目前會話中嵌入式管理單元的名稱</span><span class="sxs-lookup"><span data-stu-id="8e3d8-113">Example 1: Export the names of snap-ins in the current session</span></span>

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

<span data-ttu-id="8e3d8-114">此命令會將目前會話中 Windows PowerShell 嵌入式管理單元的名稱，匯出至 Windows PowerShell 安裝資料夾 $pshome 的 [主控台] 資料夾中的 Consoles1.psc1. console01.psc1 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-114">This command exports the names of Windows PowerShell snap-ins in the current session to the ConsoleS1.psc1 file in the Consoles folder of the Windows PowerShell installation folder, $pshome.</span></span>

### <span data-ttu-id="8e3d8-115">範例2：將嵌入式管理單元的名稱匯出至最新的主控台檔案</span><span class="sxs-lookup"><span data-stu-id="8e3d8-115">Example 2: Export the names of snap-ins to the most recent console file</span></span>

```
PS C:\> Export-Console
```

<span data-ttu-id="8e3d8-116">此命令會將 Windows PowerShell 嵌入式管理單元名稱，從目前工作階段匯出到目前工作階段中最近使用的 Windows PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-116">This command exports the names of Windows PowerShell snap-ins from current session to the Windows PowerShell console file that was most recently used in the current session.</span></span>
<span data-ttu-id="8e3d8-117">它會覆寫先前的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-117">It overwrites the previous file contents.</span></span>

<span data-ttu-id="8e3d8-118">如果您未在目前工作階段期間匯出主控台檔案，會提示您同意繼續進行，並提示您輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-118">If you have not exported a console file during the current session, you are prompted for permission to continue and then prompted for a file name.</span></span>

### <span data-ttu-id="8e3d8-119">範例3：新增嵌入式管理單元並匯出嵌入式管理單元的名稱</span><span class="sxs-lookup"><span data-stu-id="8e3d8-119">Example 3: Add a snap-in and export the names of snap-ins</span></span>

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

<span data-ttu-id="8e3d8-120">這些命令會將 NewPSSnapin Windows PowerShell 嵌入式管理單元新增到目前的工作階段、將目前工作階段中的 Windows PowerShell 嵌入式管理單元名稱匯出到主控台檔案，然後利用主控台檔案啟動 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-120">These commands add the NewPSSnapin Windows PowerShell snap-in to the current session, export the names of Windows PowerShell snap-ins in the current session to a console file, and then start a Windows PowerShell session with the console file.</span></span>

<span data-ttu-id="8e3d8-121">第一個命令使用 **PSSnapin** Cmdlet 將 NewPSSnapin 嵌入式管理單元新增至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-121">The first command uses the **Add-PSSnapin** cmdlet to add the NewPSSnapin snap-in to the current session.</span></span>
<span data-ttu-id="8e3d8-122">您也可以僅新增您系統上已註冊的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-122">You can only add Windows PowerShell snap-ins that are registered on your system.</span></span>

<span data-ttu-id="8e3d8-123">第二個命令將 Windows PowerShell 嵌入式管理單元名稱匯出到 NewPSSnapinConsole.psc1 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-123">The second command exports the Windows PowerShell snap-in names to the NewPSSnapinConsole.psc1 file.</span></span>

<span data-ttu-id="8e3d8-124">第三個命令使用 NewPSSnapinConsole.psc1 檔案來啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-124">The third command starts Windows PowerShell with the NewPSSnapinConsole.psc1 file.</span></span>
<span data-ttu-id="8e3d8-125">因為主控台檔案包含 Windows PowerShell 嵌入式管理單元名稱，嵌入式管理單元中的 Cmdlet 與提供者可用於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-125">Because the console file includes the Windows PowerShell snap-in name, the cmdlets and providers in the snap-in are available in the current session.</span></span>

### <span data-ttu-id="8e3d8-126">範例4：將嵌入式管理單元的名稱匯出到指定的位置</span><span class="sxs-lookup"><span data-stu-id="8e3d8-126">Example 4: Export names of snap-ins to a specified location</span></span>

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

<span data-ttu-id="8e3d8-127">此命令會將目前工作階段中的 Windows PowerShell 嵌入式管理單元名稱匯出到目前目錄中的 Console01.psc1 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-127">This command exports the names of the Windows PowerShell snap-ins in the current session to the Console01.psc1 file in the current directory.</span></span>

<span data-ttu-id="8e3d8-128">第二個命令在 [記事本] 中顯示 Console01.psc1 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-128">The second command displays the contents of the Console01.psc1 file in Notepad.</span></span>

### <span data-ttu-id="8e3d8-129">範例5：判斷要更新的主控台檔案</span><span class="sxs-lookup"><span data-stu-id="8e3d8-129">Example 5: Determine the console file to update</span></span>

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

<span data-ttu-id="8e3d8-130">此範例示範如何使用 $ConsoleFileName 自動變數來判斷當您使用不含 *路徑* 參數值的 **Export 主控台** 時，將會更新的主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-130">This example shows how to use the $ConsoleFileName automatic variable to determine the console file that will be updated if you use **Export-Console** without a *Path* parameter value.</span></span>

<span data-ttu-id="8e3d8-131">第一個命令使用 PowerShell.exe 的 *PSConsoleFile* 參數，以 console01.psc1 console01.psc1 檔案開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-131">The first command uses the *PSConsoleFile* parameter of PowerShell.exe to open Windows PowerShell with the Console01.psc1 file.</span></span>

<span data-ttu-id="8e3d8-132">第二個命令會使用 **PSSnapin** Cmdlet，將 MySnapin Windows PowerShell 嵌入式管理單元新增至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-132">The second command uses the **Add-PSSnapin** cmdlet to add the MySnapin Windows PowerShell snap-in to the current session.</span></span>

<span data-ttu-id="8e3d8-133">第三個命令使用 **匯出主控台** Cmdlet 將會話中所有 Windows PowerShell 嵌入式管理單元的名稱匯出至 newconsole.psc1. console01.psc1 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-133">The third command uses the **Export-Console** cmdlet to export the names of all the Windows PowerShell snap-ins in the session to the NewConsole.psc1 file.</span></span>

<span data-ttu-id="8e3d8-134">第四個命令會顯示 $ConsoleFileName 變數。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-134">The fourth command displays the $ConsoleFileName variable.</span></span>
<span data-ttu-id="8e3d8-135">它包含最近使用的主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-135">It contains the most recently used console file.</span></span>
<span data-ttu-id="8e3d8-136">範例輸出顯示 NewConsole.ps1 為最近使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-136">The sample output shows that NewConsole.ps1 is the most recently used file.</span></span>

<span data-ttu-id="8e3d8-137">第五個命令將 SnapIn03 新增至目前主控台。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-137">The fifth command adds SnapIn03 to the current console.</span></span>

<span data-ttu-id="8e3d8-138">第六個命令使用不含 *Path* 參數的 **Export 主控台** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-138">The sixth command uses the **Export-Console** cmdlet without a *Path* parameter.</span></span>
<span data-ttu-id="8e3d8-139">此命令會將目前工作階段中所有 Windows PowerShell 嵌入式管理單元名稱匯出到最近使用的檔案 NewConsole.psc1。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-139">This command exports the names of all the Windows PowerShell snap-ins in the current session to the most recently used file, NewConsole.psc1.</span></span>

## <span data-ttu-id="8e3d8-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8e3d8-140">PARAMETERS</span></span>

### <span data-ttu-id="8e3d8-141">-Force</span><span class="sxs-lookup"><span data-stu-id="8e3d8-141">-Force</span></span>
<span data-ttu-id="8e3d8-142">指出此 Cmdlet 會覆寫主控台檔案中的資料而不發出警告，即使檔案具有唯讀屬性也一樣。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-142">Indicates that this cmdlet overwrites the data in a console file without warning, even if the file has the read-only attribute.</span></span>
<span data-ttu-id="8e3d8-143">當命令完成時，唯讀屬性已變更且不會重設。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-143">The read-only attribute is changed and is not reset when the command finishes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e3d8-144">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="8e3d8-144">-NoClobber</span></span>
<span data-ttu-id="8e3d8-145">指出此 Cmdlet 不會覆寫現有的主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-145">Indicates that this cmdlet does not overwrite  an existing console file.</span></span>
<span data-ttu-id="8e3d8-146">根據預設，如果檔案發生在指定的路徑中，則 **匯出主控台** 會覆寫檔案而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-146">By default, if a file occurs in the specified path, **Export-Console** overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e3d8-147">-Path</span><span class="sxs-lookup"><span data-stu-id="8e3d8-147">-Path</span></span>
<span data-ttu-id="8e3d8-148">指定主控台檔案 (\*.psc1) 的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-148">Specifies a path and file name for the console file (\*.psc1).</span></span>
<span data-ttu-id="8e3d8-149">輸入選擇性的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-149">Enter an optional path and name.</span></span>
<span data-ttu-id="8e3d8-150">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-150">Wildcard characters are not permitted.</span></span>

<span data-ttu-id="8e3d8-151">如果您只指定檔案名，則 [ **匯出主控台** ] 會在目前的目錄中建立具有該名稱和副檔名為 console01.psc1 的檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-151">If you specify only a file name, **Export-Console** creates a file that has that name and the .psc1 file name extension in the current directory.</span></span>

<span data-ttu-id="8e3d8-152">除非您已使用 *PSConsoleFile* 參數開啟 Windows PowerShell，或在目前的會話期間匯出主控台檔案，否則此為必要參數。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-152">This parameter is required unless you have opened Windows PowerShell with the *PSConsoleFile* parameter or exported a console file during the current session.</span></span>
<span data-ttu-id="8e3d8-153">當您使用 *NoClobber* 參數來防止目前的主控台檔案遭到覆寫時，也需要使用此參數。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-153">It is also required when you use the *NoClobber* parameter to prevent the current console file from being overwritten.</span></span>

<span data-ttu-id="8e3d8-154">如果您省略此參數，則 **匯出主控台** 會覆寫此會話中最近使用的主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-154">If you omit this parameter, **Export-Console** overwrites the console file that was used most recently in this session.</span></span>
<span data-ttu-id="8e3d8-155">最近使用的主控台檔案的路徑會儲存在 $ConsoleFileName 自動變數的值中。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-155">The path of the most recently used console file is stored in the value of the $ConsoleFileName automatic variable.</span></span>
<span data-ttu-id="8e3d8-156">如需詳細資訊，請參閱 about_Automatic_Variables。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-156">For more information, see about_Automatic_Variables.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8e3d8-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8e3d8-157">-Confirm</span></span>
<span data-ttu-id="8e3d8-158">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-158">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e3d8-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8e3d8-159">-WhatIf</span></span>
<span data-ttu-id="8e3d8-160">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8e3d8-161">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-161">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8e3d8-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8e3d8-162">CommonParameters</span></span>
<span data-ttu-id="8e3d8-163">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8e3d8-164">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8e3d8-165">輸入</span><span class="sxs-lookup"><span data-stu-id="8e3d8-165">INPUTS</span></span>

### <span data-ttu-id="8e3d8-166">System.String</span><span class="sxs-lookup"><span data-stu-id="8e3d8-166">System.String</span></span>
<span data-ttu-id="8e3d8-167">您可以使用管線將路徑字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-167">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="8e3d8-168">輸出</span><span class="sxs-lookup"><span data-stu-id="8e3d8-168">OUTPUTS</span></span>

### <span data-ttu-id="8e3d8-169">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="8e3d8-169">System.IO.FileInfo</span></span>
<span data-ttu-id="8e3d8-170">此 Cmdlet 會建立包含匯出別名的檔案。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-170">This cmdlet creates a file that contains the exported aliases.</span></span>

## <span data-ttu-id="8e3d8-171">注意</span><span class="sxs-lookup"><span data-stu-id="8e3d8-171">NOTES</span></span>

* <span data-ttu-id="8e3d8-172">當使用主控台檔案 (.psc1) 來啟動工作階段，主控台檔案的名稱會自動儲存在 $ConsoleFileName 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-172">When a console file (.psc1) is used to start the session, the name of the console file is automatically stored in the $ConsoleFileName automatic variable.</span></span> <span data-ttu-id="8e3d8-173">當您使用 **Export 主控台** 的 *Path* 參數指定新的主控台檔案時，會更新 $ConsoleFileName 的值。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-173">The value of $ConsoleFileName is updated when you use the *Path* parameter of **Export-Console** to specify a new console file.</span></span> <span data-ttu-id="8e3d8-174">未使用任何主控台檔案時，$ConsoleFileName ($Null) 沒有任何值。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-174">When no console file is used, $ConsoleFileName has no value ($Null).</span></span>

  <span data-ttu-id="8e3d8-175">如果要在新的工作階段中使用 Windows PowerShell 主控台檔案，請使用使用下列語法啟動 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="8e3d8-175">To use a Windows PowerShell console file in a new session, use the following syntax to start Windows PowerShell:</span></span>

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  <span data-ttu-id="8e3d8-176">您也可以將 Add-PSSnapin 命令新增到 Windows PowerShell 設定檔，儲存 Windows PowerShell 嵌入式管理單元以供未來工作階段使用。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-176">You can also save Windows PowerShell snap-ins for future sessions by adding an Add-PSSnapin command to your Windows PowerShell profile.</span></span>
<span data-ttu-id="8e3d8-177">如需詳細資訊，請參閱 about_Profiles。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-177">For more information, see about_Profiles.</span></span>


## <span data-ttu-id="8e3d8-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="8e3d8-178">RELATED LINKS</span></span>

[<span data-ttu-id="8e3d8-179">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8e3d8-179">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="8e3d8-180">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8e3d8-180">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="8e3d8-181">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="8e3d8-181">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
