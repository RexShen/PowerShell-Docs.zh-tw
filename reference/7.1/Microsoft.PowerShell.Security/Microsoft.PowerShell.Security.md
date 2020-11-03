---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: a94c8c7e-9810-47c0-b8af-65089c13a35a
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
schema: 2.0.0
title: Microsoft.PowerShell.Security
ms.openlocfilehash: 2c9ec2f3e5c63f550698e7331e19252a865aeb8d
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "93206432"
---
# <span data-ttu-id="a46dd-103">Microsoft.PowerShell.Security 模組</span><span class="sxs-lookup"><span data-stu-id="a46dd-103">Microsoft.PowerShell.Security Module</span></span>

## <span data-ttu-id="a46dd-104">描述</span><span class="sxs-lookup"><span data-stu-id="a46dd-104">Description</span></span>

<span data-ttu-id="a46dd-105">本章節包含與 PowerShell Microsoft. PowerShell. 安全性模組一起安裝之 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="a46dd-105">This section contains the help topics for the cmdlets that are installed with PowerShell Microsoft.PowerShell.Security module.</span></span> <span data-ttu-id="a46dd-106">安全性模組包含管理 Windows 基本安全性功能的 Cmdlet 與提供者。</span><span class="sxs-lookup"><span data-stu-id="a46dd-106">The Security module contains cmdlets and providers that manage the basic security features of Windows.</span></span>

## <span data-ttu-id="a46dd-107">Microsoft. 安全性 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a46dd-107">Microsoft.PowerShell.Security Cmdlets</span></span>

### [<span data-ttu-id="a46dd-108">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="a46dd-108">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)
<span data-ttu-id="a46dd-109">將安全字串轉換成加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="a46dd-109">Converts a secure string to an encrypted standard string.</span></span>

### [<span data-ttu-id="a46dd-110">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="a46dd-110">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)
<span data-ttu-id="a46dd-111">將加密標準字串轉換成安全字串。</span><span class="sxs-lookup"><span data-stu-id="a46dd-111">Converts encrypted standard strings to secure strings.</span></span>

### [<span data-ttu-id="a46dd-112">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="a46dd-112">Get-Acl</span></span>](Get-Acl.md)
<span data-ttu-id="a46dd-113">取得資源 (例如檔案或登錄機碼) 的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="a46dd-113">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

### [<span data-ttu-id="a46dd-114">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a46dd-114">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)
<span data-ttu-id="a46dd-115">取得檔案的 Authenticode 簽章的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a46dd-115">Gets information about the Authenticode signature for a file.</span></span>

### [<span data-ttu-id="a46dd-116">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="a46dd-116">Get-CmsMessage</span></span>](Get-CmsMessage.md)
<span data-ttu-id="a46dd-117">使用密碼編譯訊息語法格式來取得已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="a46dd-117">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

### [<span data-ttu-id="a46dd-118">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="a46dd-118">Get-Credential</span></span>](Get-Credential.md)
<span data-ttu-id="a46dd-119">依據使用者名稱與密碼取得認證物件。</span><span class="sxs-lookup"><span data-stu-id="a46dd-119">Gets a credential object based on a user name and password.</span></span>

### [<span data-ttu-id="a46dd-120">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="a46dd-120">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)
<span data-ttu-id="a46dd-121">取得目前工作階段的執行原則。</span><span class="sxs-lookup"><span data-stu-id="a46dd-121">Gets the execution policies for the current session.</span></span>

### [<span data-ttu-id="a46dd-122">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="a46dd-122">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)
<span data-ttu-id="a46dd-123">取得電腦上 PFX 憑證檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a46dd-123">Gets information about PFX certificate files on the computer.</span></span>

### [<span data-ttu-id="a46dd-124">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a46dd-124">New-FileCatalog</span></span>](New-FileCatalog.md)
<span data-ttu-id="a46dd-125">建立 Windows 類別目錄檔案，其中包含指定路徑中檔案和資料夾的密碼編譯雜湊。</span><span class="sxs-lookup"><span data-stu-id="a46dd-125">Creates a Windows catalog file containing cryptographic hashes for files and folders in specified paths.</span></span>

### [<span data-ttu-id="a46dd-126">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="a46dd-126">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)
<span data-ttu-id="a46dd-127">使用密碼編譯訊息語法格式來加密內容。</span><span class="sxs-lookup"><span data-stu-id="a46dd-127">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

### [<span data-ttu-id="a46dd-128">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="a46dd-128">Set-Acl</span></span>](Set-Acl.md)
<span data-ttu-id="a46dd-129">變更指定項目的安全性描述元，例如檔案或登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="a46dd-129">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

### [<span data-ttu-id="a46dd-130">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a46dd-130">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
<span data-ttu-id="a46dd-131">將 Authenticode 簽章新增至 PowerShell 腳本或其他檔案。</span><span class="sxs-lookup"><span data-stu-id="a46dd-131">Adds an Authenticode signature to a PowerShell script or other file.</span></span>

### [<span data-ttu-id="a46dd-132">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a46dd-132">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
<span data-ttu-id="a46dd-133">設定 Windows 電腦的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="a46dd-133">Sets the PowerShell execution policies for Windows computers.</span></span>

### [<span data-ttu-id="a46dd-134">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a46dd-134">Test-FileCatalog</span></span>](Test-FileCatalog.md)
<span data-ttu-id="a46dd-135">驗證目錄檔案中包含的雜湊 ( .cat) 是否符合實際檔案的雜湊，以便驗證其真實性。</span><span class="sxs-lookup"><span data-stu-id="a46dd-135">Validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

### [<span data-ttu-id="a46dd-136">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="a46dd-136">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
<span data-ttu-id="a46dd-137">使用密碼編譯訊息語法格式來解密已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="a46dd-137">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

