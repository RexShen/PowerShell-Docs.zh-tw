---
description: PowerShell 會記錄引擎、提供者和 Cmdlet 的內部作業。
keywords: powershell
Locale: en-US
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging
ms.openlocfilehash: 5d061b38b5b0fa45cf0a86c2f5b7e0efcb8d1f7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207639"
---
# <a name="about-logging"></a><span data-ttu-id="51faa-104">關於記錄</span><span class="sxs-lookup"><span data-stu-id="51faa-104">About Logging</span></span>

## <a name="short-description"></a><span data-ttu-id="51faa-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="51faa-105">Short description</span></span>

<span data-ttu-id="51faa-106">PowerShell 會記錄引擎、提供者和 Cmdlet 的內部作業。</span><span class="sxs-lookup"><span data-stu-id="51faa-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="51faa-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="51faa-107">Long description</span></span>

<span data-ttu-id="51faa-108">PowerShell 會記錄 PowerShell 作業的詳細資料，例如啟動和停止引擎和提供者，以及執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="51faa-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="51faa-109">Windows PowerShell 版本3.0、4.0、5.0 和5.1 包含 Windows 事件記錄檔的 **EventLog** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51faa-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="51faa-110">在這些版本中，若要顯示 **EventLog** Cmdlet 的清單，請輸入： `Get-Command -Noun EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="51faa-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="51faa-111">如需詳細資訊，請參閱 Windows PowerShell 之版本的 Cmdlet 檔和 about_EventLogs。</span><span class="sxs-lookup"><span data-stu-id="51faa-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="51faa-112">在 Windows 上查看 PowerShell 事件記錄檔專案</span><span class="sxs-lookup"><span data-stu-id="51faa-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="51faa-113">您可以使用 Windows 事件檢視器來查看 PowerShell 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="51faa-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="51faa-114">事件記錄檔位於 [應用程式和服務記錄檔] 群組中，並命名為 `Microsoft-Windows-PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="51faa-114">The event log is located in the Application and Services Logs group and is named `Microsoft-Windows-PowerShell`.</span></span> <span data-ttu-id="51faa-115">相關聯的 ETW 提供者 `GUID` 為 `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}` 。</span><span class="sxs-lookup"><span data-stu-id="51faa-115">The associated ETW provider `GUID` is `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}`.</span></span>

<span data-ttu-id="51faa-116">啟用腳本區塊記錄時，PowerShell 會將下列事件記錄到記錄檔中 `Microsoft-Windows-PowerShell/Operational` ：</span><span class="sxs-lookup"><span data-stu-id="51faa-116">When Script Block Logging is enabled, PowerShell logs the following events to the `Microsoft-Windows-PowerShell/Operational` log:</span></span>

|<span data-ttu-id="51faa-117">欄位</span><span class="sxs-lookup"><span data-stu-id="51faa-117">Field</span></span>| <span data-ttu-id="51faa-118">值</span><span class="sxs-lookup"><span data-stu-id="51faa-118">Value</span></span>|
|-|-|
|<span data-ttu-id="51faa-119">EventId</span><span class="sxs-lookup"><span data-stu-id="51faa-119">EventId</span></span>|`4104` / `0x1008`|
|<span data-ttu-id="51faa-120">管道</span><span class="sxs-lookup"><span data-stu-id="51faa-120">Channel</span></span>|`Operational`|
|<span data-ttu-id="51faa-121">層級</span><span class="sxs-lookup"><span data-stu-id="51faa-121">Level</span></span>|`Verbose`|
|<span data-ttu-id="51faa-122">OpCode</span><span class="sxs-lookup"><span data-stu-id="51faa-122">Opcode</span></span>|`Create`|
|<span data-ttu-id="51faa-123">工作</span><span class="sxs-lookup"><span data-stu-id="51faa-123">Task</span></span>|`CommandStart`|
|<span data-ttu-id="51faa-124">關鍵字</span><span class="sxs-lookup"><span data-stu-id="51faa-124">Keyword</span></span>|`Runspace`|

## <a name="enabling-script-block-logging"></a><span data-ttu-id="51faa-125">啟用腳本區塊記錄</span><span class="sxs-lookup"><span data-stu-id="51faa-125">Enabling Script Block Logging</span></span>

<span data-ttu-id="51faa-126">當您啟用腳本區塊記錄時，PowerShell 會記錄其處理的所有腳本區塊的內容。</span><span class="sxs-lookup"><span data-stu-id="51faa-126">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="51faa-127">啟用之後，任何新的 PowerShell 會話都會記錄此資訊。</span><span class="sxs-lookup"><span data-stu-id="51faa-127">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="51faa-128">建議您在針對診斷目的以外的任何專案使用腳本區塊記錄時，啟用受保護的事件記錄（如下所述）。</span><span class="sxs-lookup"><span data-stu-id="51faa-128">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="51faa-129">您可以透過群組原則或登錄設定來啟用腳本區塊記錄。</span><span class="sxs-lookup"><span data-stu-id="51faa-129">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="51faa-130">使用群組原則</span><span class="sxs-lookup"><span data-stu-id="51faa-130">Using Group Policy</span></span>

<span data-ttu-id="51faa-131">若要啟用自動轉譯，請 `Turn on PowerShell Script Block
Logging` 在群組原則中啟用此功能 `Administrative Templates -> Windows
Components -> Windows PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="51faa-131">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="51faa-132">使用登錄</span><span class="sxs-lookup"><span data-stu-id="51faa-132">Using the Registry</span></span>

<span data-ttu-id="51faa-133">執行下列函式：</span><span class="sxs-lookup"><span data-stu-id="51faa-133">Run the following function:</span></span>

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

## <a name="protected-event-logging"></a><span data-ttu-id="51faa-134">受保護的事件記錄</span><span class="sxs-lookup"><span data-stu-id="51faa-134">Protected Event Logging</span></span>

<span data-ttu-id="51faa-135">提高系統上的記錄層級，可增加記錄內容可能包含機密資料的可能性。</span><span class="sxs-lookup"><span data-stu-id="51faa-135">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="51faa-136">例如，在啟用腳本記錄的情況下，您可以將腳本所使用的認證或其他機密資料寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="51faa-136">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="51faa-137">當已記錄機密資料的電腦遭到入侵時，記錄檔可以為攻擊者提供延伸其觸及範圍所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="51faa-137">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="51faa-138">為了保護這種資訊，Windows 10 引進了受保護的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="51faa-138">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="51faa-139">受保護的事件記錄可讓參與的應用程式加密寫入事件記錄檔的機密資料。</span><span class="sxs-lookup"><span data-stu-id="51faa-139">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="51faa-140">稍後，您可以在更安全且集中式的記錄收集器上解密和處理這些記錄。</span><span class="sxs-lookup"><span data-stu-id="51faa-140">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="51faa-141">使用 IETF 密碼編譯訊息語法 (CMS) 標準來保護事件記錄檔內容。</span><span class="sxs-lookup"><span data-stu-id="51faa-141">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="51faa-142">CMS 使用公開金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="51faa-142">CMS uses public key cryptography.</span></span> <span data-ttu-id="51faa-143">用來加密內容和解密內容的金鑰會分開保存。</span><span class="sxs-lookup"><span data-stu-id="51faa-143">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="51faa-144">公開金鑰可以廣泛共用，而不是機密資料。</span><span class="sxs-lookup"><span data-stu-id="51faa-144">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="51faa-145">使用這個公開金鑰加密的任何內容都只能透過私密金鑰進行解密。</span><span class="sxs-lookup"><span data-stu-id="51faa-145">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="51faa-146">如需公開金鑰加密的詳細資訊，請參閱 [維琪百科-公開金鑰密碼](https://en.wikipedia.org/wiki/Public-key_cryptography)編譯。</span><span class="sxs-lookup"><span data-stu-id="51faa-146">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="51faa-147">若要啟用受保護的事件記錄原則，請將公開金鑰部署至具有要保護之事件記錄檔資料的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="51faa-147">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="51faa-148">相對應的私密金鑰會用來在更安全的位置（例如中央事件記錄檔收集器，或 [SIEM][] 匯總工具）後置處理事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="51faa-148">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="51faa-149">您可以在 Azure 中設定 SIEM。</span><span class="sxs-lookup"><span data-stu-id="51faa-149">You can set up SIEM in Azure.</span></span> <span data-ttu-id="51faa-150">如需詳細資訊，請參閱 [泛型 SIEM 整合](/cloud-app-security/siem)。</span><span class="sxs-lookup"><span data-stu-id="51faa-150">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="51faa-151">透過群組原則啟用受保護的事件記錄</span><span class="sxs-lookup"><span data-stu-id="51faa-151">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="51faa-152">若要啟用受保護的事件記錄，請 `Enable Protected Event Logging` 在群組原則中啟用此功能 `Administrative Templates -> Windows Components
-> Event Logging` 。</span><span class="sxs-lookup"><span data-stu-id="51faa-152">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="51faa-153">這項設定需要加密憑證，您可以使用下列其中一種形式提供：</span><span class="sxs-lookup"><span data-stu-id="51faa-153">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="51faa-154">以64編碼的 x.509 憑證的內容 (例如， `Export` 憑證管理員) 中的選項所提供的內容。</span><span class="sxs-lookup"><span data-stu-id="51faa-154">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="51faa-155">可在本機電腦憑證存放區中找到之憑證的指紋 (可由 PKI 基礎結構) 部署。</span><span class="sxs-lookup"><span data-stu-id="51faa-155">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="51faa-156">憑證 (的完整路徑可以是本機或遠端共用) 。</span><span class="sxs-lookup"><span data-stu-id="51faa-156">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="51faa-157">包含憑證的目錄路徑或憑證 (可以是本機或遠端共用) 。</span><span class="sxs-lookup"><span data-stu-id="51faa-157">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="51faa-158">可在本機電腦憑證存放區中找到之憑證的主體名稱， (可以由 PKI 基礎結構) 來部署。</span><span class="sxs-lookup"><span data-stu-id="51faa-158">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="51faa-159">產生的憑證必須有 `Document Encryption` 增強金鑰使用 `1.3.6.1.4.1.311.80.1` 方法 () ，以及 `Data Encipherment` `Key
Encipherment` 啟用或金鑰使用方式。</span><span class="sxs-lookup"><span data-stu-id="51faa-159">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="51faa-160">私密金鑰不應部署至機器記錄事件。</span><span class="sxs-lookup"><span data-stu-id="51faa-160">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="51faa-161">它應該保留在您解密訊息的安全位置。</span><span class="sxs-lookup"><span data-stu-id="51faa-161">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="51faa-162">解密受保護的事件記錄訊息</span><span class="sxs-lookup"><span data-stu-id="51faa-162">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="51faa-163">下列腳本將會取得和解密，假設您有私密金鑰：</span><span class="sxs-lookup"><span data-stu-id="51faa-163">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="51faa-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51faa-164">See also</span></span>

[<span data-ttu-id="51faa-165">PowerShell Blue Team</span><span class="sxs-lookup"><span data-stu-id="51faa-165">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="51faa-166">一般 SIEM 整合</span><span class="sxs-lookup"><span data-stu-id="51faa-166">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management