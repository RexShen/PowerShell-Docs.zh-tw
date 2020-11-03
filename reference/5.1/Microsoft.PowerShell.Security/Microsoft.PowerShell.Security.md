---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=390786
Help Version: 5.2.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: a94c8c7e-9810-47c0-b8af-65089c13a35a
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
schema: 2.0.0
title: Microsoft.PowerShell.Security
ms.openlocfilehash: ee59f21ac61ee6e5086338e5ee30e4937d1f3f2f
ms.sourcegitcommit: 3571b9e87e8881adbf7984cda46a63891039a987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "93201067"
---
# <span data-ttu-id="1112a-103">Microsoft.PowerShell.Security 模組</span><span class="sxs-lookup"><span data-stu-id="1112a-103">Microsoft.PowerShell.Security Module</span></span>

## <span data-ttu-id="1112a-104">描述</span><span class="sxs-lookup"><span data-stu-id="1112a-104">Description</span></span>

<span data-ttu-id="1112a-105">本章節包含與 PowerShell Microsoft. PowerShell. 安全性模組一起安裝之 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="1112a-105">This section contains the help topics for the cmdlets that are installed with PowerShell Microsoft.PowerShell.Security module.</span></span> <span data-ttu-id="1112a-106">安全性模組包含管理 Windows 基本安全性功能的 Cmdlet 與提供者。</span><span class="sxs-lookup"><span data-stu-id="1112a-106">The Security module contains cmdlets and providers that manage the basic security features of Windows.</span></span>

## <span data-ttu-id="1112a-107">Microsoft. 安全性 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1112a-107">Microsoft.PowerShell.Security Cmdlets</span></span>

### [<span data-ttu-id="1112a-108">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="1112a-108">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)
<span data-ttu-id="1112a-109">將安全字串轉換成加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="1112a-109">Converts a secure string to an encrypted standard string.</span></span>

### [<span data-ttu-id="1112a-110">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="1112a-110">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)
<span data-ttu-id="1112a-111">將加密標準字串轉換成安全字串。</span><span class="sxs-lookup"><span data-stu-id="1112a-111">Converts encrypted standard strings to secure strings.</span></span>

### [<span data-ttu-id="1112a-112">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="1112a-112">Get-Acl</span></span>](Get-Acl.md)
<span data-ttu-id="1112a-113">取得資源 (例如檔案或登錄機碼) 的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="1112a-113">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

### [<span data-ttu-id="1112a-114">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1112a-114">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)
<span data-ttu-id="1112a-115">取得檔案的 Authenticode 簽章的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1112a-115">Gets information about the Authenticode signature for a file.</span></span>

### [<span data-ttu-id="1112a-116">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="1112a-116">Get-CmsMessage</span></span>](Get-CmsMessage.md)
<span data-ttu-id="1112a-117">使用密碼編譯訊息語法格式來取得已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="1112a-117">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

### [<span data-ttu-id="1112a-118">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="1112a-118">Get-Credential</span></span>](Get-Credential.md)
<span data-ttu-id="1112a-119">依據使用者名稱與密碼取得認證物件。</span><span class="sxs-lookup"><span data-stu-id="1112a-119">Gets a credential object based on a user name and password.</span></span>

### [<span data-ttu-id="1112a-120">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="1112a-120">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)
<span data-ttu-id="1112a-121">取得目前工作階段的執行原則。</span><span class="sxs-lookup"><span data-stu-id="1112a-121">Gets the execution policies for the current session.</span></span>

### [<span data-ttu-id="1112a-122">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="1112a-122">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)
<span data-ttu-id="1112a-123">取得電腦上 .pfx 憑證檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1112a-123">Gets information about .pfx certificate files on the computer.</span></span>

### [<span data-ttu-id="1112a-124">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="1112a-124">New-FileCatalog</span></span>](New-FileCatalog.md)
<span data-ttu-id="1112a-125">建立 Windows 類別目錄檔案，其中包含指定路徑中檔案和資料夾的密碼編譯雜湊。</span><span class="sxs-lookup"><span data-stu-id="1112a-125">Creates a Windows catalog file containing cryptographic hashes for files and folders in specified paths.</span></span>

### [<span data-ttu-id="1112a-126">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="1112a-126">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)
<span data-ttu-id="1112a-127">使用密碼編譯訊息語法格式來加密內容。</span><span class="sxs-lookup"><span data-stu-id="1112a-127">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

### [<span data-ttu-id="1112a-128">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="1112a-128">Set-Acl</span></span>](Set-Acl.md)
<span data-ttu-id="1112a-129">變更指定項目的安全性描述元，例如檔案或登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="1112a-129">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

### [<span data-ttu-id="1112a-130">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1112a-130">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
<span data-ttu-id="1112a-131">將 Authenticode 簽章新增至 PowerShell 腳本或其他檔案。</span><span class="sxs-lookup"><span data-stu-id="1112a-131">Adds an Authenticode signature to a PowerShell script or other file.</span></span>

### [<span data-ttu-id="1112a-132">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="1112a-132">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
<span data-ttu-id="1112a-133">變更 PowerShell 執行原則的使用者喜好設定。</span><span class="sxs-lookup"><span data-stu-id="1112a-133">Changes the user preference for the PowerShell execution policy.</span></span>

### [<span data-ttu-id="1112a-134">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="1112a-134">Test-FileCatalog</span></span>](Test-FileCatalog.md)
<span data-ttu-id="1112a-135">藉由比較檔案和資料夾的路徑相關雜湊與目錄中記錄的雜湊來驗證檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="1112a-135">Validates files and folders by comparing their path-sensitive hashes against those recorded in a catalog.</span></span>

### [<span data-ttu-id="1112a-136">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="1112a-136">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
<span data-ttu-id="1112a-137">使用密碼編譯訊息語法格式來解密已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="1112a-137">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>
