---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 67bb56a50f452475ba12abb2fccaeeaf5785c8b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204736"
---
# <span data-ttu-id="79555-103">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="79555-103">Get-PfxCertificate</span></span>

## <span data-ttu-id="79555-104">概要</span><span class="sxs-lookup"><span data-stu-id="79555-104">SYNOPSIS</span></span>
<span data-ttu-id="79555-105">取得電腦上 PFX 憑證檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79555-105">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="79555-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79555-106">SYNTAX</span></span>

### <span data-ttu-id="79555-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="79555-107">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="79555-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="79555-108">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="79555-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="79555-109">DESCRIPTION</span></span>

<span data-ttu-id="79555-110">`Get-PfxCertificate`Cmdlet 會取得代表每個指定 PFX 憑證檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="79555-110">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="79555-111">PFX 檔案包含憑證和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="79555-111">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="79555-112">範例</span><span class="sxs-lookup"><span data-stu-id="79555-112">EXAMPLES</span></span>

### <span data-ttu-id="79555-113">範例1：取得 PFX 憑證</span><span class="sxs-lookup"><span data-stu-id="79555-113">Example 1: Get a PFX certificate</span></span>

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

<span data-ttu-id="79555-114">此命令會取得系統上的 Test .pfx 憑證檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79555-114">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="79555-115">範例2：從遠端電腦取得 PFX 憑證</span><span class="sxs-lookup"><span data-stu-id="79555-115">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="79555-116">此命令會從 Server01 遠端電腦取得 PFX 憑證檔案。</span><span class="sxs-lookup"><span data-stu-id="79555-116">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="79555-117">它是用 `Invoke-Command` 來 `Get-PfxCertificate` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="79555-117">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="79555-118">如果 PFX 憑證檔案未受密碼保護，的 **Authentication** 參數值 `Invoke-Command` 必須是 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="79555-118">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="79555-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79555-119">PARAMETERS</span></span>

### <span data-ttu-id="79555-120">-FilePath</span><span class="sxs-lookup"><span data-stu-id="79555-120">-FilePath</span></span>

<span data-ttu-id="79555-121">指定受保護檔案之 PFX 檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="79555-121">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="79555-122">如果您指定此參數的值，則不需要 `-FilePath` 在命令列輸入。</span><span class="sxs-lookup"><span data-stu-id="79555-122">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="79555-123">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="79555-123">-LiteralPath</span></span>

<span data-ttu-id="79555-124">受保護檔案之 PFX 檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="79555-124">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="79555-125">**LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="79555-125">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="79555-126">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="79555-126">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="79555-127">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="79555-127">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="79555-128">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="79555-128">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="79555-129">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="79555-129">-NoPromptForPassword</span></span>

<span data-ttu-id="79555-130">抑制提示輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="79555-130">Suppresses prompting for a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79555-131">-Password</span><span class="sxs-lookup"><span data-stu-id="79555-131">-Password</span></span>

<span data-ttu-id="79555-132">指定存取憑證檔案所需的密碼 `.pfx` 。</span><span class="sxs-lookup"><span data-stu-id="79555-132">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="79555-133">此參數是在 PowerShell 6.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="79555-133">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="79555-134">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="79555-134">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79555-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79555-135">CommonParameters</span></span>

<span data-ttu-id="79555-136">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="79555-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79555-137">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="79555-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79555-138">輸入</span><span class="sxs-lookup"><span data-stu-id="79555-138">INPUTS</span></span>

### <span data-ttu-id="79555-139">System.String</span><span class="sxs-lookup"><span data-stu-id="79555-139">System.String</span></span>

<span data-ttu-id="79555-140">您可以使用管線將包含檔案路徑的字串傳送至 `Get-PfxCertificate` 。</span><span class="sxs-lookup"><span data-stu-id="79555-140">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="79555-141">輸出</span><span class="sxs-lookup"><span data-stu-id="79555-141">OUTPUTS</span></span>

### <span data-ttu-id="79555-142">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="79555-142">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="79555-143">`Get-PfxCertificate` 針對取得的每個憑證傳回物件。</span><span class="sxs-lookup"><span data-stu-id="79555-143">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="79555-144">注意</span><span class="sxs-lookup"><span data-stu-id="79555-144">NOTES</span></span>

<span data-ttu-id="79555-145">使用 `Invoke-Command` `Get-PfxCertificate` 指令程式從遠端執行命令，且 PFX 憑證檔案未受密碼保護時，的 **Authentication** 參數值 `Invoke-Command` 必須是 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="79555-145">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="79555-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="79555-146">RELATED LINKS</span></span>

[<span data-ttu-id="79555-147">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="79555-147">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="79555-148">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="79555-148">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
