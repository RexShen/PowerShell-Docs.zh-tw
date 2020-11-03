---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: aacc89001373ecc8ef75e630f965a8d807bd4ac3
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "93205247"
---
# <span data-ttu-id="121d1-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="121d1-103">Read-Host</span></span>

## <span data-ttu-id="121d1-104">概要</span><span class="sxs-lookup"><span data-stu-id="121d1-104">SYNOPSIS</span></span>
<span data-ttu-id="121d1-105">從主控台讀取輸入的一行。</span><span class="sxs-lookup"><span data-stu-id="121d1-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="121d1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="121d1-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="121d1-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="121d1-107">DESCRIPTION</span></span>

<span data-ttu-id="121d1-108">`Read-Host`Cmdlet 會從主控台讀取輸入的一行。</span><span class="sxs-lookup"><span data-stu-id="121d1-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="121d1-109">您可以使用它來提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="121d1-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="121d1-110">由於您可以將輸入儲存成安全字串，因此您可以使用這個 Cmdlet 來提示使用者輸入安全資料 (例如密碼) 和共用的資料。</span><span class="sxs-lookup"><span data-stu-id="121d1-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="121d1-111">範例</span><span class="sxs-lookup"><span data-stu-id="121d1-111">EXAMPLES</span></span>

### <span data-ttu-id="121d1-112">範例1：將主控台輸入儲存至變數</span><span class="sxs-lookup"><span data-stu-id="121d1-112">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="121d1-113">此範例會顯示 "請輸入您的年齡：" 字串做為提示。</span><span class="sxs-lookup"><span data-stu-id="121d1-113">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="121d1-114">當輸入值並按下 Enter 鍵時，值會儲存在 `$Age` 變數中。</span><span class="sxs-lookup"><span data-stu-id="121d1-114">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="121d1-115">範例2：將主控台輸入儲存為安全字串</span><span class="sxs-lookup"><span data-stu-id="121d1-115">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="121d1-116">此範例會顯示 "Enter a Password：" 字串做為提示。</span><span class="sxs-lookup"><span data-stu-id="121d1-116">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="121d1-117">輸入值時，星號 (`*`) 會出現在主控台上，以取代輸入。</span><span class="sxs-lookup"><span data-stu-id="121d1-117">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="121d1-118">按下 Enter 鍵時，該值會以 **SecureString** 物件的形式儲存在變數中 `$pwd_secure_string` 。</span><span class="sxs-lookup"><span data-stu-id="121d1-118">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="121d1-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="121d1-119">PARAMETERS</span></span>

### <span data-ttu-id="121d1-120">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="121d1-120">-AsSecureString</span></span>

<span data-ttu-id="121d1-121">指出此 Cmdlet 會顯示星號 (`*`) 來取代使用者輸入的字元。</span><span class="sxs-lookup"><span data-stu-id="121d1-121">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="121d1-122">當您使用此參數時，Cmdlet 的輸出 `Read-Host` 會是 **SecureString** 物件， ( **SecureString** ) 。</span><span class="sxs-lookup"><span data-stu-id="121d1-122">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

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

### <span data-ttu-id="121d1-123">-Prompt</span><span class="sxs-lookup"><span data-stu-id="121d1-123">-Prompt</span></span>

<span data-ttu-id="121d1-124">指定提示的文字。</span><span class="sxs-lookup"><span data-stu-id="121d1-124">Specifies the text of the prompt.</span></span>
<span data-ttu-id="121d1-125">輸入字串。</span><span class="sxs-lookup"><span data-stu-id="121d1-125">Type a string.</span></span>
<span data-ttu-id="121d1-126">如果字串包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="121d1-126">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="121d1-127">PowerShell `:` 會在您輸入的文字中附加冒號 () 。</span><span class="sxs-lookup"><span data-stu-id="121d1-127">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="121d1-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="121d1-128">CommonParameters</span></span>

<span data-ttu-id="121d1-129">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="121d1-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="121d1-130">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="121d1-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="121d1-131">輸入</span><span class="sxs-lookup"><span data-stu-id="121d1-131">INPUTS</span></span>

### <span data-ttu-id="121d1-132">無</span><span class="sxs-lookup"><span data-stu-id="121d1-132">None</span></span>

<span data-ttu-id="121d1-133">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="121d1-133">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="121d1-134">輸出</span><span class="sxs-lookup"><span data-stu-id="121d1-134">OUTPUTS</span></span>

### <span data-ttu-id="121d1-135">System.String 或 System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="121d1-135">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="121d1-136">如果使用 **AsSecureString** 參數，則會傳回 `Read-Host` **SecureString** 。</span><span class="sxs-lookup"><span data-stu-id="121d1-136">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString** .</span></span> <span data-ttu-id="121d1-137">否則，它會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="121d1-137">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="121d1-138">注意</span><span class="sxs-lookup"><span data-stu-id="121d1-138">NOTES</span></span>

## <span data-ttu-id="121d1-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="121d1-139">RELATED LINKS</span></span>

[<span data-ttu-id="121d1-140">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="121d1-140">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="121d1-141">Get-Host</span><span class="sxs-lookup"><span data-stu-id="121d1-141">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="121d1-142">Write-Host</span><span class="sxs-lookup"><span data-stu-id="121d1-142">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="121d1-143">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="121d1-143">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
