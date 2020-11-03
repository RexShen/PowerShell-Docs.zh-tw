---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: e24bb117b4d4277adc359c130789cf7ee03b1fd6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204135"
---
# <span data-ttu-id="5daf6-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5daf6-103">Get-PSRepository</span></span>

## <span data-ttu-id="5daf6-104">概要</span><span class="sxs-lookup"><span data-stu-id="5daf6-104">SYNOPSIS</span></span>
<span data-ttu-id="5daf6-105">取得 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="5daf6-105">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="5daf6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5daf6-106">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5daf6-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5daf6-107">DESCRIPTION</span></span>

<span data-ttu-id="5daf6-108">**PSRepository** 指令程式會取得為目前使用者註冊的 PowerShell 模組存放庫。</span><span class="sxs-lookup"><span data-stu-id="5daf6-108">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="5daf6-109">範例</span><span class="sxs-lookup"><span data-stu-id="5daf6-109">EXAMPLES</span></span>

### <span data-ttu-id="5daf6-110">範例1：取得所有模組存放庫</span><span class="sxs-lookup"><span data-stu-id="5daf6-110">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="5daf6-111">此命令會取得為目前使用者註冊的所有模組存放庫。</span><span class="sxs-lookup"><span data-stu-id="5daf6-111">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="5daf6-112">範例2：依名稱取得模組存放庫</span><span class="sxs-lookup"><span data-stu-id="5daf6-112">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="5daf6-113">此命令會取得名稱中包含 NuGet 的所有模組存放庫。</span><span class="sxs-lookup"><span data-stu-id="5daf6-113">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="5daf6-114">範例3：取得模組存放庫並將輸出格式化</span><span class="sxs-lookup"><span data-stu-id="5daf6-114">Example 3: Get a module repository and format the output</span></span>

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

<span data-ttu-id="5daf6-115">此命令會取得名為 Local01 的存放庫，並使用管線運算子將該物件傳遞至 Format-List Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5daf6-115">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="5daf6-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5daf6-116">PARAMETERS</span></span>

### <span data-ttu-id="5daf6-117">-Name</span><span class="sxs-lookup"><span data-stu-id="5daf6-117">-Name</span></span>

<span data-ttu-id="5daf6-118">指定要取得之存放庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="5daf6-118">Specifies the names of the repositories to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5daf6-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5daf6-119">CommonParameters</span></span>

<span data-ttu-id="5daf6-120">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5daf6-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5daf6-121">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5daf6-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5daf6-122">輸入</span><span class="sxs-lookup"><span data-stu-id="5daf6-122">INPUTS</span></span>

### <span data-ttu-id="5daf6-123">System.String[]</span><span class="sxs-lookup"><span data-stu-id="5daf6-123">System.String[]</span></span>

## <span data-ttu-id="5daf6-124">輸出</span><span class="sxs-lookup"><span data-stu-id="5daf6-124">OUTPUTS</span></span>

### <span data-ttu-id="5daf6-125">System.Object</span><span class="sxs-lookup"><span data-stu-id="5daf6-125">System.Object</span></span>

## <span data-ttu-id="5daf6-126">注意</span><span class="sxs-lookup"><span data-stu-id="5daf6-126">NOTES</span></span>

## <span data-ttu-id="5daf6-127">相關連結</span><span class="sxs-lookup"><span data-stu-id="5daf6-127">RELATED LINKS</span></span>

[<span data-ttu-id="5daf6-128">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5daf6-128">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="5daf6-129">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5daf6-129">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="5daf6-130">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5daf6-130">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

