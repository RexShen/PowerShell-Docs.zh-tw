---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: a63386356542f7753d3f1b840da9629fba13dc80
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206195"
---
# <span data-ttu-id="d8caf-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="d8caf-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="d8caf-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8caf-104">SYNOPSIS</span></span>
<span data-ttu-id="d8caf-105">將 SDDL 字串轉換成自訂物件。</span><span class="sxs-lookup"><span data-stu-id="d8caf-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="d8caf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8caf-106">SYNTAX</span></span>

### <span data-ttu-id="d8caf-107">全部</span><span class="sxs-lookup"><span data-stu-id="d8caf-107">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="d8caf-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8caf-108">DESCRIPTION</span></span>

<span data-ttu-id="d8caf-109">此 `ConvertFrom-SddlString` Cmdlet 會將安全描述項定義語言字串轉換為具有下列屬性的自訂 **PSCustomObject** 物件： Owner、Group、objdescriptor.discretionaryacl、SystemAcl 和 RawDescriptor。</span><span class="sxs-lookup"><span data-stu-id="d8caf-109">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="d8caf-110">Owner、Group、Objdescriptor.discretionaryacl 和 SystemAcl 屬性包含 SDDL 字串中所指定存取權限的可讀取文字表示。</span><span class="sxs-lookup"><span data-stu-id="d8caf-110">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="d8caf-111">此 Cmdlet 是在 PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="d8caf-111">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="d8caf-112">範例</span><span class="sxs-lookup"><span data-stu-id="d8caf-112">EXAMPLES</span></span>

### <span data-ttu-id="d8caf-113">範例1：將檔案系統存取權限 SDDL 轉換成 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="d8caf-113">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="d8caf-114">第一個命令會使用 `Get-Acl` Cmdlet 來取得 C：\Windows 資料夾的安全描述項，並將其儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="d8caf-114">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="d8caf-115">第二個命令會使用 `ConvertFrom-SddlString` Cmdlet 來取得 sddl 字串的文字標記法，此物件包含在代表安全描述項之物件的 sddl 屬性中。</span><span class="sxs-lookup"><span data-stu-id="d8caf-115">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="d8caf-116">範例2：將登錄存取權限 SDDL 轉換成 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="d8caf-116">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="d8caf-117">第一個命令會使用 `Get-Acl` Cmdlet 來取得 HKLM： \ SOFTWARE\Microsoft\ 金鑰的安全描述項，並將其儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="d8caf-117">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="d8caf-118">第二個命令會使用 `ConvertFrom-SddlString` Cmdlet 來取得 sddl 字串的文字標記法，此物件包含在代表安全描述項之物件的 sddl 屬性中。</span><span class="sxs-lookup"><span data-stu-id="d8caf-118">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="d8caf-119">它會使用 `-Type` 參數來指定 SDDL 字串代表登錄安全描述項。</span><span class="sxs-lookup"><span data-stu-id="d8caf-119">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="d8caf-120">範例3：使用 ConvertFrom-SddlString 搭配和不使用參數，將登錄存取權限 SDDL 轉換成 PSCustomObject `-Type`</span><span class="sxs-lookup"><span data-stu-id="d8caf-120">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="d8caf-121">第一個命令會使用 `Get-Acl` Cmdlet 來取得 HKLM： \ SOFTWARE\Microsoft\ 金鑰的安全描述項，並將其儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="d8caf-121">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="d8caf-122">第二個命令會使用 `ConvertFrom-SddlString` Cmdlet 來取得 sddl 字串的文字標記法，此物件包含在代表安全描述項之物件的 sddl 屬性中。</span><span class="sxs-lookup"><span data-stu-id="d8caf-122">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="d8caf-123">它不會使用 `-Type` 參數，因此顯示的存取權限是針對檔案系統。</span><span class="sxs-lookup"><span data-stu-id="d8caf-123">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="d8caf-124">第三個命令 `ConvertFrom-SddlString` 會使用 Cmdlet 搭配 `-Type` 參數，因此傳回的存取權限是針對登錄。</span><span class="sxs-lookup"><span data-stu-id="d8caf-124">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="d8caf-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8caf-125">PARAMETERS</span></span>

### <span data-ttu-id="d8caf-126">-Sddl</span><span class="sxs-lookup"><span data-stu-id="d8caf-126">-Sddl</span></span>

<span data-ttu-id="d8caf-127">指定以 SDDL 語法表示安全描述項的字串。</span><span class="sxs-lookup"><span data-stu-id="d8caf-127">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8caf-128">-Type</span><span class="sxs-lookup"><span data-stu-id="d8caf-128">-Type</span></span>

<span data-ttu-id="d8caf-129">指定 SDDL 字串代表的許可權類型。</span><span class="sxs-lookup"><span data-stu-id="d8caf-129">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="d8caf-130">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d8caf-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d8caf-131">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-131">FileSystemRights</span></span>
- <span data-ttu-id="d8caf-132">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-132">RegistryRights</span></span>
- <span data-ttu-id="d8caf-133">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-133">ActiveDirectoryRights</span></span>
- <span data-ttu-id="d8caf-134">MutexRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-134">MutexRights</span></span>
- <span data-ttu-id="d8caf-135">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-135">SemaphoreRights</span></span>
- <span data-ttu-id="d8caf-136">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-136">CryptoKeyRights</span></span>
- <span data-ttu-id="d8caf-137">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="d8caf-137">EventWaitHandleRights</span></span>

<span data-ttu-id="d8caf-138">根據預設，Cmdlet 會使用檔案系統許可權。</span><span class="sxs-lookup"><span data-stu-id="d8caf-138">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="d8caf-139">PowerShell Core 不支援 CryptoKeyRights 和 ActiveDirectoryRights。</span><span class="sxs-lookup"><span data-stu-id="d8caf-139">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8caf-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8caf-140">CommonParameters</span></span>

<span data-ttu-id="d8caf-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8caf-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8caf-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8caf-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8caf-143">輸入</span><span class="sxs-lookup"><span data-stu-id="d8caf-143">INPUTS</span></span>

### <span data-ttu-id="d8caf-144">System.String</span><span class="sxs-lookup"><span data-stu-id="d8caf-144">System.String</span></span>

<span data-ttu-id="d8caf-145">您可以使用管線將 SDDL 字串傳送至 `ConvertFrom-SddlString` 。</span><span class="sxs-lookup"><span data-stu-id="d8caf-145">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="d8caf-146">輸出</span><span class="sxs-lookup"><span data-stu-id="d8caf-146">OUTPUTS</span></span>

## <span data-ttu-id="d8caf-147">注意</span><span class="sxs-lookup"><span data-stu-id="d8caf-147">NOTES</span></span>

## <span data-ttu-id="d8caf-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8caf-148">RELATED LINKS</span></span>

[<span data-ttu-id="d8caf-149">安全描述項定義語言</span><span class="sxs-lookup"><span data-stu-id="d8caf-149">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)

