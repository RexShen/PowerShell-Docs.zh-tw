---
description: 描述可產生終止錯誤的 Throw 關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: caac7679e2c7ecd21b4fa9e43ab76681ee3faed5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207528"
---
# <a name="about-throw"></a><span data-ttu-id="f8e7b-104">關於擲回</span><span class="sxs-lookup"><span data-stu-id="f8e7b-104">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="f8e7b-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="f8e7b-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="f8e7b-106">描述可產生終止錯誤的 Throw 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-106">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="f8e7b-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="f8e7b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f8e7b-108">Throw 關鍵字會導致終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-108">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="f8e7b-109">您可以使用 Throw 關鍵字來停止處理命令、函數或腳本。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-109">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="f8e7b-110">例如，您可以在 If 語句的腳本區塊中使用 Throw 關鍵字，以回應條件或 try-catch 語句的 Catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-110">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="f8e7b-111">您也可以在參數宣告中使用 Throw 關鍵字，讓函式參數變成強制性。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-111">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="f8e7b-112">Throw 關鍵字可以擲回任何物件，例如使用者訊息字串或造成錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-112">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8e7b-113">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f8e7b-113">SYNTAX</span></span>

<span data-ttu-id="f8e7b-114">Throw 關鍵字的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="f8e7b-114">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="f8e7b-115">Throw 語法中的運算式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-115">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="f8e7b-116">當 Throw 語句未出現在 Catch 區塊中，而且它不包含運算式時，它會產生 ScriptHalted 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-116">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="f8e7b-117">如果在沒有運算式的 Catch 區塊中使用 Throw 關鍵字，它會再次擲回目前的 RuntimeException。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-117">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="f8e7b-118">如需詳細資訊，請參閱 about_Try_Catch_Finally。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-118">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="f8e7b-119">擲回字串</span><span class="sxs-lookup"><span data-stu-id="f8e7b-119">THROWING A STRING</span></span>

<span data-ttu-id="f8e7b-120">Throw 語句中的選擇性運算式可以是字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f8e7b-120">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="f8e7b-121">擲回其他物件</span><span class="sxs-lookup"><span data-stu-id="f8e7b-121">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="f8e7b-122">運算式也可以是擲回代表 PowerShell 進程之物件的物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f8e7b-122">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

<span data-ttu-id="f8e7b-123">您可以使用 $error 自動變數中 ErrorRecord 物件的 TargetObject 屬性來檢查錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-123">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="f8e7b-124">您也可以擲回 ErrorRecord 物件或 Microsoft .NET Framework 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-124">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="f8e7b-125">下列範例會使用 Throw 關鍵字來擲回 >formatexception 物件。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-125">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a><span data-ttu-id="f8e7b-126">產生的錯誤</span><span class="sxs-lookup"><span data-stu-id="f8e7b-126">RESULTING ERROR</span></span>

<span data-ttu-id="f8e7b-127">Throw 關鍵字可以產生 ErrorRecord 物件。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-127">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="f8e7b-128">ErrorRecord 物件的 Exception 屬性包含 RuntimeException 物件。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-128">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="f8e7b-129">ErrorRecord 物件和 RuntimeException 物件的其餘部分，會隨著 Throw 關鍵字擲回的物件而不同。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-129">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="f8e7b-130">RunTimeException 物件會包裝在 ErrorRecord 物件中，而 ErrorRecord 物件會自動儲存在 $Error 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-130">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="f8e7b-131">使用 THROW 來建立必要參數</span><span class="sxs-lookup"><span data-stu-id="f8e7b-131">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="f8e7b-132">您可以使用 Throw 關鍵字來強制執行函式參數。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-132">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="f8e7b-133">這是使用 Parameter 關鍵字的強制參數的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-133">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="f8e7b-134">當您使用強制參數時，系統會提示使用者輸入必要的參數值。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-134">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="f8e7b-135">當您使用 Throw 關鍵字時，命令會停止並顯示錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-135">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="f8e7b-136">例如，在參數子運算式中的 Throw 關鍵字會讓 Path 參數成為函數中的必要參數。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-136">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="f8e7b-137">在此情況下，Throw 關鍵字會擲回訊息字串，但如果未指定 Path 參數，則會產生 Throw 關鍵字來產生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-137">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="f8e7b-138">接下來的運算式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f8e7b-138">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="f8e7b-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8e7b-139">SEE ALSO</span></span>

[<span data-ttu-id="f8e7b-140">about_Break</span><span class="sxs-lookup"><span data-stu-id="f8e7b-140">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="f8e7b-141">about_Continue</span><span class="sxs-lookup"><span data-stu-id="f8e7b-141">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="f8e7b-142">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f8e7b-142">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="f8e7b-143">about_Trap</span><span class="sxs-lookup"><span data-stu-id="f8e7b-143">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="f8e7b-144">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="f8e7b-144">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
