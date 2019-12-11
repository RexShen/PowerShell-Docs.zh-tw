---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中使用設定檔
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030613"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="2e0f5-103">如何在 Windows PowerShell ISE 中使用設定檔</span><span class="sxs-lookup"><span data-stu-id="2e0f5-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="2e0f5-104">本主題說明如何在 Windows PowerShell® 整合式指令碼環境 (ISE) 中使用設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="2e0f5-105">建議您在執行本節所述的工作之前，先檢閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)，或在 [主控台] 窗格中輸入 `Get-Help about_Profiles`，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="2e0f5-106">設定檔是當您啟動新的工作階段時自動執行的 Windows PowerShell ISE 指令碼。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="2e0f5-107">您可以為 Windows PowerShell ISE 建立一或多個 Windows PowerShell 設定檔，然後使用這些設定檔來新增 Windows PowerShell 或 Windows PowerShell ISE 環境的設定、準備環境供您使用，以及提供您所需的變數、別名、函式、色彩和字型喜好設定。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="2e0f5-108">設定檔會影響您啟動的每個 Windows PowerShell ISE 工作階段。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="2e0f5-109">Windows PowerShell 執行原則會決定您是否可以執行指令碼並載入設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="2e0f5-110">預設執行原則 “Restricted” 可防止所有指令碼執行，包括設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="2e0f5-111">如果使用 “Restricted” 原則，則無法載入設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="2e0f5-112">如需執行原則的詳細資訊，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="2e0f5-113">選取要在 Windows PowerShell ISE 中使用的設定檔</span><span class="sxs-lookup"><span data-stu-id="2e0f5-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="2e0f5-114">Windows PowerShell ISE 支援目前使用者和所有使用者的設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="2e0f5-115">它也支援適用於所有主機的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="2e0f5-116">您使用的設定檔取決於您使用 Windows PowerShell 和 Windows PowerShell ISE 的方式。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="2e0f5-117">如果只使用 Windows PowerShell ISE 來執行 Windows PowerShell，則要將所有項目儲存到 ISE 特定的其中一個設定檔，例如，適用於 Windows PowerShell ISE 的 CurrentUserCurrentHost 設定檔，或者適用於 Windows PowerShell ISE 的 AllUsersCurrentHost 設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="2e0f5-118">如果使用多個主機程式來執行 Windows PowerShell，請在影響所有主機程式的設定檔 (例如 CurrentUserAllHosts 或 AllUsersAllHosts 設定檔) 中儲存您的函式、別名、變數和命令，並在適用於 Windows PowerShell ISE 設定檔的 CurrentUserCurrentHost 設定檔或適用於 Windows PowerShell ISE 的 AllUsersCurrentHost 設定檔中儲存 ISE 特定的功能 (例如色彩和字型自訂)。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="2e0f5-119">以下是可在 Windows PowerShell ISE 中建立及使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="2e0f5-120">每個設定檔會儲存到自己的特定路徑。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="2e0f5-121">設定檔類型</span><span class="sxs-lookup"><span data-stu-id="2e0f5-121">Profile Type</span></span> | <span data-ttu-id="2e0f5-122">設定檔路徑</span><span class="sxs-lookup"><span data-stu-id="2e0f5-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="2e0f5-123">**目前的使用者，PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="2e0f5-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="2e0f5-124">`$PROFILE.CurrentUserCurrentHost`，或 `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="2e0f5-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="2e0f5-125">**所有使用者，PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="2e0f5-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="2e0f5-126">**目前的使用者，所有主機**</span><span class="sxs-lookup"><span data-stu-id="2e0f5-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="2e0f5-127">**所有使用者，所有主機**</span><span class="sxs-lookup"><span data-stu-id="2e0f5-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="2e0f5-128">建立新的設定檔</span><span class="sxs-lookup"><span data-stu-id="2e0f5-128">To create a new profile</span></span>

<span data-ttu-id="2e0f5-129">若要建立新的 “Current user, Windows PowerShell ISE” 設定檔，請執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2e0f5-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="2e0f5-130">若要建立新的 “All users, Windows PowerShell ISE” 設定檔，請執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2e0f5-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="2e0f5-131">若要建立新的 “Current user, All Hosts” 設定檔，請執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2e0f5-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="2e0f5-132">若要建立新的 “All users, All Hosts” 設定檔，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="2e0f5-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="2e0f5-133">編輯設定檔</span><span class="sxs-lookup"><span data-stu-id="2e0f5-133">To edit a profile</span></span>

1. <span data-ttu-id="2e0f5-134">若要開啟設定檔，請執行命令 psedit，並提供指定您要編輯之設定檔的變數。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="2e0f5-135">例如，若要開啟 “Current user, Windows PowerShell ISE” 設定檔，請輸入︰`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="2e0f5-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="2e0f5-136">將一些項目新增至您的設定檔。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-136">Add some items to your profile.</span></span> <span data-ttu-id="2e0f5-137">以下是一些可協助您開始的範例︰</span><span class="sxs-lookup"><span data-stu-id="2e0f5-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="2e0f5-138">若要將主控台窗格的預設背景色彩變更為藍色，請在設定檔中輸入︰`$psISE.Options.OutputPaneBackground = 'blue'`。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="2e0f5-139">如需 $psISE 變數的詳細資訊，請參閱 [Windows PowerShell ISE 物件模型參考](object-model/The-ISE-Object-Model-Hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="2e0f5-140">若要將字型大小變更為 20，請在設定檔中輸入︰`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="2e0f5-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="2e0f5-141">若要儲存設定檔，請在 **[檔案]** 功能表上，按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="2e0f5-142">下次當您開啟 Windows PowerShell ISE 時，便會套用您的自訂。</span><span class="sxs-lookup"><span data-stu-id="2e0f5-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e0f5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e0f5-143">See Also</span></span>

- [<span data-ttu-id="2e0f5-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="2e0f5-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="2e0f5-145">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="2e0f5-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
