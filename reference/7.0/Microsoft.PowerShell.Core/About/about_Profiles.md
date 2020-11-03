---
description: 說明如何建立和使用 PowerShell 設定檔。
keywords: powershell,cmdlet
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 3fb6a67e160281f60f20c187bf37c6920a506705
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206616"
---
# <a name="about-profiles"></a><span data-ttu-id="0fe7d-104">關於設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-104">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="0fe7d-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0fe7d-105">Short Description</span></span>
<span data-ttu-id="0fe7d-106">說明如何建立和使用 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-106">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="0fe7d-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="0fe7d-107">Long Description</span></span>

<span data-ttu-id="0fe7d-108">您可以建立 PowerShell 設定檔來自訂您的環境，並將工作階段特定項目新增至您啟動的每一個 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-108">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="0fe7d-109">PowerShell 設定檔是在 PowerShell 啟動時執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-109">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="0fe7d-110">您可以使用設定檔做為登入腳本來自訂環境。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-110">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="0fe7d-111">您可以新增命令、別名、函式、變數、嵌入式管理單元、模組和 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-111">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="0fe7d-112">您也可以將其他會話專屬的元素新增至您的設定檔，以便在每個會話中都能使用它們，而不需要匯入或重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-112">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="0fe7d-113">PowerShell 支援使用者和主機程式的數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-113">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="0fe7d-114">不過，它不會為您建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-114">However, it does not create the profiles for you.</span></span> <span data-ttu-id="0fe7d-115">本主題說明這些設定檔，並說明如何在您的電腦上建立及維護設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-115">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="0fe7d-116">它說明如何使用 PowerShell 主控台的 **NoProfile** 參數 ( # A0) 來啟動 powershell，而不需要任何設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-116">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="0fe7d-117">而且，它會說明 PowerShell 執行原則對設定檔的影響。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-117">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="0fe7d-118">設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-118">The Profile Files</span></span>

<span data-ttu-id="0fe7d-119">PowerShell 支援數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-119">PowerShell supports several profile files.</span></span> <span data-ttu-id="0fe7d-120">此外，PowerShell 主機程式可以支援自己的主機專屬設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-120">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="0fe7d-121">例如，PowerShell 主控台支援下列基本設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-121">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="0fe7d-122">設定檔會依優先順序列出。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-122">The profiles are listed in precedence order.</span></span> <span data-ttu-id="0fe7d-123">第一個設定檔的優先順序最高。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-123">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="0fe7d-124">Description</span><span class="sxs-lookup"><span data-stu-id="0fe7d-124">Description</span></span>               | <span data-ttu-id="0fe7d-125">路徑</span><span class="sxs-lookup"><span data-stu-id="0fe7d-125">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="0fe7d-126">所有使用者、所有主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-126">All Users, All Hosts</span></span>      |<span data-ttu-id="0fe7d-127">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="0fe7d-127">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="0fe7d-128">所有使用者、目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-128">All Users, Current Host</span></span>   |<span data-ttu-id="0fe7d-129">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="0fe7d-129">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="0fe7d-130">目前的使用者，所有主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-130">Current User, All Hosts</span></span>   |<span data-ttu-id="0fe7d-131">$Home \\ [My] 檔 \\ PowerShell \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="0fe7d-131">$Home\\[My ]Documents\\PowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="0fe7d-132">目前的使用者，目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-132">Current user, Current Host</span></span>|<span data-ttu-id="0fe7d-133">$Home \\ [My] 檔 \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fe7d-133">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="0fe7d-134">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="0fe7d-134">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="0fe7d-135">設定檔路徑包含下列變數：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-135">The profile paths include the following variables:</span></span>

- <span data-ttu-id="0fe7d-136">`$PSHOME`變數，儲存 PowerShell 的安裝目錄</span><span class="sxs-lookup"><span data-stu-id="0fe7d-136">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="0fe7d-137">`$Home`變數，用來儲存目前使用者的主目錄</span><span class="sxs-lookup"><span data-stu-id="0fe7d-137">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="0fe7d-138">此外，裝載 PowerShell 的其他程式也可以支援自己的設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-138">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="0fe7d-139">例如，Visual Studio Code 支援下列主機特定設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-139">For example, Visual Studio Code supports the following host-specific profiles.</span></span>

|<span data-ttu-id="0fe7d-140">Description</span><span class="sxs-lookup"><span data-stu-id="0fe7d-140">Description</span></span>               | <span data-ttu-id="0fe7d-141">路徑</span><span class="sxs-lookup"><span data-stu-id="0fe7d-141">Path</span></span>                                     |
|--------------------------|------------------------------------------|
|<span data-ttu-id="0fe7d-142">所有使用者、目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-142">All users, Current Host</span></span>   |<span data-ttu-id="0fe7d-143">$PSHOME \\Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="0fe7d-143">$PSHOME\\Microsoft.VSCode_profile.ps1</span></span>|
|<span data-ttu-id="0fe7d-144">目前的使用者，目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-144">Current user, Current Host</span></span>|<span data-ttu-id="0fe7d-145">$Home \\ [My] 檔 \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fe7d-145">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="0fe7d-146">Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="0fe7d-146">Microsoft.VSCode_profile.ps1</span></span>|

<span data-ttu-id="0fe7d-147">在 PowerShell 說明中，「CurrentUser，Current Host」設定檔是最常稱為「您的 PowerShell 設定檔」的設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-147">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="0fe7d-148">$PROFILE 變數</span><span class="sxs-lookup"><span data-stu-id="0fe7d-148">The $PROFILE variable</span></span>

<span data-ttu-id="0fe7d-149">`$PROFILE`自動變數會儲存目前會話中可用之 PowerShell 設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-149">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="0fe7d-150">若要查看設定檔路徑，請顯示變數的值 `$PROFILE` 。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-150">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="0fe7d-151">您也可以 `$PROFILE` 在命令中使用變數來代表路徑。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-151">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="0fe7d-152">`$PROFILE`變數會儲存「目前使用者、目前主機」設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-152">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="0fe7d-153">其他設定檔會儲存在變數的附注屬性中 `$PROFILE` 。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-153">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="0fe7d-154">例如，在 `$PROFILE` Windows PowerShell 主控台中，變數具有下列值。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-154">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="0fe7d-155">描述</span><span class="sxs-lookup"><span data-stu-id="0fe7d-155">Description</span></span>                |<span data-ttu-id="0fe7d-156">Name</span><span class="sxs-lookup"><span data-stu-id="0fe7d-156">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="0fe7d-157">目前的使用者，目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-157">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="0fe7d-158">目前的使用者，目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-158">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="0fe7d-159">目前的使用者，所有主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-159">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="0fe7d-160">所有使用者、目前的主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-160">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="0fe7d-161">所有使用者、所有主機</span><span class="sxs-lookup"><span data-stu-id="0fe7d-161">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="0fe7d-162">由於變數的值會隨著每個 `$PROFILE` 使用者和每個主應用程式而變更，因此請務必在您使用的每個 PowerShell 主應用程式中顯示設定檔變數的值。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-162">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="0fe7d-163">若要查看變數目前的值 `$PROFILE` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-163">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="0fe7d-164">您可以使用 `$PROFILE` 多個命令中的變數。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-164">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="0fe7d-165">例如，下列命令會在 [記事本] 中開啟「目前的使用者、目前的主機」設定檔：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-165">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="0fe7d-166">下列命令會判斷是否已在本機電腦上建立 "All Users，All Hosts" 設定檔：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-166">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="0fe7d-167">如何建立設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-167">How to create a profile</span></span>

<span data-ttu-id="0fe7d-168">若要建立 PowerShell 設定檔，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-168">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="0fe7d-169">例如，若要在目前的 PowerShell 主應用程式中建立目前使用者的設定檔，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-169">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="0fe7d-170">在這個命令中， `If` 語句會防止您覆寫現有的設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-170">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="0fe7d-171">將預留位置的值取代 \<profile-path\> 為您想要建立之設定檔檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-171">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="0fe7d-172">若要在 Windows Vista 和更新版本的 Windows 中建立「所有使用者」設定檔，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-172">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="0fe7d-173">如何編輯設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-173">How to edit a profile</span></span>

<span data-ttu-id="0fe7d-174">您可以在文字編輯器（例如 [記事本]）中開啟任何 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-174">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="0fe7d-175">若要在 [記事本] 的目前 PowerShell 主應用程式中開啟目前使用者的設定檔，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-175">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="0fe7d-176">若要開啟其他設定檔，請指定設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-176">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="0fe7d-177">例如，若要為所有主機應用程式的所有使用者開啟設定檔，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-177">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="0fe7d-178">若要套用變更，請儲存設定檔，然後重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-178">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="0fe7d-179">如何選擇設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-179">How to choose a profile</span></span>

<span data-ttu-id="0fe7d-180">如果您使用多個主應用程式，請將您在所有主機應用程式中使用的專案放入 `$PROFILE.CurrentUserAllHosts` 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-180">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="0fe7d-181">放置主機應用程式特定的專案，例如，設定主應用程式之背景色彩的命令（位於該主應用程式專用的設定檔中）。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-181">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="0fe7d-182">如果您是為許多使用者自訂 PowerShell 的系統管理員，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-182">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="0fe7d-183">將一般專案儲存在 `$PROFILE.AllUsersAllHosts` 設定檔中</span><span class="sxs-lookup"><span data-stu-id="0fe7d-183">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="0fe7d-184">將主應用程式專用的專案儲存在 `$PROFILE.AllUsersCurrentHost` 主機應用程式專用的設定檔中</span><span class="sxs-lookup"><span data-stu-id="0fe7d-184">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="0fe7d-185">在使用者特定的設定檔中儲存特定使用者的專案</span><span class="sxs-lookup"><span data-stu-id="0fe7d-185">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="0fe7d-186">請務必查看主機應用程式檔，以瞭解 PowerShell 設定檔的任何特殊執行。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-186">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="0fe7d-187">如何使用設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-187">How to use a profile</span></span>

<span data-ttu-id="0fe7d-188">您在 PowerShell 中建立的許多專案和大部分執行的命令只會影響目前的會話。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-188">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="0fe7d-189">當您結束會話時，會刪除專案。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-189">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="0fe7d-190">會話專屬的命令和專案包括變數、喜好設定變數、別名、函式、命令 (除了 [ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) 之外，以及您新增至會話的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-190">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="0fe7d-191">若要儲存這些專案並讓這些專案可在所有未來的會話中使用，請將它們新增至 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-191">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="0fe7d-192">設定檔的另一個常見用途是儲存經常使用的函式、別名和變數。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-192">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="0fe7d-193">當您將專案儲存在設定檔時，可以在任何適用的會話中使用它們，而不需要重新建立。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-193">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="0fe7d-194">如何啟動設定檔</span><span class="sxs-lookup"><span data-stu-id="0fe7d-194">How to start a profile</span></span>

<span data-ttu-id="0fe7d-195">當您開啟設定檔時，它是空白的。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-195">When you open the profile file, it is blank.</span></span> <span data-ttu-id="0fe7d-196">不過，您可以使用經常使用的變數、別名和命令來填入它。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-196">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="0fe7d-197">以下是一些協助您入門的建議。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-197">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="0fe7d-198">新增可讓您輕鬆開啟設定檔的命令</span><span class="sxs-lookup"><span data-stu-id="0fe7d-198">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="0fe7d-199">如果您使用「目前使用者」、「目前的主機」設定檔以外的設定檔，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-199">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="0fe7d-200">例如，新增下列命令：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-200">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="0fe7d-201">新增可列出任何 Cmdlet 之別名的函式</span><span class="sxs-lookup"><span data-stu-id="0fe7d-201">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="0fe7d-202">自訂您的主控台</span><span class="sxs-lookup"><span data-stu-id="0fe7d-202">Customize your console</span></span>

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="0fe7d-203">新增自訂的 PowerShell 提示字元</span><span class="sxs-lookup"><span data-stu-id="0fe7d-203">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="0fe7d-204">如需 PowerShell 提示的詳細資訊，請參閱 [about_Prompts](about_Prompts.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-204">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="0fe7d-205">NoProfile 參數</span><span class="sxs-lookup"><span data-stu-id="0fe7d-205">The NoProfile parameter</span></span>

<span data-ttu-id="0fe7d-206">若要啟動沒有設定檔的 PowerShell，請使用 **PowerShell.exe** 的 **NoProfile** 參數，也就是啟動 powershell 的程式。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-206">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe** , the program that starts PowerShell.</span></span>

<span data-ttu-id="0fe7d-207">若要開始，請開啟可以啟動 PowerShell 的程式，例如 Cmd.exe 或 PowerShell 本身。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-207">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="0fe7d-208">您也可以使用 Windows 中的 [執行] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-208">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="0fe7d-209">輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-209">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="0fe7d-210">如需 PowerShell.exe 之參數的完整清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7d-210">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="0fe7d-211">設定檔和執行原則</span><span class="sxs-lookup"><span data-stu-id="0fe7d-211">Profiles and Execution Policy</span></span>

<span data-ttu-id="0fe7d-212">PowerShell 執行原則會決定您是否可以執行腳本並載入設定檔，包括設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-212">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="0fe7d-213">**受限制** 的執行原則是預設值。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-213">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="0fe7d-214">它可防止所有腳本執行，包括設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-214">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="0fe7d-215">如果您使用「受限」原則，則不會執行設定檔，而且不會套用其內容。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-215">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="0fe7d-216">`Set-ExecutionPolicy`命令會設定並變更您的執行原則。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-216">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="0fe7d-217">它是在所有 PowerShell 會話中套用的幾個命令之一，因為該值會儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-217">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="0fe7d-218">當您開啟主控台時，不需要進行設定，也不需要 `Set-ExecutionPolicy` 在設定檔中儲存命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-218">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="0fe7d-219">設定檔和遠端會話</span><span class="sxs-lookup"><span data-stu-id="0fe7d-219">Profiles and remote sessions</span></span>

<span data-ttu-id="0fe7d-220">PowerShell 設定檔不會自動在遠端會話中執行，因此設定檔新增的命令不會出現在遠端會話中。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-220">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="0fe7d-221">此外，在 `$PROFILE` 遠端會話中不會填入自動變數。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-221">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="0fe7d-222">若要在會話中執行設定檔，請使用 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-222">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="0fe7d-223">例如，下列命令會從會話中的本機電腦執行「目前使用者、目前的主機」設定檔 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-223">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="0fe7d-224">下列命令會從會話中的遠端電腦執行「目前使用者、目前的主機」設定檔 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-224">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="0fe7d-225">因為 `$PROFILE` 未填入變數，所以命令會使用設定檔的明確路徑。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-225">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="0fe7d-226">我們會使用點出運算子，讓設定檔在遠端電腦上的目前範圍中執行，而不是在它自己的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-226">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="0fe7d-227">執行此命令之後，就可以在中使用設定檔新增至會話的命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-227">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe7d-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe7d-228">See Also</span></span>

[<span data-ttu-id="0fe7d-229">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="0fe7d-229">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="0fe7d-230">about_Functions</span><span class="sxs-lookup"><span data-stu-id="0fe7d-230">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="0fe7d-231">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="0fe7d-231">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="0fe7d-232">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="0fe7d-232">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="0fe7d-233">about_Signing</span><span class="sxs-lookup"><span data-stu-id="0fe7d-233">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="0fe7d-234">about_Remote</span><span class="sxs-lookup"><span data-stu-id="0fe7d-234">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="0fe7d-235">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="0fe7d-235">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="0fe7d-236">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0fe7d-236">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
