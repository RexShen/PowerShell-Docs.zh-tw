---
description: 描述 (Pssession 的 Windows PowerShell 會話) 並說明如何建立與遠端電腦的持續連線。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: 0bf3e24ca11108b5ab4739abd9be530243c50f11
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207984"
---
# <a name="about-pssessions"></a><span data-ttu-id="0f466-104">關於 Pssession</span><span class="sxs-lookup"><span data-stu-id="0f466-104">About PSSessions</span></span>

## <a name="short-description"></a><span data-ttu-id="0f466-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0f466-105">Short Description</span></span>

<span data-ttu-id="0f466-106">描述 (Pssession 的 Windows PowerShell 會話) 並說明如何建立與遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="0f466-106">Describes Windows PowerShell sessions (PSSessions) and explains how to establish a persistent connection to a remote computer.</span></span>

## <a name="long-description"></a><span data-ttu-id="0f466-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="0f466-107">Long Description</span></span>

<span data-ttu-id="0f466-108">若要在遠端電腦上執行 Windows PowerShell 命令，您可以使用 Cmdlet 的 **ComputerName** 參數，也可以建立 Windows PowerShell 會話 (pssession) 並在 pssession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-108">To run Windows PowerShell commands on a remote computer, you can use the **ComputerName** parameter of a cmdlet, or you can create a Windows PowerShell session (PSSession) and run commands in the PSSession.</span></span>

<span data-ttu-id="0f466-109">當您建立 PSSession 時，Windows PowerShell 會建立連到遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="0f466-109">When you create a PSSession, Windows PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="0f466-110">使用 PSSession 在遠端電腦上執行一連串的相關命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-110">Use a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="0f466-111">在相同 PSSession 中執行的命令可以共用資料，例如變數、別名和函數的值。</span><span class="sxs-lookup"><span data-stu-id="0f466-111">Commands that run in the same PSSession can share data, such as the values of variables, aliases, and functions.</span></span>

<span data-ttu-id="0f466-112">您也可以在本機電腦上建立 PSSession，並在其中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-112">You can also create a PSSession on the local computer and run commands in it.</span></span>
<span data-ttu-id="0f466-113">本機 PSSession 使用 Windows PowerShell 遠端基礎結構來建立和維護 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-113">A local PSSession uses the Windows PowerShell remoting infrastructure to create and maintain the PSSession.</span></span>

<span data-ttu-id="0f466-114">從 Windows PowerShell 3.0 開始，Pssession 與建立它們的會話無關。</span><span class="sxs-lookup"><span data-stu-id="0f466-114">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they are created.</span></span> <span data-ttu-id="0f466-115">作用中的 Pssession 會在遠端電腦上進行維護 (或連線) 的「伺服器端」電腦。</span><span class="sxs-lookup"><span data-stu-id="0f466-115">Active PSSessions are maintained on the remote computer (or the computer at the remote end or "server-side" of the connection).</span></span> <span data-ttu-id="0f466-116">如此一來，您就可以從 PSSession 中斷連線，並在稍後從同一部電腦或不同的電腦重新連接到它。</span><span class="sxs-lookup"><span data-stu-id="0f466-116">As a result, you can disconnect from the PSSession and reconnect to it at a later time from the same computer or from a different computer.</span></span>

<span data-ttu-id="0f466-117">本主題說明如何建立、使用、取得和刪除 Pssession。</span><span class="sxs-lookup"><span data-stu-id="0f466-117">This topic explains how to create, use, get, and delete PSSessions.</span></span> <span data-ttu-id="0f466-118">如需更多的詳細資訊，請參閱 [about_PSSession_Details](about_PSSession_Details.md)。</span><span class="sxs-lookup"><span data-stu-id="0f466-118">For more advanced information, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

<span data-ttu-id="0f466-119">注意： Pssession 使用 Windows PowerShell 遠端基礎結構。</span><span class="sxs-lookup"><span data-stu-id="0f466-119">Note: PSSessions use the Windows PowerShell remoting infrastructure.</span></span> <span data-ttu-id="0f466-120">若要使用 Pssession，必須設定本機和遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="0f466-120">To use PSSessions, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="0f466-121">如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f466-121">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

<span data-ttu-id="0f466-122">在 Windows Vista 和更新版本的 Windows 中，若要在本機電腦上建立 PSSession，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0f466-122">In Windows Vista and later versions of Windows, to create a PSSession on a local computer, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

## <a name="what-is-a-session"></a><span data-ttu-id="0f466-123">什麼是會話？</span><span class="sxs-lookup"><span data-stu-id="0f466-123">What Is a Session?</span></span>

<span data-ttu-id="0f466-124">會話是 Windows PowerShell 執行所在的環境。</span><span class="sxs-lookup"><span data-stu-id="0f466-124">A session is an environment in which Windows PowerShell runs.</span></span>

<span data-ttu-id="0f466-125">每次啟動 Windows PowerShell 時，系統就會為您建立會話，而且您可以在會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-125">Each time you start Windows PowerShell, a session is created for you, and you can run commands in the session.</span></span> <span data-ttu-id="0f466-126">您也可以將專案新增至您的會話（例如模組和嵌入式管理單元），也可以建立專案，例如變數、函式和別名。</span><span class="sxs-lookup"><span data-stu-id="0f466-126">You can also add items to your session, such as modules and snap-ins, and you can create items, such as variables, functions, and aliases.</span></span> <span data-ttu-id="0f466-127">這些專案只存在於會話中，而且會在會話結束時刪除。</span><span class="sxs-lookup"><span data-stu-id="0f466-127">These items exist only in the session and are deleted when the session ends.</span></span>

<span data-ttu-id="0f466-128">您也可以在本機電腦或遠端電腦上建立使用者管理的會話，稱為「Windows PowerShell 會話」或「Pssession」。</span><span class="sxs-lookup"><span data-stu-id="0f466-128">You can also create user-managed sessions, known as " Windows PowerShell sessions" or "PSSessions," on the local computer or on a remote computer.</span></span> <span data-ttu-id="0f466-129">如同預設的會話，您可以在 PSSession 中執行命令，並加入和建立專案。</span><span class="sxs-lookup"><span data-stu-id="0f466-129">Like the default session, you can run commands in a PSSession and add and create items.</span></span> <span data-ttu-id="0f466-130">但是，不同于自動啟動的會話，您可以控制您所建立的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="0f466-130">However, unlike the session that starts automatically, you can control the PSSessions that you create.</span></span> <span data-ttu-id="0f466-131">您可以取得、建立、設定和移除它們、中斷連接並重新連接，以及在相同的 PSSession 中執行多個命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-131">You can get, create, configure, and remove them, disconnect and reconnect to them, and run multiple commands in the same PSSession.</span></span> <span data-ttu-id="0f466-132">PSSession 會保持可用，直到您將它刪除或超時為止。</span><span class="sxs-lookup"><span data-stu-id="0f466-132">The PSSession remains available until you delete it or it times out.</span></span>

<span data-ttu-id="0f466-133">一般來說，您會建立 PSSession，在遠端電腦上執行一連串的相關命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-133">Typically, you create a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="0f466-134">當您在遠端電腦上建立 PSSession 時，Windows PowerShell 會建立與遠端電腦的持續連線以支援會話。</span><span class="sxs-lookup"><span data-stu-id="0f466-134">When you create a PSSession on a remote computer, Windows PowerShell establishes a persistent connection to the remote computer to support the session.</span></span>

<span data-ttu-id="0f466-135">如果您使用或 Cmdlet 的 **ComputerName** 參數 `Invoke-Command` `Enter-PSSession` 來執行遠端命令或啟動互動式會話，Windows PowerShell 會在遠端電腦上建立暫時會話，並在命令完成或互動式會話結束時立即關閉會話。</span><span class="sxs-lookup"><span data-stu-id="0f466-135">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlet to run a remote command or to start an interactive session, Windows PowerShell creates a temporary session on the remote computer and closes the session as soon as the command is complete or as soon as the interactive session ends.</span></span> <span data-ttu-id="0f466-136">您無法控制這些暫時性會話，也無法將它們用於單一命令或單一互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0f466-136">You cannot control these temporary sessions, and you cannot use them for more than a single command or a single interactive session.</span></span>

<span data-ttu-id="0f466-137">在 Windows PowerShell 中，「目前會話」是您正在使用的會話。</span><span class="sxs-lookup"><span data-stu-id="0f466-137">In Windows PowerShell, the "current session" is the session that you are working in.</span></span> <span data-ttu-id="0f466-138">「目前的會話」可以參考任何會話，包括暫時性會話或 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-138">The "current session" can refer to any session, including a temporary session or a PSSession.</span></span>

## <a name="why-use-a-pssession"></a><span data-ttu-id="0f466-139">為何要使用 PSSession？</span><span class="sxs-lookup"><span data-stu-id="0f466-139">Why Use a PSSession?</span></span>

<span data-ttu-id="0f466-140">當您需要持續連線到遠端電腦時，請使用 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-140">Use a PSSession when you need a persistent connection to a remote computer.</span></span>
<span data-ttu-id="0f466-141">您可以使用 PSSession 來執行一系列共用資料的命令，例如變數的值、函式的內容，或別名的定義。</span><span class="sxs-lookup"><span data-stu-id="0f466-141">With a PSSession, you can run a series of commands that share data, such as the value of variables, the contents of a function, or the definition of an alias.</span></span>

<span data-ttu-id="0f466-142">您可以執行遠端命令，而不需要建立 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-142">You can run remote commands without creating a PSSession.</span></span> <span data-ttu-id="0f466-143">使用已啟用遠端 Cmdlet 的 **ComputerName** 參數，在一或多部電腦上執行單一命令或一系列不相關的命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-143">Use the **ComputerName** parameter of remote-enabled cmdlets to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="0f466-144">當您使用或的 **ComputerName** 參數時 `Invoke-Command` Windows PowerShell 會 `Enter-PSSession` 建立與遠端電腦的暫時連線，然後在命令完成時立即關閉連接。</span><span class="sxs-lookup"><span data-stu-id="0f466-144">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, Windows PowerShell establishes a temporary connection to the remote computer and then closes the connection as soon as the command is complete.</span></span> <span data-ttu-id="0f466-145">當連接關閉時，您建立的任何資料元素都會遺失。</span><span class="sxs-lookup"><span data-stu-id="0f466-145">Any data elements that you create are lost when the connection is closed.</span></span>

<span data-ttu-id="0f466-146">其他具有 **ComputerName** 參數的 Cmdlet （例如 `Get-Eventlog` 和）會 `Get-WmiObject` 使用不同的遠端技術來收集資料。</span><span class="sxs-lookup"><span data-stu-id="0f466-146">Other cmdlets that have a **ComputerName** parameter, such as `Get-Eventlog` and `Get-WmiObject`, use different remoting technologies to gather data.</span></span> <span data-ttu-id="0f466-147">無建立持續連線，例如 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-147">None create a persistent connection like a PSSession.</span></span>

## <a name="how-to-create-a-pssession"></a><span data-ttu-id="0f466-148">如何建立 PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-148">How to Create a PSSession</span></span>

<span data-ttu-id="0f466-149">若要建立 PSSession，請使用 `New-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f466-149">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="0f466-150">若要在遠端電腦上建立 PSSession，請使用 Cmdlet 的 **ComputerName** 參數 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0f466-150">To create the PSSession on a remote computer, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="0f466-151">例如，下列命令會在 Server01 電腦上建立新的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-151">For example, the following command creates a new PSSession on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

<span data-ttu-id="0f466-152">當您提交命令時，會 `New-PSSession` 建立 PSSession 並傳回代表 PSSession 的物件。</span><span class="sxs-lookup"><span data-stu-id="0f466-152">When you submit the command, `New-PSSession` creates the PSSession and returns an object that represents the PSSession.</span></span> <span data-ttu-id="0f466-153">當您建立 PSSession 時，可以將物件儲存在變數中，或者您可以使用 `Get-PSSession` 命令，在稍後取得 pssession。</span><span class="sxs-lookup"><span data-stu-id="0f466-153">You can save the object in a variable when you create the PSSession, or you can use a `Get-PSSession` command to get the PSSession at a later time.</span></span>

<span data-ttu-id="0f466-154">例如，下列命令會在 Server01 電腦上建立新的 PSSession，並將產生的物件儲存在 $ps 變數中。</span><span class="sxs-lookup"><span data-stu-id="0f466-154">For example, the following command creates a new PSSession on the Server01 computer and saves the resulting object in the $ps variable.</span></span>

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a><span data-ttu-id="0f466-155">如何在多部電腦上建立 Pssession</span><span class="sxs-lookup"><span data-stu-id="0f466-155">How to Create PSSessions on Multiple Computers</span></span>

<span data-ttu-id="0f466-156">若要在多部電腦上建立 Pssession，請使用 Cmdlet 的 **ComputerName** 參數 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0f466-156">To create PSSessions on multiple computers, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="0f466-157">在以逗號分隔的清單中輸入遠端電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f466-157">Type the names of the remote computers in a comma-separated list.</span></span>

<span data-ttu-id="0f466-158">例如，若要在 Server01、Server02 和 Server03 電腦上建立 Pssession，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0f466-158">For example, to create PSSessions on the Server01, Server02, and Server03 computers, type:</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="0f466-159">`New-PSSession` 在每一部遠端電腦上建立一個 PSSession。</span><span class="sxs-lookup"><span data-stu-id="0f466-159">`New-PSSession` creates one PSSession on each of the remote computers.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="0f466-160">如何取得 Pssession</span><span class="sxs-lookup"><span data-stu-id="0f466-160">How to Get PSSessions</span></span>

<span data-ttu-id="0f466-161">若要取得在目前會話中建立的 Pssession，請使用 `Get-PSSession` 不含 **ComputerName** 參數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f466-161">To get the PSSessions that were created in your current session, use the `Get-PSSession` cmdlet without the **ComputerName** parameter.</span></span> <span data-ttu-id="0f466-162">`Get-PSSession` 傳回傳回的相同物件類型 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0f466-162">`Get-PSSession` returns the same type of object that `New-PSSession` returns.</span></span>

<span data-ttu-id="0f466-163">下列命令會取得在目前會話中建立的所有 Pssession。</span><span class="sxs-lookup"><span data-stu-id="0f466-163">The following command gets all the PSSessions that were created in the current session.</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="0f466-164">Pssession 的預設顯示會顯示其識別碼和預設顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0f466-164">The default display of the PSSessions shows their ID and a default display name.</span></span> <span data-ttu-id="0f466-165">當您建立會話時，可以指派替代的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0f466-165">You can assign an alternate display name when you create the session.</span></span>

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

<span data-ttu-id="0f466-166">您也可以將 Pssession 儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="0f466-166">You can also save the PSSessions in a variable.</span></span> <span data-ttu-id="0f466-167">下列命令會取得 Pssession，並將它們儲存在 \$ ps123 變數中。</span><span class="sxs-lookup"><span data-stu-id="0f466-167">The following command gets the PSSessions and saves them in the \$ps123 variable.</span></span>

```powershell
$ps123 = Get-PSSession
```

<span data-ttu-id="0f466-168">使用 PSSession Cmdlet 時，您可以依識別碼、名稱或其實例識別碼來參考 PSSession， (GUID) 。</span><span class="sxs-lookup"><span data-stu-id="0f466-168">When using the PSSession cmdlets, you can refer to a PSSession by its ID, by its name, or by its instance ID (a GUID).</span></span> <span data-ttu-id="0f466-169">下列命令會依識別碼取得 PSSession，並將它儲存在 \$ ps01 變數中。</span><span class="sxs-lookup"><span data-stu-id="0f466-169">The following command gets a PSSession by its ID and saves it in the \$ps01 variable.</span></span>

```powershell
$ps01 = Get-PSSession -Id 1
```

<span data-ttu-id="0f466-170">從 Windows PowerShell 3.0 開始，Pssession 會在遠端電腦上進行維護。</span><span class="sxs-lookup"><span data-stu-id="0f466-170">Beginning in Windows PowerShell 3.0, PSSessions are maintained on the remote computer.</span></span> <span data-ttu-id="0f466-171">若要取得您在特定遠端電腦上建立的 Pssession，請使用 Cmdlet 的 **ComputerName** 參數 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0f466-171">To get PSSessions that you created on particular remote computers, use the **ComputerName** parameter of the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="0f466-172">下列命令會取得您在 Server01 遠端電腦上建立的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="0f466-172">The following command gets the PSSessions that you created on the Server01 remote computer.</span></span> <span data-ttu-id="0f466-173">這包括在目前會話中建立的 Pssession，以及在本機電腦或其他電腦上的其他會話中建立的。</span><span class="sxs-lookup"><span data-stu-id="0f466-173">This includes PSSessions created in the current session and in other sessions on the local computer or other computers.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

<span data-ttu-id="0f466-174">在 Windows PowerShell 2.0 中， `Get-PSSession` 只會取得在目前會話中建立的 pssession。</span><span class="sxs-lookup"><span data-stu-id="0f466-174">In Windows PowerShell 2.0, `Get-PSSession` gets only the PSSessions that were created in the current session.</span></span> <span data-ttu-id="0f466-175">它不會取得在其他會話或其他電腦上建立的 Pssession，即使會話連線到本機電腦上的命令也是如此。</span><span class="sxs-lookup"><span data-stu-id="0f466-175">It does not get PSSessions that were created in other sessions or on other computers, even if the sessions are connected to and are running commands on the local computer.</span></span>

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="0f466-176">如何在 PSSession 中執行命令</span><span class="sxs-lookup"><span data-stu-id="0f466-176">How to Run Commands in a PSSession</span></span>

<span data-ttu-id="0f466-177">若要在一或多個 Pssession 中執行命令，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f466-177">To run a command in one or more PSSessions, use the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="0f466-178">使用 Session 參數指定 Pssession 和 **ScriptBlock** 參數來指定命令。</span><span class="sxs-lookup"><span data-stu-id="0f466-178">Use the Session parameter to specify the PSSessions and the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="0f466-179">例如，若要 `Get-ChildItem` 在 $ps 123 變數中儲存的三個 pssession 中，執行 ( "dir" ) 命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0f466-179">For example, to run a `Get-ChildItem` ("dir") command in each of the three PSSessions saved in the $ps123 variable, type:</span></span>

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a><span data-ttu-id="0f466-180">如何刪除 Pssession</span><span class="sxs-lookup"><span data-stu-id="0f466-180">How to Delete PSSessions</span></span>

<span data-ttu-id="0f466-181">當您完成 PSSession 之後，請使用指令程式 `Remove-PSSession` 來刪除 pssession 並釋放它所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="0f466-181">When you are finished with the PSSession, use the `Remove-PSSession` cmdlet to delete the PSSession and to release the resources that it was using.</span></span>

```powershell
Remove-PSSession -Session $ps
```

<span data-ttu-id="0f466-182">或</span><span class="sxs-lookup"><span data-stu-id="0f466-182">or</span></span>

```powershell
Remove-PSSession -Id 1
```

<span data-ttu-id="0f466-183">若要從遠端電腦移除 PSSession，請使用 Cmdlet 的 **ComputerName** 參數 `Remove-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="0f466-183">To remove a PSSession from a remote computer, use the **ComputerName** parameter of the `Remove-PSSession` cmdlet.</span></span>

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

<span data-ttu-id="0f466-184">如果您未刪除 PSSession，PSSession 仍可供使用，直到它超時為止。</span><span class="sxs-lookup"><span data-stu-id="0f466-184">If you do not delete the PSSession, the PSSession remains available for use until it times out.</span></span>

<span data-ttu-id="0f466-185">您也可以使用 Cmdlet 的 **IdleTimeout** 參數 `New-PSSessionOption` 來設定閒置 PSSession 的到期時間。</span><span class="sxs-lookup"><span data-stu-id="0f466-185">You can also use the **IdleTimeout** parameter of the `New-PSSessionOption` cmdlet to set an expiration time for an idle PSSession.</span></span> <span data-ttu-id="0f466-186">如需詳細資訊，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。</span><span class="sxs-lookup"><span data-stu-id="0f466-186">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="the-pssession-cmdlets"></a><span data-ttu-id="0f466-187">PSSession Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0f466-187">The PSSession Cmdlets</span></span>

<span data-ttu-id="0f466-188">如需 PSSession Cmdlet 的清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0f466-188">For a list of PSSession cmdlets, type:</span></span>

```powershell
Get-Help *-PSSession
```

- <span data-ttu-id="0f466-189">Connect-PSSession：將 PSSession 連接到目前的會話</span><span class="sxs-lookup"><span data-stu-id="0f466-189">Connect-PSSession: Connects a PSSession to the current session</span></span>
- <span data-ttu-id="0f466-190">中斷連線-PSSession：中斷目前會話的 PSSession 連接</span><span class="sxs-lookup"><span data-stu-id="0f466-190">Disconnect-PSSession: Disconnects a PSSession from the current session</span></span>
- <span data-ttu-id="0f466-191">輸入-PSSession：啟動互動式會話</span><span class="sxs-lookup"><span data-stu-id="0f466-191">Enter-PSSession: Starts an interactive session</span></span>
- <span data-ttu-id="0f466-192">Exit-PSSession：結束互動式會話</span><span class="sxs-lookup"><span data-stu-id="0f466-192">Exit-PSSession: Ends an interactive session</span></span>
- <span data-ttu-id="0f466-193">取得-PSSession：取得目前會話中的 Pssession</span><span class="sxs-lookup"><span data-stu-id="0f466-193">Get-PSSession: Gets the PSSessions in the current session</span></span>
- <span data-ttu-id="0f466-194">新的-PSSession：在本機或遠端電腦上建立新的 PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-194">New-PSSession: Creates a new PSSession on a local or remote computer</span></span>
- <span data-ttu-id="0f466-195">接收-PSSession：取得在中斷連線的會話中執行的命令結果</span><span class="sxs-lookup"><span data-stu-id="0f466-195">Receive-PSSession: Gets the results of commands that ran in a disconnected session</span></span>
- <span data-ttu-id="0f466-196">移除-PSSession：刪除目前會話中的 Pssession</span><span class="sxs-lookup"><span data-stu-id="0f466-196">Remove-PSSession: Deletes the PSSessions in the current session</span></span>

## <a name="for-more-information"></a><span data-ttu-id="0f466-197">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0f466-197">For More Information</span></span>

<span data-ttu-id="0f466-198">如需 Pssession 的詳細資訊，請參閱 [about_PSSession_Details](about_PSSession_Details.md)。</span><span class="sxs-lookup"><span data-stu-id="0f466-198">For more information about PSSessions, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f466-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f466-199">See Also</span></span>

[<span data-ttu-id="0f466-200">about_Remote</span><span class="sxs-lookup"><span data-stu-id="0f466-200">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="0f466-201">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="0f466-201">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="0f466-202">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="0f466-202">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="0f466-203">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-203">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="0f466-204">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-204">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="0f466-205">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-205">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="0f466-206">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-206">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="0f466-207">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-207">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="0f466-208">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="0f466-208">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="0f466-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-209">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="0f466-210">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="0f466-210">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)
