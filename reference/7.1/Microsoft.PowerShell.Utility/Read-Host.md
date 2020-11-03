---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: b76fc092046a29dcad52f755794fd55dd84ac675
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "93205248"
---
# <span data-ttu-id="a04d4-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="a04d4-103">Read-Host</span></span>

## <span data-ttu-id="a04d4-104">概要</span><span class="sxs-lookup"><span data-stu-id="a04d4-104">SYNOPSIS</span></span>
<span data-ttu-id="a04d4-105">從主控台讀取輸入的一行。</span><span class="sxs-lookup"><span data-stu-id="a04d4-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="a04d4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a04d4-106">SYNTAX</span></span>

### <span data-ttu-id="a04d4-107">AsString (預設值)</span><span class="sxs-lookup"><span data-stu-id="a04d4-107">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="a04d4-108">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="a04d4-108">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="a04d4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a04d4-109">DESCRIPTION</span></span>

<span data-ttu-id="a04d4-110">`Read-Host`Cmdlet 會從主控台讀取輸入的一行。</span><span class="sxs-lookup"><span data-stu-id="a04d4-110">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="a04d4-111">您可以使用它來提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="a04d4-111">You can use it to prompt a user for input.</span></span> <span data-ttu-id="a04d4-112">由於您可以將輸入儲存成安全字串，因此您可以使用這個 Cmdlet 來提示使用者輸入安全資料 (例如密碼) 和共用的資料。</span><span class="sxs-lookup"><span data-stu-id="a04d4-112">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="a04d4-113">範例</span><span class="sxs-lookup"><span data-stu-id="a04d4-113">EXAMPLES</span></span>

### <span data-ttu-id="a04d4-114">範例1：將主控台輸入儲存至變數</span><span class="sxs-lookup"><span data-stu-id="a04d4-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="a04d4-115">此範例會顯示 "請輸入您的年齡：" 字串做為提示。</span><span class="sxs-lookup"><span data-stu-id="a04d4-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="a04d4-116">當輸入值並按下 Enter 鍵時，值會儲存在 `$Age` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a04d4-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="a04d4-117">範例2：將主控台輸入儲存為安全字串</span><span class="sxs-lookup"><span data-stu-id="a04d4-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="a04d4-118">此範例會顯示 "Enter a Password：" 字串做為提示。</span><span class="sxs-lookup"><span data-stu-id="a04d4-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="a04d4-119">輸入值時，星號 (`*`) 會出現在主控台上，以取代輸入。</span><span class="sxs-lookup"><span data-stu-id="a04d4-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="a04d4-120">按下 Enter 鍵時，該值會以 **SecureString** 物件的形式儲存在變數中 `$pwd_secure_string` 。</span><span class="sxs-lookup"><span data-stu-id="a04d4-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="a04d4-121">範例3：遮罩輸入和純文字字串</span><span class="sxs-lookup"><span data-stu-id="a04d4-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="a04d4-122">此範例會顯示 "Enter a Password：" 字串做為提示。</span><span class="sxs-lookup"><span data-stu-id="a04d4-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="a04d4-123">輸入值時，星號 (`*`) 會出現在主控台上，以取代輸入。</span><span class="sxs-lookup"><span data-stu-id="a04d4-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="a04d4-124">按下 Enter 鍵時，該值會以純文字 **字串** 物件的形式儲存在 `$pwd_string` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a04d4-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="a04d4-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a04d4-125">PARAMETERS</span></span>

### <span data-ttu-id="a04d4-126">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="a04d4-126">-AsSecureString</span></span>

<span data-ttu-id="a04d4-127">指出此 Cmdlet 會顯示星號 (`*`) 來取代使用者輸入的字元。</span><span class="sxs-lookup"><span data-stu-id="a04d4-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="a04d4-128">當您使用此參數時，Cmdlet 的輸出 `Read-Host` 會是 **SecureString** 物件， ( **SecureString** ) 。</span><span class="sxs-lookup"><span data-stu-id="a04d4-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a04d4-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="a04d4-129">-MaskInput</span></span>

<span data-ttu-id="a04d4-130">指出此 Cmdlet 會顯示星號 (`*`) 來取代使用者輸入的字元。</span><span class="sxs-lookup"><span data-stu-id="a04d4-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="a04d4-131">當您使用此參數時，Cmdlet 的輸出 `Read-Host` 是 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="a04d4-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="a04d4-132">這可讓您安全地提示輸入以純文字格式傳回的密碼，而不是 **SecureString** 。</span><span class="sxs-lookup"><span data-stu-id="a04d4-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a04d4-133">-Prompt</span><span class="sxs-lookup"><span data-stu-id="a04d4-133">-Prompt</span></span>

<span data-ttu-id="a04d4-134">指定提示的文字。</span><span class="sxs-lookup"><span data-stu-id="a04d4-134">Specifies the text of the prompt.</span></span>
<span data-ttu-id="a04d4-135">輸入字串。</span><span class="sxs-lookup"><span data-stu-id="a04d4-135">Type a string.</span></span>
<span data-ttu-id="a04d4-136">如果字串包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="a04d4-136">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="a04d4-137">PowerShell `:` 會在您輸入的文字中附加冒號 () 。</span><span class="sxs-lookup"><span data-stu-id="a04d4-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="a04d4-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a04d4-138">CommonParameters</span></span>

<span data-ttu-id="a04d4-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a04d4-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a04d4-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a04d4-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a04d4-141">輸入</span><span class="sxs-lookup"><span data-stu-id="a04d4-141">INPUTS</span></span>

### <span data-ttu-id="a04d4-142">無</span><span class="sxs-lookup"><span data-stu-id="a04d4-142">None</span></span>

<span data-ttu-id="a04d4-143">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a04d4-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a04d4-144">輸出</span><span class="sxs-lookup"><span data-stu-id="a04d4-144">OUTPUTS</span></span>

### <span data-ttu-id="a04d4-145">System.String 或 System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="a04d4-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="a04d4-146">如果使用 **AsSecureString** 參數，則會傳回 `Read-Host` **SecureString** 。</span><span class="sxs-lookup"><span data-stu-id="a04d4-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString** .</span></span> <span data-ttu-id="a04d4-147">否則，它會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="a04d4-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="a04d4-148">注意</span><span class="sxs-lookup"><span data-stu-id="a04d4-148">NOTES</span></span>

## <span data-ttu-id="a04d4-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="a04d4-149">RELATED LINKS</span></span>

[<span data-ttu-id="a04d4-150">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="a04d4-150">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="a04d4-151">Get-Host</span><span class="sxs-lookup"><span data-stu-id="a04d4-151">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="a04d4-152">Write-Host</span><span class="sxs-lookup"><span data-stu-id="a04d4-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="a04d4-153">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="a04d4-153">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
