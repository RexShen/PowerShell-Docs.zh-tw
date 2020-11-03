---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: ea57ae0b3affcbe060b74c6cc21e6df6d50e50ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204863"
---
# <span data-ttu-id="db2bb-103">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="db2bb-103">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="db2bb-104">概要</span><span class="sxs-lookup"><span data-stu-id="db2bb-104">SYNOPSIS</span></span>
<span data-ttu-id="db2bb-105">驗證工作階段設定檔中的索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="db2bb-105">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="db2bb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db2bb-106">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="db2bb-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="db2bb-107">DESCRIPTION</span></span>

<span data-ttu-id="db2bb-108">此 Cmdlet 會驗證會話設定檔包含有效的金鑰，而且值的類型是正確的。</span><span class="sxs-lookup"><span data-stu-id="db2bb-108">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="db2bb-109">對於列舉的值，此 Cmdlet 會驗證指定的值是否有效。</span><span class="sxs-lookup"><span data-stu-id="db2bb-109">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="db2bb-110">`$True`如果檔案通過所有測試，則 Cmdlet 會傳回， `$False` 否則會傳回。</span><span class="sxs-lookup"><span data-stu-id="db2bb-110">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="db2bb-111">若要尋找任何錯誤，請使用 **Verbose** 參數。</span><span class="sxs-lookup"><span data-stu-id="db2bb-111">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="db2bb-112">`Test-PSSessionConfigurationFile` 驗證會話設定檔，例如 Cmdlet 所建立的設定檔 `New-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="db2bb-112">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="db2bb-113">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="db2bb-113">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="db2bb-114">如需會話設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="db2bb-114">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="db2bb-115">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="db2bb-115">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="db2bb-116">範例</span><span class="sxs-lookup"><span data-stu-id="db2bb-116">EXAMPLES</span></span>

### <span data-ttu-id="db2bb-117">範例 1：測試工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="db2bb-117">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="db2bb-118">範例 2：測試工作階段設定的工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="db2bb-118">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="db2bb-119">在此範例中，我們會測試 **受限制** 會話設定中使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="db2bb-119">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="db2bb-120">**Path** 參數的值是命令的結果 `Get-PSSessionConfiguration` ，此命令會取得 **受限制** 的會話設定。</span><span class="sxs-lookup"><span data-stu-id="db2bb-120">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="db2bb-121">工作階段設定檔的路徑儲存在工作階段設定之 **ConfigFilePath** 屬性的值中。</span><span class="sxs-lookup"><span data-stu-id="db2bb-121">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="db2bb-122">範例 3：測試所有工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="db2bb-122">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="db2bb-123">此範例中的函數會測試本機電腦上的所有會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="db2bb-123">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="db2bb-124">函數會使用 `Get-PSSessionConfiguration` Cmdlet 來取得所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="db2bb-124">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="db2bb-125">迴圈內的程式碼會 `ForEach-Object` 顯示檔案路徑，並測試每個會話設定。</span><span class="sxs-lookup"><span data-stu-id="db2bb-125">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

<span data-ttu-id="db2bb-126">工作階段設定的 **ConfigFilePath** 屬性包含在工作階段設定中使用之工作階段設定檔的路徑 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="db2bb-126">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="db2bb-127">如果已填入 **ConfigFilePath** 屬性的值 (為 True)，此命令會取得 (印出) **ConfigFilePath** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="db2bb-127">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="db2bb-128">然後，它會使用 `Test-PSSessionConfigurationFile` Cmdlet 來測試 **ConfigFilePath** 值中的檔案。</span><span class="sxs-lookup"><span data-stu-id="db2bb-128">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="db2bb-129">當檔案無法通過測試時， **Verbose** 參數會傳回檔案錯誤。</span><span class="sxs-lookup"><span data-stu-id="db2bb-129">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="db2bb-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db2bb-130">PARAMETERS</span></span>

### <span data-ttu-id="db2bb-131">-Path</span><span class="sxs-lookup"><span data-stu-id="db2bb-131">-Path</span></span>

<span data-ttu-id="db2bb-132">指定會話設定檔的路徑和檔案名 (. .pssc) 。</span><span class="sxs-lookup"><span data-stu-id="db2bb-132">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="db2bb-133">若省略路徑，則預設為目前資料夾。</span><span class="sxs-lookup"><span data-stu-id="db2bb-133">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="db2bb-134">支援使用萬用字元，但它們必須解析為單一檔案。</span><span class="sxs-lookup"><span data-stu-id="db2bb-134">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="db2bb-135">您也可以使用管線將會話設定檔路徑傳送至 `Test-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="db2bb-135">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="db2bb-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db2bb-136">CommonParameters</span></span>

<span data-ttu-id="db2bb-137">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="db2bb-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db2bb-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="db2bb-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db2bb-139">輸入</span><span class="sxs-lookup"><span data-stu-id="db2bb-139">INPUTS</span></span>

### <span data-ttu-id="db2bb-140">System.String</span><span class="sxs-lookup"><span data-stu-id="db2bb-140">System.String</span></span>

<span data-ttu-id="db2bb-141">您可以使用管線將會話設定檔路徑傳送至 `Test-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="db2bb-141">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="db2bb-142">輸出</span><span class="sxs-lookup"><span data-stu-id="db2bb-142">OUTPUTS</span></span>

### <span data-ttu-id="db2bb-143">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="db2bb-143">System.Boolean</span></span>

## <span data-ttu-id="db2bb-144">注意</span><span class="sxs-lookup"><span data-stu-id="db2bb-144">NOTES</span></span>

## <span data-ttu-id="db2bb-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="db2bb-145">RELATED LINKS</span></span>

[<span data-ttu-id="db2bb-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db2bb-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="db2bb-147">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db2bb-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="db2bb-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db2bb-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="db2bb-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="db2bb-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="db2bb-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="db2bb-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="db2bb-151">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db2bb-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="db2bb-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db2bb-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="db2bb-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="db2bb-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="db2bb-154">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="db2bb-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="db2bb-155">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="db2bb-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="db2bb-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="db2bb-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="db2bb-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="db2bb-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
