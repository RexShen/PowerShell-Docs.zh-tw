---
description: 描述會話設定中使用的會話設定檔， (也稱為「端點」 ) 來定義使用會話設定之會話的環境。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 45c8a6e0ba8478e0a49cb287cd4311d7556a42ea
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206707"
---
# <a name="about-session-configuration-files"></a><span data-ttu-id="fa556-104">關於會話設定檔</span><span class="sxs-lookup"><span data-stu-id="fa556-104">About Session Configuration Files</span></span>

## <a name="short-description"></a><span data-ttu-id="fa556-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="fa556-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="fa556-106">描述會話設定中使用的會話設定檔， (也稱為「端點」 ) 來定義使用會話設定之會話的環境。</span><span class="sxs-lookup"><span data-stu-id="fa556-106">Describes session configuration files, which are used in a session configuration (also known as an "endpoint") to define the environment of sessions that use the session configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="fa556-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="fa556-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="fa556-108">「會話設定檔」是副檔名為 .pssc 的文字檔，其中包含會話設定屬性和值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="fa556-108">A "session configuration file" is a text file with a .pssc file name extension that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="fa556-109">您可以使用會話設定檔來設定會話設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="fa556-109">You can use a session configuration file to set the properties of a session configuration.</span></span> <span data-ttu-id="fa556-110">這麼做會定義使用該會話設定之任何 PowerShell 會話的環境。</span><span class="sxs-lookup"><span data-stu-id="fa556-110">Doing so defines the environment of any PowerShell sessions that use that session configuration.</span></span>

<span data-ttu-id="fa556-111">會話設定檔可讓您輕鬆地建立自訂會話設定，而不需要使用複雜的 c # 元件或腳本。</span><span class="sxs-lookup"><span data-stu-id="fa556-111">Session configuration files make it easy to create custom session configurations without using complex C# assemblies or scripts.</span></span>

<span data-ttu-id="fa556-112">「會話設定」或「端點」是本機電腦設定的集合，可決定使用者可在電腦上建立會話的專案;使用者可以在這些會話中執行哪些命令;以及會話是否應以特殊許可權虛擬帳戶的形式執行。</span><span class="sxs-lookup"><span data-stu-id="fa556-112">A "session configuration" or "endpoint" is a collection of local computer settings that determine such things as which users can create sessions on the computer; which commands users can run in those sessions; and whether the session should run as a privileged virtual account.</span></span> <span data-ttu-id="fa556-113">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="fa556-113">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

<span data-ttu-id="fa556-114">會話設定是在 Windows PowerShell 2.0 中引進，而會話設定檔是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="fa556-114">Session configurations were introduced in Windows PowerShell 2.0, and session configuration files were introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="fa556-115">您必須使用 Windows PowerShell 3.0，將會話設定檔包含在會話設定中。</span><span class="sxs-lookup"><span data-stu-id="fa556-115">You must use Windows PowerShell 3.0 to include a session configuration file in a session configuration.</span></span> <span data-ttu-id="fa556-116">不過，Windows PowerShell 2.0 (和更新版本) 的使用者會受到會話設定中的設定影響。</span><span class="sxs-lookup"><span data-stu-id="fa556-116">However, users of Windows PowerShell 2.0 (and later) are affected by the settings in the session configuration.</span></span>

## <a name="creating-custom-sessions"></a><span data-ttu-id="fa556-117">建立自訂會話</span><span class="sxs-lookup"><span data-stu-id="fa556-117">Creating Custom Sessions</span></span>

<span data-ttu-id="fa556-118">您可以在會話設定中指定會話屬性，以自訂 PowerShell 會話的許多功能。</span><span class="sxs-lookup"><span data-stu-id="fa556-118">You can customize many features of a PowerShell session by specifying session properties in a session configuration.</span></span> <span data-ttu-id="fa556-119">您可以撰寫可定義自訂執行時間的 c # 程式來自訂會話，也可以使用會話設定檔來定義使用會話設定建立之會話的屬性。</span><span class="sxs-lookup"><span data-stu-id="fa556-119">You can customize a session by writing a C# program that defines a custom runspace, or you can use a session configuration file to define the properties of sessions created by using the session configuration.</span></span> <span data-ttu-id="fa556-120">一般來說，使用會話設定檔比撰寫 c # 程式更容易。</span><span class="sxs-lookup"><span data-stu-id="fa556-120">As a general rule, it is easier to use the session configuration file than to write a C# program.</span></span>

<span data-ttu-id="fa556-121">您可以使用會話設定檔來建立專案，例如高度信任的使用者的完整運作會話;允許存取基本的已鎖定會話;專為特定而設計的會話，其中只包含這些工作所需的模組;和不具特殊許可權的使用者只能以特殊許可權帳戶執行特定命令的會話。</span><span class="sxs-lookup"><span data-stu-id="fa556-121">You can use a session configuration file to create items such as fully-functioning sessions for highly trusted users; locked-down sessions that allow minimal access; sessions designed for particular and that contain only the modules required for those tasks; and sessions where unprivileged users can only run specific commands as a privileged account.</span></span>

<span data-ttu-id="fa556-122">此外，您可以管理會話的使用者是否可以使用 PowerShell 語言專案（例如腳本區塊），或是否只能執行命令。</span><span class="sxs-lookup"><span data-stu-id="fa556-122">In addition to that, you can manage whether users of the session can use PowerShell language elements such as script blocks, or whether they can only run commands.</span></span> <span data-ttu-id="fa556-123">您可以管理可在會話中執行的 PowerShell 使用者版本;管理哪些模組會匯入到會話;以及管理哪些 Cmdlet、函式和別名會話使用者可以執行。</span><span class="sxs-lookup"><span data-stu-id="fa556-123">You can manage the version of PowerShell users can run in the session; manage which modules are imported into the session; and manage which cmdlets, functions, and aliases session users can run.</span></span> <span data-ttu-id="fa556-124">使用 [RoleDefinitions] 欄位時，您可以根據群組成員資格，為使用者的會話提供不同的功能。</span><span class="sxs-lookup"><span data-stu-id="fa556-124">When using the RoleDefinitions field, you can give users different capabilities in the session based on group membership.</span></span>

<span data-ttu-id="fa556-125">如需有關 RoleDefinitions 以及如何定義此值的詳細資訊，請參閱 New-PSRoleCapabilityFile Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="fa556-125">For more information about RoleDefinitions and how to define this Value, see the help topic for the New-PSRoleCapabilityFile Cmdlet.</span></span>

## <a name="creating-a-session-configuration-file"></a><span data-ttu-id="fa556-126">建立會話設定檔</span><span class="sxs-lookup"><span data-stu-id="fa556-126">Creating a Session Configuration File</span></span>

<span data-ttu-id="fa556-127">若要建立會話設定檔，最簡單的方式是使用 New-PSSessionConfigurationFile Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa556-127">The easiest way to create a session configuration file is by using the New-PSSessionConfigurationFile cmdlet.</span></span> <span data-ttu-id="fa556-128">此 Cmdlet 會產生使用正確語法和格式的檔案，並自動驗證許多配置檔案屬性值。</span><span class="sxs-lookup"><span data-stu-id="fa556-128">This cmdlet generates a file that uses the correct syntax and format, and that automatically verifies many of the configuration file property values.</span></span>

<span data-ttu-id="fa556-129">如需可在會話設定檔中設定之屬性的詳細說明，請參閱 New-PSSessionConfigurationFile Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="fa556-129">For detailed descriptions of the properties that you can set in a session configuration file, see the help topic for the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="fa556-130">下列命令會建立使用預設值的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-130">The following command creates a session configuration file that uses the default values.</span></span> <span data-ttu-id="fa556-131">產生的設定檔案只會使用預設值，因為 Path 參數以外的參數 (指定檔案路徑) 包含：</span><span class="sxs-lookup"><span data-stu-id="fa556-131">The resulting configuration file uses only the default values because no parameters other than the Path parameter (which specifies the file path) are included:</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

<span data-ttu-id="fa556-132">若要在您的預設文字編輯器中查看新的設定檔，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="fa556-132">To view the new configuration file in your default text editor, use the following command:</span></span>

```powershell
Invoke-Item -Path .\Defaults.pssc
```

<span data-ttu-id="fa556-133">若要建立會話的會話設定，讓使用者可以在其中執行命令，但不使用 PowerShell 語言的其他元素，請輸入：</span><span class="sxs-lookup"><span data-stu-id="fa556-133">To create a session configuration for sessions in which user can run commands, but not use other elements of the PowerShell language, type:</span></span>

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="fa556-134">在上述命令中，將 LanguageMode 參數設定為 NoLanguage，可防止使用者進行撰寫或執行腳本，或使用變數等操作。</span><span class="sxs-lookup"><span data-stu-id="fa556-134">In the preceding command, setting the LanguageMode parameter to NoLanguage prevents users from doing such things as writing or running scripts, or using variables.</span></span>

<span data-ttu-id="fa556-135">若要建立會話的會話設定，讓使用者只能使用 Get Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="fa556-135">To create a session configuration for sessions in which users can use only Get cmdlets, type:</span></span>

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

<span data-ttu-id="fa556-136">在上述範例中，將 VisibleCmdlets 參數設定為 Get-help，會將使用者限制為名稱開頭為字串值 "Get-" 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa556-136">In the preceding example, setting the VisibleCmdlets parameter to Get-\* limits users to cmdlets that have names that start with the string value "Get-".</span></span>

<span data-ttu-id="fa556-137">若要針對以特殊許可權虛擬帳戶（而非使用者認證）執行的會話建立會話設定，請輸入：</span><span class="sxs-lookup"><span data-stu-id="fa556-137">To create a session configuration for sessions that run under a privileged virtual account instead of the user's credentials, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

<span data-ttu-id="fa556-138">若要針對在角色功能檔案中指定使用者可看見之命令的會話建立會話設定，請輸入：</span><span class="sxs-lookup"><span data-stu-id="fa556-138">To create a session configuration for sessions in which the commands visible to the user are specified in a role capabilities file, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a><span data-ttu-id="fa556-139">使用會話設定檔</span><span class="sxs-lookup"><span data-stu-id="fa556-139">Using a Session Configuration File</span></span>

<span data-ttu-id="fa556-140">您可以在建立會話設定時包含會話設定檔，或新增您稍後可以將檔案新增至會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-140">You can include a session configuration file when you create a session configuration or add you can add a file to the session configuration at a later time.</span></span>

<span data-ttu-id="fa556-141">若要在建立會話設定時包含會話設定檔，請使用 Register-PSSessionConfiguration Cmdlet 的 Path 參數。</span><span class="sxs-lookup"><span data-stu-id="fa556-141">To include a session configuration file when creating a session configuration, use the Path parameter of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="fa556-142">例如，下列命令會在建立 NoLanguage 會話設定時，使用 NoLanguage. .pssc 檔案。</span><span class="sxs-lookup"><span data-stu-id="fa556-142">For example, the following command uses the NoLanguage.pssc file when it creates a NoLanguage session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="fa556-143">當新的 NoLanguage 會話啟動時，使用者將只能存取 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="fa556-143">When a new NoLanguage session starts, users will only have access to PowerShell commands.</span></span>

<span data-ttu-id="fa556-144">若要將會話設定檔新增至現有的會話設定，請使用 Set-PSSessionConfiguration Cmdlet 和 Path 參數。</span><span class="sxs-lookup"><span data-stu-id="fa556-144">To add a session configuration file to an existing session configuration, use the Set-PSSessionConfiguration cmdlet and the Path parameter.</span></span> <span data-ttu-id="fa556-145">這會影響使用指定的會話設定所建立的任何新會話。</span><span class="sxs-lookup"><span data-stu-id="fa556-145">This affects any new sessions created with the specified session configuration.</span></span> <span data-ttu-id="fa556-146">請注意，Set-PSSessionConfiguration Cmdlet 會變更會話本身，而不會修改會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-146">Note that the Set-PSSessionConfiguration cmdlet changes the session itself and does not modify the session configuration file.</span></span>

<span data-ttu-id="fa556-147">例如，下列命令會將 NoLanguage. .pssc 檔案新增至 LockedDown 會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-147">For example, the following command adds the NoLanguage.pssc file to the LockedDown session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

<span data-ttu-id="fa556-148">當使用者使用 LockedDown 會話設定來建立會話時，他們將能夠執行 Cmdlet，但他們將無法建立或使用變數、指派值或使用其他 PowerShell 語言元素。</span><span class="sxs-lookup"><span data-stu-id="fa556-148">When users use the LockedDown session configuration to create a session, they will be able to run cmdlets but they will not be able to create or use variables, assign values, or use other PowerShell language elements.</span></span>

<span data-ttu-id="fa556-149">下列命令使用 New-PSSession Cmdlet 在使用 LockedDown 會話設定的電腦 Srv01 上建立會話，並在 $s 變數中儲存會話的物件參考。</span><span class="sxs-lookup"><span data-stu-id="fa556-149">The following command uses the New-PSSession cmdlet to create a session on the computer Srv01 that uses the LockedDown session configuration, saving an object reference to the session in the $s variable.</span></span> <span data-ttu-id="fa556-150">會話設定的 ACL (存取控制清單) 會決定誰可以使用它來建立會話。</span><span class="sxs-lookup"><span data-stu-id="fa556-150">The ACL (access control list) of the session configuration determines who can use it to create a session.</span></span>

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

<span data-ttu-id="fa556-151">因為 NoLanguage 條件約束已新增至 LockedDown 會話設定，所以 LockedDown 會話中的使用者將只能執行 PowerShell 命令和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa556-151">Because the NoLanguage constraints were added to the LockedDown session configuration, users in LockedDown sessions will only be able to run PowerShell commands and cmdlets.</span></span> <span data-ttu-id="fa556-152">例如，下列兩個命令會使用 Invoke-Command Cmdlet，在 $s 變數中所參考的會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="fa556-152">For example, the following two commands use the Invoke-Command cmdlet to run commands in the session referenced in the $s variable.</span></span> <span data-ttu-id="fa556-153">第一個命令會執行 Get-UICulture Cmdlet，且不會使用任何變數，而是會成功。</span><span class="sxs-lookup"><span data-stu-id="fa556-153">The first command, which runs the Get-UICulture cmdlet and does not use any variables, succeeds.</span></span> <span data-ttu-id="fa556-154">第二個命令會取得 $PSUICulture 變數的值失敗。</span><span class="sxs-lookup"><span data-stu-id="fa556-154">The second command, which gets the value of the $PSUICulture variable, fails.</span></span>

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a><span data-ttu-id="fa556-155">編輯工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="fa556-155">Editing a Session Configuration File</span></span>

<span data-ttu-id="fa556-156">除了將 runasvirtualaccount 設和 RunAsVirtualAccountGroups，會話設定中的所有設定都可以藉由編輯會話設定所使用的會話設定檔來進行修改。</span><span class="sxs-lookup"><span data-stu-id="fa556-156">All settings in a session configuration except for RunAsVirtualAccount and RunAsVirtualAccountGroups can be modified by editing the session configuration file used by the session configuration.</span></span> <span data-ttu-id="fa556-157">若要這樣做，請先找出會話設定檔的使用中複本。</span><span class="sxs-lookup"><span data-stu-id="fa556-157">To do this, begin by locating the active copy of the session configuration file.</span></span>

<span data-ttu-id="fa556-158">當您在會話設定中使用會話設定檔時，PowerShell 會建立會話設定檔的使用中複本，並將它儲存 \$ 在 \\ 本機電腦上的 pshome SessionConfig 目錄中。</span><span class="sxs-lookup"><span data-stu-id="fa556-158">When you use a session configuration file in a session configuration, PowerShell creates an active copy of the session configuration file and stores it in the \$pshome\\SessionConfig directory on the local computer.</span></span>

<span data-ttu-id="fa556-159">會話設定檔的使用中複本位置會儲存在會話設定物件的 ConfigFilePath 屬性中。</span><span class="sxs-lookup"><span data-stu-id="fa556-159">The location of the active copy of a session configuration file is stored in the ConfigFilePath property of the session configuration object.</span></span>

<span data-ttu-id="fa556-160">下列命令會取得 NoLanguage 會話設定之會話設定檔的位置。</span><span class="sxs-lookup"><span data-stu-id="fa556-160">The following command gets the location of the session configuration file for the NoLanguage session configuration.</span></span>

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

<span data-ttu-id="fa556-161">該命令會傳回類似下列的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="fa556-161">That command returns a file path similar to the following:</span></span>

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="fa556-162">您可以在任何文字編輯器中編輯 .pssc 檔案。</span><span class="sxs-lookup"><span data-stu-id="fa556-162">You can edit the .pssc file in any text editor.</span></span> <span data-ttu-id="fa556-163">儲存檔案之後，任何使用會話設定的新會話都會採用此檔案。</span><span class="sxs-lookup"><span data-stu-id="fa556-163">After the file is saved it will be employed by any new sessions that use the session configuration.</span></span>

<span data-ttu-id="fa556-164">如果您需要修改將 runasvirtualaccount 設或 RunAsVirtualAccountGroups 設定，您必須取消註冊會話設定，並重新註冊包含已編輯值的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-164">If you need to modify the RunAsVirtualAccount or the RunAsVirtualAccountGroups settings, you must un-register the session configuration and re-register a session configuration file that includes the edited values.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="fa556-165">測試會話設定檔</span><span class="sxs-lookup"><span data-stu-id="fa556-165">Testing a Session Configuration File</span></span>

<span data-ttu-id="fa556-166">使用 Test-PSSessionConfigurationFile Cmdlet 測試手動編輯的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-166">Use the Test-PSSessionConfigurationFile cmdlet to test manually edited session configuration files.</span></span> <span data-ttu-id="fa556-167">這一點很重要：如果檔案語法和值不是有效的，使用者將無法使用會話設定來建立會話。</span><span class="sxs-lookup"><span data-stu-id="fa556-167">That's important: if the file syntax and values are not valid users will not be able to use the session configuration to create a session.</span></span>

<span data-ttu-id="fa556-168">例如，下列命令會測試 NoLanguage 會話設定的作用中會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-168">For example, the following command tests the active session configuration file of the NoLanguage session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="fa556-169">如果設定檔中的語法和值有效 Test-PSSessionConfigurationFile 會傳回 True。</span><span class="sxs-lookup"><span data-stu-id="fa556-169">If the syntax and values in the configuration file are valid Test-PSSessionConfigurationFile returns True.</span></span> <span data-ttu-id="fa556-170">如果語法和值無效，則 Cmdlet 會傳回 False。</span><span class="sxs-lookup"><span data-stu-id="fa556-170">If the syntax and values are not valid then the cmdlet returns False.</span></span>

<span data-ttu-id="fa556-171">您可以使用 Test-PSSessionConfigurationFile 來測試任何會話設定檔，包括 New-PSSessionConfiguration Cmdlet 所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="fa556-171">You can use Test-PSSessionConfigurationFile to test any session configuration file, including files that the New-PSSessionConfiguration cmdlet creates.</span></span> <span data-ttu-id="fa556-172">如需詳細資訊，請參閱 Test-PSSessionConfigurationFile Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="fa556-172">For more information, see the help topic for the Test-PSSessionConfigurationFile cmdlet.</span></span>

## <a name="removing-a-session-configuration-file"></a><span data-ttu-id="fa556-173">移除會話設定檔</span><span class="sxs-lookup"><span data-stu-id="fa556-173">Removing a Session Configuration File</span></span>

<span data-ttu-id="fa556-174">您無法從會話設定中移除會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-174">You cannot remove a session configuration file from a session configuration.</span></span>
<span data-ttu-id="fa556-175">不過，您可以將檔案取代為使用預設設定的新檔案。</span><span class="sxs-lookup"><span data-stu-id="fa556-175">However, you can replace the file with a new file that uses the default settings.</span></span> <span data-ttu-id="fa556-176">這可有效地取消原始設定檔案所使用的設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-176">This effectively cancels the settings used by the original configuration file.</span></span>

<span data-ttu-id="fa556-177">若要取代會話設定檔，請建立新的會話設定檔，以使用預設設定，然後使用 Set-PSSessionConfiguration Cmdlet 將自訂會話設定檔取代為新的檔案。</span><span class="sxs-lookup"><span data-stu-id="fa556-177">To replace a session configuration file, create a new session configuration file that uses the default settings, then use the Set-PSSessionConfiguration cmdlet to replace the custom session configuration file with the new file.</span></span>

<span data-ttu-id="fa556-178">例如，下列命令會建立預設會話設定檔，然後取代 NoLanguage 會話設定中的使用中會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="fa556-178">For example, the following commands create a Default session configuration file and then replace the active session configuration file in the NoLanguage session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

<span data-ttu-id="fa556-179">當這些命令完成時，NoLanguage 會話設定實際上會提供完整的語言支援 (使用該會話設定建立之所有會話的預設設定) 。</span><span class="sxs-lookup"><span data-stu-id="fa556-179">When these commands finish, the NoLanguage session configuration will actually provide full language support (the default setting) for all sessions created with that session configuration.</span></span>

<span data-ttu-id="fa556-180">使用會話設定檔來查看會話設定的內容：代表會話設定的會話設定物件具有額外的屬性，可讓您輕鬆地探索及分析會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-180">Viewing the Properties of a Session Configuration The session configuration objects that represent session configurations using session configuration files have additional properties that make it easy to discover and analyze the session configuration.</span></span> <span data-ttu-id="fa556-181"> (請注意，以下所示的類型名稱包含格式化的視圖定義。 ) 您可以執行 Get-PSSessionConfiguration Cmdlet 來查看屬性，並將傳回的資料輸送到 Get-Member Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="fa556-181">(Note that the type name shown below includes a formatted view definition.) You can view the properties by running the Get-PSSessionConfiguration cmdlet and piping the returned data to the Get-Member cmdlet:</span></span>

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

<span data-ttu-id="fa556-182">這些屬性可讓您輕鬆地搜尋特定的會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-182">These properties make it easy to search for specific session configurations.</span></span>
<span data-ttu-id="fa556-183">例如，您可以使用 ExecutionPolicy 屬性來尋找支援會話與 RemoteSigned 執行原則的會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-183">For example, you can use the ExecutionPolicy property to find a session configuration that supports sessions with the RemoteSigned execution policy.</span></span>
<span data-ttu-id="fa556-184">請注意，因為 ExecutionPolicy 屬性只存在於使用會話設定檔的會話中，所以此命令可能不會傳回所有合格的會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-184">Note that, because the ExecutionPolicy property exists only on sessions that use session configuration files, the command might not return all qualifying session configurations.</span></span>

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

<span data-ttu-id="fa556-185">下列命令會取得 RunAsUser 為 Exchange 系統管理員的會話設定。</span><span class="sxs-lookup"><span data-stu-id="fa556-185">The following command gets session configurations in which the RunAsUser is the Exchange administrator.</span></span>

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

<span data-ttu-id="fa556-186">若要查看與設定相關聯之角色定義的相關資訊，請使用 Get-PSSessionCapability Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa556-186">To view information about the role definitions associated with a configuration use the Get-PSSessionCapability cmdlet.</span></span> <span data-ttu-id="fa556-187">這個 Cmdlet 可讓您判斷特定端點中特定使用者可用的命令和環境。</span><span class="sxs-lookup"><span data-stu-id="fa556-187">This cmdlet enables you to determine the commands and environment available to specific users in specific endpoints.</span></span>

## <a name="notes"></a><span data-ttu-id="fa556-188">注意</span><span class="sxs-lookup"><span data-stu-id="fa556-188">NOTES</span></span>

<span data-ttu-id="fa556-189">會話設定也支援稱為「空白」會話的會話類型。</span><span class="sxs-lookup"><span data-stu-id="fa556-189">Session configurations also support a type of session known as an "empty" session.</span></span> <span data-ttu-id="fa556-190">空白的會話類型可讓您使用選取的命令來建立自訂會話。</span><span class="sxs-lookup"><span data-stu-id="fa556-190">An Empty session type enables you to create custom sessions with selected commands.</span></span> <span data-ttu-id="fa556-191">如果您沒有將模組、函式或腳本新增至空的會話，會話會限制為運算式，而且可能不會有任何實用的用途。</span><span class="sxs-lookup"><span data-stu-id="fa556-191">If you do not add modules, functions, or scripts to an empty session, the session is limited to expressions and might not be of any practical use.</span></span> <span data-ttu-id="fa556-192">SessionType 屬性會告知您是否正在使用空白會話。</span><span class="sxs-lookup"><span data-stu-id="fa556-192">The SessionType property tells you whether or not you are working with an empty session.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa556-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa556-193">SEE ALSO</span></span>

[<span data-ttu-id="fa556-194">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="fa556-194">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="fa556-195">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa556-195">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="fa556-196">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa556-196">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="fa556-197">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa556-197">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="fa556-198">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa556-198">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="fa556-199">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="fa556-199">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="fa556-200">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa556-200">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="fa556-201">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa556-201">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="fa556-202">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="fa556-202">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="fa556-203">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa556-203">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[<span data-ttu-id="fa556-204">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="fa556-204">Get-PSSessionCapability</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[<span data-ttu-id="fa556-205">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="fa556-205">New-PSRoleCapabilityFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)

