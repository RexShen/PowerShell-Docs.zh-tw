---
description: PowerShell 會將引擎、提供者和 Cmdlet 的內部作業記錄至 Windows 事件記錄檔。
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: 960394838097e4bfad1af5f4f0af7a813a50e761
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355012"
---
# <a name="about-logging-windows"></a><span data-ttu-id="680f0-104">關於記錄視窗</span><span class="sxs-lookup"><span data-stu-id="680f0-104">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="680f0-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="680f0-105">Short description</span></span>
<span data-ttu-id="680f0-106">PowerShell 會將引擎、提供者和 Cmdlet 的內部作業記錄至 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="680f0-106">PowerShell logs internal operations from the engine, providers, and cmdlets to the Windows event log.</span></span>

## <a name="long-description"></a><span data-ttu-id="680f0-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="680f0-107">Long description</span></span>

<span data-ttu-id="680f0-108">PowerShell 會記錄 PowerShell 作業的詳細資料，例如啟動和停止引擎和提供者，以及執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="680f0-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="680f0-109">Windows PowerShell 版本3.0、4.0、5.0 和5.1 包含 Windows 事件記錄檔的 **EventLog** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="680f0-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="680f0-110">在這些版本中，若要顯示 **EventLog** Cmdlet 的清單，請輸入： `Get-Command -Noun EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="680f0-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="680f0-111">如需詳細資訊，請參閱 Windows PowerShell 之版本的 Cmdlet 檔和 about_EventLogs。</span><span class="sxs-lookup"><span data-stu-id="680f0-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="680f0-112">在 Windows 上查看 PowerShell 事件記錄檔專案</span><span class="sxs-lookup"><span data-stu-id="680f0-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="680f0-113">您可以使用 Windows 事件檢視器來查看 PowerShell 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="680f0-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="680f0-114">事件記錄檔位於 [應用程式和服務記錄檔] 群組中，並命名為 `PowerShellCore` 。</span><span class="sxs-lookup"><span data-stu-id="680f0-114">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="680f0-115">相關聯的 ETW 提供者 `GUID` 為 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 。</span><span class="sxs-lookup"><span data-stu-id="680f0-115">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="680f0-116">啟用腳本區塊記錄時，PowerShell 會將下列事件記錄到記錄檔中 `PowerShellCore/Operational` ：</span><span class="sxs-lookup"><span data-stu-id="680f0-116">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|  <span data-ttu-id="680f0-117">欄位</span><span class="sxs-lookup"><span data-stu-id="680f0-117">Field</span></span>  |       <span data-ttu-id="680f0-118">值</span><span class="sxs-lookup"><span data-stu-id="680f0-118">Value</span></span>       |
| ------- | ----------------- |
| <span data-ttu-id="680f0-119">EventId</span><span class="sxs-lookup"><span data-stu-id="680f0-119">EventId</span></span> | `4104` / `0x1008` |
| <span data-ttu-id="680f0-120">通路</span><span class="sxs-lookup"><span data-stu-id="680f0-120">Channel</span></span> | `Operational`     |
| <span data-ttu-id="680f0-121">層級</span><span class="sxs-lookup"><span data-stu-id="680f0-121">Level</span></span>   | `Verbose`         |
| <span data-ttu-id="680f0-122">OpCode</span><span class="sxs-lookup"><span data-stu-id="680f0-122">Opcode</span></span>  | `Create`          |
| <span data-ttu-id="680f0-123">Task</span><span class="sxs-lookup"><span data-stu-id="680f0-123">Task</span></span>    | `CommandStart`    |
| <span data-ttu-id="680f0-124">關鍵字</span><span class="sxs-lookup"><span data-stu-id="680f0-124">Keyword</span></span> | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="680f0-125">在 Windows 上註冊 PowerShell 事件提供者</span><span class="sxs-lookup"><span data-stu-id="680f0-125">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="680f0-126">不同于 Linux 或 macOS，Windows 需要註冊事件提供者，然後才能將事件寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="680f0-126">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="680f0-127">若要啟用 PowerShell 事件提供者，請從已提升許可權的 PowerShell 提示字元中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="680f0-127">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="680f0-128">在 Windows 上取消註冊 PowerShell 事件提供者</span><span class="sxs-lookup"><span data-stu-id="680f0-128">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="680f0-129">註冊事件提供者會在用來解碼事件的二進位程式庫中放置鎖定。</span><span class="sxs-lookup"><span data-stu-id="680f0-129">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="680f0-130">若要更新此程式庫，必須取消註冊此提供者，才能釋放此鎖定。</span><span class="sxs-lookup"><span data-stu-id="680f0-130">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="680f0-131">若要取消註冊 PowerShell 提供者，請從已提升許可權的 PowerShell 提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="680f0-131">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="680f0-132">更新 PowerShell 之後，請執行 `$PSHOME\RegisterManifest.ps1` 以註冊更新的事件提供者。</span><span class="sxs-lookup"><span data-stu-id="680f0-132">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="680f0-133">啟用腳本區塊記錄</span><span class="sxs-lookup"><span data-stu-id="680f0-133">Enabling Script Block Logging</span></span>

<span data-ttu-id="680f0-134">當您啟用腳本區塊記錄時，PowerShell 會記錄其處理的所有腳本區塊的內容。</span><span class="sxs-lookup"><span data-stu-id="680f0-134">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="680f0-135">啟用之後，任何新的 PowerShell 會話都會記錄此資訊。</span><span class="sxs-lookup"><span data-stu-id="680f0-135">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="680f0-136">建議您在針對診斷目的以外的任何專案使用腳本區塊記錄時，啟用受保護的事件記錄（如下所述）。</span><span class="sxs-lookup"><span data-stu-id="680f0-136">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="680f0-137">您可以透過群組原則或登錄設定來啟用腳本區塊記錄。</span><span class="sxs-lookup"><span data-stu-id="680f0-137">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="680f0-138">使用群組原則</span><span class="sxs-lookup"><span data-stu-id="680f0-138">Using Group Policy</span></span>

<span data-ttu-id="680f0-139">若要啟用自動轉譯，請 `Turn on PowerShell Script Block
Logging` 在群組原則中啟用此功能 `Administrative Templates -> Windows
Components -> Windows PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="680f0-139">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="680f0-140">使用登錄</span><span class="sxs-lookup"><span data-stu-id="680f0-140">Using the Registry</span></span>

<span data-ttu-id="680f0-141">執行下列函式：</span><span class="sxs-lookup"><span data-stu-id="680f0-141">Run the following function:</span></span>

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a><span data-ttu-id="680f0-142">受保護的事件記錄</span><span class="sxs-lookup"><span data-stu-id="680f0-142">Protected Event Logging</span></span>

<span data-ttu-id="680f0-143">提高系統上的記錄層級，可增加記錄內容可能包含機密資料的可能性。</span><span class="sxs-lookup"><span data-stu-id="680f0-143">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="680f0-144">例如，在啟用腳本記錄的情況下，您可以將腳本所使用的認證或其他機密資料寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="680f0-144">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="680f0-145">當已記錄機密資料的電腦遭到入侵時，記錄檔可以為攻擊者提供延伸其觸及範圍所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="680f0-145">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="680f0-146">為了保護這種資訊，Windows 10 引進了受保護的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="680f0-146">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="680f0-147">受保護的事件記錄可讓參與的應用程式加密寫入事件記錄檔的機密資料。</span><span class="sxs-lookup"><span data-stu-id="680f0-147">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="680f0-148">稍後，您可以在更安全且集中式的記錄收集器上解密和處理這些記錄。</span><span class="sxs-lookup"><span data-stu-id="680f0-148">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="680f0-149">使用 IETF 密碼編譯訊息語法 (CMS) 標準來保護事件記錄檔內容。</span><span class="sxs-lookup"><span data-stu-id="680f0-149">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="680f0-150">CMS 使用公開金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="680f0-150">CMS uses public key cryptography.</span></span> <span data-ttu-id="680f0-151">用來加密內容和解密內容的金鑰會分開保存。</span><span class="sxs-lookup"><span data-stu-id="680f0-151">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="680f0-152">公開金鑰可以廣泛共用，而不是機密資料。</span><span class="sxs-lookup"><span data-stu-id="680f0-152">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="680f0-153">使用這個公開金鑰加密的任何內容都只能透過私密金鑰進行解密。</span><span class="sxs-lookup"><span data-stu-id="680f0-153">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="680f0-154">如需公開金鑰加密的詳細資訊，請參閱 [維琪百科-公開金鑰密碼](https://en.wikipedia.org/wiki/Public-key_cryptography)編譯。</span><span class="sxs-lookup"><span data-stu-id="680f0-154">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="680f0-155">若要啟用受保護的事件記錄原則，請將公開金鑰部署至具有要保護之事件記錄檔資料的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="680f0-155">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="680f0-156">相對應的私密金鑰會用來在更安全的位置（例如中央事件記錄檔收集器，或 [SIEM][] 匯總工具）後置處理事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="680f0-156">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="680f0-157">您可以在 Azure 中設定 SIEM。</span><span class="sxs-lookup"><span data-stu-id="680f0-157">You can set up SIEM in Azure.</span></span> <span data-ttu-id="680f0-158">如需詳細資訊，請參閱 [泛型 SIEM 整合](/cloud-app-security/siem)。</span><span class="sxs-lookup"><span data-stu-id="680f0-158">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="680f0-159">透過群組原則啟用受保護的事件記錄</span><span class="sxs-lookup"><span data-stu-id="680f0-159">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="680f0-160">若要啟用受保護的事件記錄，請 `Enable Protected Event Logging` 在群組原則中啟用此功能 `Administrative Templates -> Windows Components
-> Event Logging` 。</span><span class="sxs-lookup"><span data-stu-id="680f0-160">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="680f0-161">這項設定需要加密憑證，您可以使用下列其中一種形式提供：</span><span class="sxs-lookup"><span data-stu-id="680f0-161">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="680f0-162">以64編碼的 x.509 憑證的內容 (例如， `Export` 憑證管理員) 中的選項所提供的內容。</span><span class="sxs-lookup"><span data-stu-id="680f0-162">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="680f0-163">可在本機電腦憑證存放區中找到之憑證的指紋 (可由 PKI 基礎結構) 部署。</span><span class="sxs-lookup"><span data-stu-id="680f0-163">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="680f0-164">憑證 (的完整路徑可以是本機或遠端共用) 。</span><span class="sxs-lookup"><span data-stu-id="680f0-164">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="680f0-165">包含憑證的目錄路徑或憑證 (可以是本機或遠端共用) 。</span><span class="sxs-lookup"><span data-stu-id="680f0-165">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="680f0-166">可在本機電腦憑證存放區中找到之憑證的主體名稱， (可以由 PKI 基礎結構) 來部署。</span><span class="sxs-lookup"><span data-stu-id="680f0-166">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="680f0-167">產生的憑證必須有 `Document Encryption` 增強金鑰使用 `1.3.6.1.4.1.311.80.1` 方法 () ，以及 `Data Encipherment` `Key
Encipherment` 啟用或金鑰使用方式。</span><span class="sxs-lookup"><span data-stu-id="680f0-167">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="680f0-168">私密金鑰不應部署至機器記錄事件。</span><span class="sxs-lookup"><span data-stu-id="680f0-168">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="680f0-169">它應該保留在您解密訊息的安全位置。</span><span class="sxs-lookup"><span data-stu-id="680f0-169">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="680f0-170">解密受保護的事件記錄訊息</span><span class="sxs-lookup"><span data-stu-id="680f0-170">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="680f0-171">下列腳本將會取得和解密，假設您有私密金鑰：</span><span class="sxs-lookup"><span data-stu-id="680f0-171">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="680f0-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="680f0-172">See also</span></span>

[<span data-ttu-id="680f0-173">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="680f0-173">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="680f0-174">PowerShell Blue Team</span><span class="sxs-lookup"><span data-stu-id="680f0-174">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="680f0-175">一般 SIEM 整合</span><span class="sxs-lookup"><span data-stu-id="680f0-175">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
