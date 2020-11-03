---
description: 描述可產生終止錯誤的 Throw 關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: d4bf0ea00145c03522d4db952be201c877c9d50c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206548"
---
# <a name="about-throw"></a><span data-ttu-id="84d33-104">關於擲回</span><span class="sxs-lookup"><span data-stu-id="84d33-104">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="84d33-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="84d33-105">Short description</span></span>
<span data-ttu-id="84d33-106">描述可產生終止錯誤的 Throw 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="84d33-106">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="84d33-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="84d33-107">Long description</span></span>

<span data-ttu-id="84d33-108">Throw 關鍵字會導致終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="84d33-108">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="84d33-109">您可以使用 Throw 關鍵字來停止處理命令、函數或腳本。</span><span class="sxs-lookup"><span data-stu-id="84d33-109">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="84d33-110">例如，您可以在 If 語句的腳本區塊中使用 Throw 關鍵字，以回應條件或 try-catch 語句的 Catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="84d33-110">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="84d33-111">您也可以在參數宣告中使用 Throw 關鍵字，讓函式參數變成強制性。</span><span class="sxs-lookup"><span data-stu-id="84d33-111">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="84d33-112">Throw 關鍵字可以擲回任何物件，例如使用者訊息字串或造成錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="84d33-112">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="84d33-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="84d33-113">Syntax</span></span>

<span data-ttu-id="84d33-114">Throw 關鍵字的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="84d33-114">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="84d33-115">Throw 語法中的運算式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="84d33-115">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="84d33-116">當 Throw 語句未出現在 Catch 區塊中，而且它不包含運算式時，它會產生 ScriptHalted 錯誤。</span><span class="sxs-lookup"><span data-stu-id="84d33-116">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

Exception: ScriptHalted
```

<span data-ttu-id="84d33-117">如果在沒有運算式的 Catch 區塊中使用 Throw 關鍵字，它會再次擲回目前的 RuntimeException。</span><span class="sxs-lookup"><span data-stu-id="84d33-117">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="84d33-118">如需詳細資訊，請參閱 about_Try_Catch_Finally。</span><span class="sxs-lookup"><span data-stu-id="84d33-118">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="84d33-119">擲回字串</span><span class="sxs-lookup"><span data-stu-id="84d33-119">Throwing a string</span></span>

<span data-ttu-id="84d33-120">Throw 語句中的選擇性運算式可以是字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="84d33-120">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="84d33-121">擲回其他物件</span><span class="sxs-lookup"><span data-stu-id="84d33-121">Throwing other objects</span></span>

<span data-ttu-id="84d33-122">運算式也可以是擲回代表 PowerShell 進程之物件的物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="84d33-122">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

<span data-ttu-id="84d33-123">您可以使用 $error 自動變數中 ErrorRecord 物件的 TargetObject 屬性來檢查錯誤。</span><span class="sxs-lookup"><span data-stu-id="84d33-123">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

<span data-ttu-id="84d33-124">您也可以擲回 ErrorRecord 物件或 .NET 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="84d33-124">You can also throw an ErrorRecord object or a .NET exception.</span></span> <span data-ttu-id="84d33-125">下列範例會使用 Throw 關鍵字來擲回 >formatexception 物件。</span><span class="sxs-lookup"><span data-stu-id="84d33-125">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a><span data-ttu-id="84d33-126">產生的錯誤</span><span class="sxs-lookup"><span data-stu-id="84d33-126">The resulting error</span></span>

<span data-ttu-id="84d33-127">Throw 關鍵字可以產生 ErrorRecord 物件。</span><span class="sxs-lookup"><span data-stu-id="84d33-127">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="84d33-128">ErrorRecord 物件的 Exception 屬性包含 RuntimeException 物件。</span><span class="sxs-lookup"><span data-stu-id="84d33-128">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="84d33-129">ErrorRecord 物件和 RuntimeException 物件的其餘部分，會隨著 Throw 關鍵字擲回的物件而不同。</span><span class="sxs-lookup"><span data-stu-id="84d33-129">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="84d33-130">RunTimeException 物件會包裝在 ErrorRecord 物件中，而 ErrorRecord 物件會自動儲存在 $Error 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="84d33-130">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="84d33-131">使用 Throw 來建立必要參數</span><span class="sxs-lookup"><span data-stu-id="84d33-131">Using Throw to create a mandatory parameter</span></span>

<span data-ttu-id="84d33-132">不同于舊版的 PowerShell，請勿使用 Throw 關鍵字進行參數驗證。</span><span class="sxs-lookup"><span data-stu-id="84d33-132">Unlike past versions of PowerShell, do not use the Throw keyword for parameter validation.</span></span> <span data-ttu-id="84d33-133">請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) 以取得正確的方式。</span><span class="sxs-lookup"><span data-stu-id="84d33-133">See [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) for the correct way.</span></span>

## <a name="see-also"></a><span data-ttu-id="84d33-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84d33-134">See also</span></span>

- [<span data-ttu-id="84d33-135">about_Break</span><span class="sxs-lookup"><span data-stu-id="84d33-135">about_Break</span></span>](about_Break.md)
- [<span data-ttu-id="84d33-136">about_Continue</span><span class="sxs-lookup"><span data-stu-id="84d33-136">about_Continue</span></span>](about_Continue.md)
- [<span data-ttu-id="84d33-137">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="84d33-137">about_Scopes</span></span>](about_Scopes.md)
- [<span data-ttu-id="84d33-138">about_Trap</span><span class="sxs-lookup"><span data-stu-id="84d33-138">about_Trap</span></span>](about_Trap.md)
- [<span data-ttu-id="84d33-139">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="84d33-139">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
