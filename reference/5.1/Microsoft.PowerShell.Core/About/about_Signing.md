---
description: 說明如何簽署腳本，讓它們符合 PowerShell 執行原則。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 6e4c8c3783af1fda68c6a0c067b79e8d22943c1a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207548"
---
# <a name="about-signing"></a><span data-ttu-id="5a710-104">關於簽署</span><span class="sxs-lookup"><span data-stu-id="5a710-104">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="5a710-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="5a710-105">Short description</span></span>
<span data-ttu-id="5a710-106">說明如何簽署腳本，讓它們符合 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="5a710-106">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="5a710-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="5a710-107">Long description</span></span>

<span data-ttu-id="5a710-108">受限制的執行原則不允許執行任何腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-108">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="5a710-109">**AllSigned** 和 **RemoteSigned** 執行原則會防止 PowerShell 執行沒有數位簽章的腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-109">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="5a710-110">本主題說明如何執行未簽署的選取腳本，即使執行原則是 **RemoteSigned** ，以及如何簽署腳本以供自己使用。</span><span class="sxs-lookup"><span data-stu-id="5a710-110">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned** , and how to sign scripts for your own use.</span></span>

<span data-ttu-id="5a710-111">如需 PowerShell 執行原則的詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="5a710-111">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="5a710-112">允許已簽署的腳本執行</span><span class="sxs-lookup"><span data-stu-id="5a710-112">To permit signed scripts to run</span></span>

<span data-ttu-id="5a710-113">當您第一次在電腦上啟動 PowerShell 時， **受限制** 的執行原則 (預設) 可能會生效。</span><span class="sxs-lookup"><span data-stu-id="5a710-113">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="5a710-114">**受限制** 的原則不允許執行任何腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-114">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="5a710-115">若要在您的電腦上尋找有效的執行原則，請輸入：</span><span class="sxs-lookup"><span data-stu-id="5a710-115">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="5a710-116">若要執行您在本機電腦上撰寫的未簽署腳本，以及其他使用者的已簽署腳本，請使用 [以系統管理員身分執行] 選項啟動 PowerShell，然後使用下列命令將電腦上的執行原則變更為 **RemoteSigned** ：</span><span class="sxs-lookup"><span data-stu-id="5a710-116">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned** :</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="5a710-117">如需詳細資訊，請參閱 Cmdlet 的說明主題 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="5a710-117">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="5a710-118">使用 RemoteSigned 執行原則執行未簽署的腳本</span><span class="sxs-lookup"><span data-stu-id="5a710-118">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="5a710-119">如果您的 PowerShell 執行原則是 **RemoteSigned** ，powershell 將不會執行從網際網路下載的未簽署腳本，包括您透過電子郵件和立即訊息程式收到的未簽署腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-119">If your PowerShell execution policy is **RemoteSigned** , PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="5a710-120">如果您嘗試執行下載的腳本，PowerShell 會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="5a710-120">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="5a710-121">執行腳本之前，請先檢查程式碼，以確定您信任它。</span><span class="sxs-lookup"><span data-stu-id="5a710-121">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="5a710-122">腳本的效果與任何可執行檔程式相同。</span><span class="sxs-lookup"><span data-stu-id="5a710-122">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="5a710-123">若要執行未簽署的腳本，請使用 Unblock-File Cmdlet，或使用下列程式。</span><span class="sxs-lookup"><span data-stu-id="5a710-123">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="5a710-124">將腳本檔案儲存在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5a710-124">Save the script file on your computer.</span></span>
2. <span data-ttu-id="5a710-125">按一下 [開始]，按一下 [我的電腦]，然後找出已儲存的腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="5a710-125">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="5a710-126">在腳本檔案上按一下滑鼠右鍵，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="5a710-126">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="5a710-127">按一下 [解除封鎖]。</span><span class="sxs-lookup"><span data-stu-id="5a710-127">Click Unblock.</span></span>

<span data-ttu-id="5a710-128">如果從網際網路下載的腳本經過數位簽署，但您尚未選擇信任其發行者，則 PowerShell 會顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="5a710-128">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="5a710-129">如果您信任發行者，請選取 [執行一次] 或 [永遠執行]。</span><span class="sxs-lookup"><span data-stu-id="5a710-129">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="5a710-130">如果您不信任發行者，請選取 [永不執行] 或 [不要執行]。</span><span class="sxs-lookup"><span data-stu-id="5a710-130">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="5a710-131">如果您選取 [永不執行] 或 [永遠執行]，PowerShell 將不會再次提示您輸入此發行者。</span><span class="sxs-lookup"><span data-stu-id="5a710-131">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="5a710-132">簽署腳本的方法</span><span class="sxs-lookup"><span data-stu-id="5a710-132">Methods of signing scripts</span></span>

<span data-ttu-id="5a710-133">您可以簽署您所撰寫的腳本，以及您從其他來源取得的腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-133">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="5a710-134">簽署任何腳本之前，請檢查每個命令以確認可安全執行。</span><span class="sxs-lookup"><span data-stu-id="5a710-134">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="5a710-135">如需程式碼簽署的最佳作法，請參閱 [程式碼簽署最佳做法](/previous-versions/windows/hardware/design/dn653556(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5a710-135">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="5a710-136">如需如何簽署指令檔的詳細資訊，請參閱 [get-authenticodesignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)。</span><span class="sxs-lookup"><span data-stu-id="5a710-136">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="5a710-137">在 `New-SelfSignedCertificate` PowerShell 3.0 的 PKI 模組中引進的 Cmdlet 會建立適用于測試的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-137">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="5a710-138">如需詳細資訊，請參閱 New-SelfSignedCertificate Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="5a710-138">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="5a710-139">若要將數位簽章新增至腳本，您必須使用程式碼簽署憑證來簽署。</span><span class="sxs-lookup"><span data-stu-id="5a710-139">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="5a710-140">有兩種類型的憑證適用于簽署腳本檔案：</span><span class="sxs-lookup"><span data-stu-id="5a710-140">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="5a710-141">憑證授權單位單位所建立的憑證：為了付費，公開憑證授權單位單位會驗證您的身分識別，並提供程式碼簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-141">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="5a710-142">當您向知名的憑證授權單位單位購買憑證時，您可以與其他執行 Windows 的電腦上的使用者共用您的腳本，因為這些電腦信任憑證授權單位單位。</span><span class="sxs-lookup"><span data-stu-id="5a710-142">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="5a710-143">您建立的憑證：您可以建立自我簽署的憑證，讓您的電腦成為建立憑證的授權單位。</span><span class="sxs-lookup"><span data-stu-id="5a710-143">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="5a710-144">此憑證是免費的，可讓您在電腦上撰寫、簽署和執行腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-144">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="5a710-145">不過，自我簽署憑證所簽署的腳本將不會在其他電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="5a710-145">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="5a710-146">一般而言，您只會使用自我簽署的憑證來簽署您自行撰寫用的腳本，以及簽署您從已驗證為安全的其他來源取得的腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-146">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="5a710-147">它並不適用于將共用的腳本，即使在企業內也是如此。</span><span class="sxs-lookup"><span data-stu-id="5a710-147">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="5a710-148">如果您建立自我簽署憑證，請務必在您的憑證上啟用強式私密金鑰保護。</span><span class="sxs-lookup"><span data-stu-id="5a710-148">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="5a710-149">這可防止惡意程式代表您簽署腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-149">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="5a710-150">本主題的結尾包含這些指示。</span><span class="sxs-lookup"><span data-stu-id="5a710-150">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="5a710-151">建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="5a710-151">Create a self-signed certificate</span></span>

<span data-ttu-id="5a710-152">若要在中建立自我簽署憑證，請使用 `New-SelfSignedCertificate` PKI 模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a710-152">To create a self-signed certificate in use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="5a710-153">此模組是在 PowerShell 3.0 中引進，且包含在 Windows 8 和 Windows Server 2012 中。</span><span class="sxs-lookup"><span data-stu-id="5a710-153">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="5a710-154">如需詳細資訊，請參閱 Cmdlet 的說明主題 `New-SelfSignedCertificate` 。</span><span class="sxs-lookup"><span data-stu-id="5a710-154">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="5a710-155">若要在舊版 Windows 中建立自我簽署憑證，請使用憑證建立工具 `MakeCert.exe` 。</span><span class="sxs-lookup"><span data-stu-id="5a710-155">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="5a710-156">這項工具組含在 Microsoft .NET SDK (1.1 版和更新版本中) 和 Microsoft Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="5a710-156">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="5a710-157">如需有關 MakeCert.exe 工具的語法和參數描述的詳細資訊，請參閱 [憑證建立工具 ( # A1) ](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))。</span><span class="sxs-lookup"><span data-stu-id="5a710-157">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="5a710-158">若要使用 MakeCert.exe 工具來建立憑證，請在 [SDK 命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="5a710-158">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="5a710-159">注意：第一個命令會建立您電腦的本機憑證授權單位單位。</span><span class="sxs-lookup"><span data-stu-id="5a710-159">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="5a710-160">第二個命令會從憑證授權單位單位產生個人憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-160">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="5a710-161">注意：您可以在命令出現時，完全複製或輸入命令。</span><span class="sxs-lookup"><span data-stu-id="5a710-161">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="5a710-162">雖然您可以變更憑證名稱，但不需要任何替代。</span><span class="sxs-lookup"><span data-stu-id="5a710-162">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="5a710-163">MakeCert.exe 工具會提示您輸入私密金鑰密碼。</span><span class="sxs-lookup"><span data-stu-id="5a710-163">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="5a710-164">密碼可確保沒有人可在未經您同意的情況下，使用或存取該憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-164">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="5a710-165">建立並輸入您可以記住的密碼。</span><span class="sxs-lookup"><span data-stu-id="5a710-165">Create and enter a password that you can remember.</span></span> <span data-ttu-id="5a710-166">您稍後將會使用此密碼來取得憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-166">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="5a710-167">若要確認憑證是否已正確產生，請使用下列命令來取得電腦上憑證存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-167">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="5a710-168">您在檔案系統目錄中找不到憑證檔案。</span><span class="sxs-lookup"><span data-stu-id="5a710-168">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="5a710-169">在 PowerShell 提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="5a710-169">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="5a710-170">此命令會使用 PowerShell 憑證提供者來查看憑證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5a710-170">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="5a710-171">如果已建立憑證，則輸出會在顯示中顯示識別憑證的憑證 **指紋** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a710-171">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="5a710-172">簽署腳本</span><span class="sxs-lookup"><span data-stu-id="5a710-172">Sign a script</span></span>

<span data-ttu-id="5a710-173">建立自我簽署憑證之後，您就可以簽署腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-173">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="5a710-174">如果您使用 **AllSigned** 執行原則，簽署腳本會允許您在電腦上執行腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-174">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="5a710-175">下列範例腳本會 `Add-Signature.ps1` 簽署腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-175">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="5a710-176">但是，如果您使用 **AllSigned** 執行原則，則必須先簽署腳本， `Add-Signature.ps1` 然後再執行它。</span><span class="sxs-lookup"><span data-stu-id="5a710-176">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a710-177">您必須使用 ASCII 或 UTF8NoBOM 編碼來儲存腳本。您可以簽署使用不同編碼方式的腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="5a710-177">The script must be saved using ASCII or UTF8NoBOM encoding.You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="5a710-178">但是腳本無法執行，或包含腳本的模組無法匯入。</span><span class="sxs-lookup"><span data-stu-id="5a710-178">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="5a710-179">若要使用此腳本，請將下列文字複製到文字檔中，並將其命名為 `Add-Signature.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="5a710-179">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="5a710-180">若要簽署 `Add-Signature.ps1` 腳本檔案，請在 PowerShell 命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5a710-180">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="5a710-181">腳本簽署之後，您就可以在本機電腦上執行它。</span><span class="sxs-lookup"><span data-stu-id="5a710-181">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="5a710-182">不過，腳本不會在 PowerShell 執行原則需要來自受信任授權單位的數位簽章之電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="5a710-182">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="5a710-183">如果您嘗試，PowerShell 會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="5a710-183">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="5a710-184">如果當您執行未寫入的腳本時，PowerShell 會顯示此訊息，請將檔案視為處理任何未簽署的腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-184">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="5a710-185">檢查程式碼，以判斷您是否可以信任腳本。</span><span class="sxs-lookup"><span data-stu-id="5a710-185">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="5a710-186">為您的憑證啟用強式私密金鑰保護</span><span class="sxs-lookup"><span data-stu-id="5a710-186">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="5a710-187">如果您的電腦上有私人憑證，惡意軟體可能會代表您簽署腳本，以授權 PowerShell 執行它們。</span><span class="sxs-lookup"><span data-stu-id="5a710-187">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="5a710-188">若要防止您自動簽署，請使用憑證管理員將 `Certmgr.exe` 簽署憑證匯出至檔案 `.pfx` 。</span><span class="sxs-lookup"><span data-stu-id="5a710-188">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="5a710-189">憑證管理員包含在 Microsoft .NET SDK、Microsoft Windows SDK 和 internet Explorer 中。</span><span class="sxs-lookup"><span data-stu-id="5a710-189">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="5a710-190">若要匯出憑證：</span><span class="sxs-lookup"><span data-stu-id="5a710-190">To export the certificate:</span></span>

1. <span data-ttu-id="5a710-191">啟動 [憑證管理員]。</span><span class="sxs-lookup"><span data-stu-id="5a710-191">Start Certificate Manager.</span></span>
2. <span data-ttu-id="5a710-192">選取 PowerShell 本機憑證根目錄所發行的憑證。</span><span class="sxs-lookup"><span data-stu-id="5a710-192">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="5a710-193">按一下 [匯出]，以啟動 [憑證匯出嚮導]。</span><span class="sxs-lookup"><span data-stu-id="5a710-193">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="5a710-194">選取 [是，匯出私密金鑰]，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="5a710-194">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="5a710-195">選取 [啟用加強保護]。</span><span class="sxs-lookup"><span data-stu-id="5a710-195">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="5a710-196">輸入密碼，然後再輸入一次以確認。</span><span class="sxs-lookup"><span data-stu-id="5a710-196">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="5a710-197">輸入副檔名為 .pfx 的檔案名。</span><span class="sxs-lookup"><span data-stu-id="5a710-197">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="5a710-198">按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="5a710-198">Click Finish.</span></span>

<span data-ttu-id="5a710-199">若要重新匯入憑證：</span><span class="sxs-lookup"><span data-stu-id="5a710-199">To re-import the certificate:</span></span>

1. <span data-ttu-id="5a710-200">啟動 [憑證管理員]。</span><span class="sxs-lookup"><span data-stu-id="5a710-200">Start Certificate Manager.</span></span>
2. <span data-ttu-id="5a710-201">按一下 [匯入] 以啟動 [憑證匯入嚮導]。</span><span class="sxs-lookup"><span data-stu-id="5a710-201">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="5a710-202">開啟您在匯出程式期間建立的 .pfx 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="5a710-202">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="5a710-203">在 [密碼] 頁面上，選取 [啟用加強私密金鑰保護]，然後輸入您在匯出過程中指派的密碼。</span><span class="sxs-lookup"><span data-stu-id="5a710-203">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="5a710-204">選取 [個人] 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="5a710-204">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="5a710-205">按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="5a710-205">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="5a710-206">防止簽章過期</span><span class="sxs-lookup"><span data-stu-id="5a710-206">Prevent the signature from expiring</span></span>

<span data-ttu-id="5a710-207">在簽署憑證到期之前，腳本中的數位簽章是有效的，只要時間戳記伺服器可以確認簽署憑證有效時腳本已簽署。</span><span class="sxs-lookup"><span data-stu-id="5a710-207">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="5a710-208">因為大部分的簽署憑證僅適用于一年，所以使用時間戳伺服器可確保使用者可以使用您的腳本數年的時間。</span><span class="sxs-lookup"><span data-stu-id="5a710-208">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a710-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a710-209">See also</span></span>

[<span data-ttu-id="5a710-210">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="5a710-210">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="5a710-211">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="5a710-211">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="5a710-212">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="5a710-212">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="5a710-213">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="5a710-213">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="5a710-214">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="5a710-214">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="5a710-215">[程式碼簽署簡介](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5a710-215">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>
