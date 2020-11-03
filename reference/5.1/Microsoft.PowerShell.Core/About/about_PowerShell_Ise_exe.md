---
description: 說明如何使用 PowerShell_Ise.exe 命令列工具。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207956"
---
# <a name="about-powershell-iseexe"></a><span data-ttu-id="00093-104">關於 PowerShell Ise.exe</span><span class="sxs-lookup"><span data-stu-id="00093-104">About PowerShell Ise.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="00093-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="00093-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="00093-106">說明如何使用 PowerShell_Ise.exe 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="00093-106">Explains how to use the PowerShell_Ise.exe command-line tool.</span></span>

## <a name="long-description"></a><span data-ttu-id="00093-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="00093-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="00093-108">PowerShell_Ise.exe 啟動 Windows PowerShell 整合式腳本環境 (ISE) 會話。</span><span class="sxs-lookup"><span data-stu-id="00093-108">PowerShell_Ise.exe starts a Windows PowerShell Integrated Scripting Environment (ISE) session.</span></span> <span data-ttu-id="00093-109">您可以在 Cmd.exe 和 Windows PowerShell 中執行它。</span><span class="sxs-lookup"><span data-stu-id="00093-109">You can run it in Cmd.exe and in Windows PowerShell.</span></span>

<span data-ttu-id="00093-110">若要執行 PowerShell_ISE.exe，請輸入 PowerShell_ISE.exe、PowerShell_ISE 或 ISE。</span><span class="sxs-lookup"><span data-stu-id="00093-110">To run PowerShell_ISE.exe, type PowerShell_ISE.exe, PowerShell_ISE, or ISE.</span></span>

## <a name="syntax"></a><span data-ttu-id="00093-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="00093-111">SYNTAX</span></span>

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a><span data-ttu-id="00093-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00093-112">PARAMETERS</span></span>

### <a name="-file"></a><span data-ttu-id="00093-113">-File</span><span class="sxs-lookup"><span data-stu-id="00093-113">-File</span></span>

<span data-ttu-id="00093-114">在 Windows PowerShell ISE 中開啟指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="00093-114">Opens the specified files in Windows PowerShell ISE.</span></span> <span data-ttu-id="00093-115">參數名稱 ( "-File" ) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="00093-115">The parameter name ("-File") is optional.</span></span> <span data-ttu-id="00093-116">若要列出一個以上的檔案，請輸入一個以引號括住的文字字串。</span><span class="sxs-lookup"><span data-stu-id="00093-116">To list more than one file, enter one text string enclosed in quotation marks.</span></span> <span data-ttu-id="00093-117">使用逗號來分隔字串內的檔案名。</span><span class="sxs-lookup"><span data-stu-id="00093-117">Use commas to separate the file names within the string.</span></span>

<span data-ttu-id="00093-118">例如：</span><span class="sxs-lookup"><span data-stu-id="00093-118">For example:</span></span>

<span data-ttu-id="00093-119">PowerShell_ISE-File "File1.ps1，File2.ps1，File3.xml"。</span><span class="sxs-lookup"><span data-stu-id="00093-119">PowerShell_ISE -File "File1.ps1,File2.ps1,File3.xml".</span></span>

<span data-ttu-id="00093-120">Windows PowerShell 中允許檔案名之間的空格，但其他程式可能無法正確地解讀，例如 Cmd.exe。</span><span class="sxs-lookup"><span data-stu-id="00093-120">Spaces between the file names are permitted in Windows PowerShell, but might not be interpreted correctly by other programs, such as Cmd.exe.</span></span>

<span data-ttu-id="00093-121">您可以使用這個參數來開啟任何文字檔，包括 Windows PowerShell 腳本檔案和 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="00093-121">You can use this parameter to open any text file, including Windows PowerShell script files and XML files.</span></span>

### <a name="-mta"></a><span data-ttu-id="00093-122">-Mta</span><span class="sxs-lookup"><span data-stu-id="00093-122">-Mta</span></span>

<span data-ttu-id="00093-123">使用多執行緒的單元開始 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="00093-123">Starts Windows PowerShell ISE using a multi-threaded apartment.</span></span> <span data-ttu-id="00093-124">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="00093-124">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="00093-125">單一執行緒的單元 (STA) 為預設值。</span><span class="sxs-lookup"><span data-stu-id="00093-125">Single-threaded apartment (STA) is the default.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="00093-126">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="00093-126">-NoProfile</span></span>

<span data-ttu-id="00093-127">不會執行 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="00093-127">Does not run Windows PowerShell profiles.</span></span> <span data-ttu-id="00093-128">根據預設，Windows PowerShell 設定檔會在每個會話中執行。</span><span class="sxs-lookup"><span data-stu-id="00093-128">By default, Windows PowerShell profiles are run in every session.</span></span>

<span data-ttu-id="00093-129">當您要撰寫共用內容（例如，將在具有不同設定檔的系統上執行的函式和腳本）時，建議使用此參數。</span><span class="sxs-lookup"><span data-stu-id="00093-129">This parameter is recommended when you are writing shared content, such as functions and scripts that will be run on systems with different profiles.</span></span>
<span data-ttu-id="00093-130">如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="00093-130">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="-help---"></a><span data-ttu-id="00093-131">-Help-?,/？</span><span class="sxs-lookup"><span data-stu-id="00093-131">-Help -?, /?</span></span>

<span data-ttu-id="00093-132">顯示 PowerShell_ISE.exe 的說明。</span><span class="sxs-lookup"><span data-stu-id="00093-132">Displays help for PowerShell_ISE.exe.</span></span>

## <a name="examples"></a><span data-ttu-id="00093-133">範例</span><span class="sxs-lookup"><span data-stu-id="00093-133">EXAMPLES</span></span>

<span data-ttu-id="00093-134">這些命令會啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="00093-134">These commands start Windows PowerShell ISE.</span></span> <span data-ttu-id="00093-135">這些命令是相等的，可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="00093-135">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

<span data-ttu-id="00093-136">這些命令會在 Windows PowerShell ISE 中開啟 Get-Profile.ps1 腳本。</span><span class="sxs-lookup"><span data-stu-id="00093-136">These commands open the Get-Profile.ps1 script in Windows PowerShell ISE.</span></span>
<span data-ttu-id="00093-137">這些命令是相等的，可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="00093-137">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

<span data-ttu-id="00093-138">此命令會在 Windows PowerShell ISE 中開啟 Get-Backups.ps1 和 Get-BackupInstance.ps1 腳本。</span><span class="sxs-lookup"><span data-stu-id="00093-138">This command opens the Get-Backups.ps1 and Get-BackupInstance.ps1 scripts in Windows PowerShell ISE.</span></span> <span data-ttu-id="00093-139">若要開啟一個以上的檔案，請使用逗號來分隔檔案名，並以引號括住整個檔案名。</span><span class="sxs-lookup"><span data-stu-id="00093-139">To open more than one file, use a comma to separate the file names and enclose the entire file name value in quotation marks.</span></span>

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

<span data-ttu-id="00093-140">此命令會 Windows PowerShell ISE 沒有設定檔的情況下啟動。</span><span class="sxs-lookup"><span data-stu-id="00093-140">This command starts Windows PowerShell ISE with no profiles.</span></span>

```
PS C:> ISE -NoProfile
```

<span data-ttu-id="00093-141">此命令會取得 PowerShell_ISE.exe 的說明。</span><span class="sxs-lookup"><span data-stu-id="00093-141">This command gets help for PowerShell_ISE.exe.</span></span>

```
PS C:> ISE -help
```

## <a name="see-also"></a><span data-ttu-id="00093-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00093-142">SEE ALSO</span></span>

[<span data-ttu-id="00093-143">about_PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="00093-143">about_PowerShell.exe</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="00093-144">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="00093-144">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)

[<span data-ttu-id="00093-145">Windows PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="00093-145">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
