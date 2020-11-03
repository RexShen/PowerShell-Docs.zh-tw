---
description: 描述 PowerShell 中使用的語法圖表。
keywords: powershell,cmdlet
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: 180df88bb41b98bc308f192f7c4caf38aa7445ad
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207688"
---
# <a name="about-command-syntax"></a><span data-ttu-id="515c2-104">關於命令語法</span><span class="sxs-lookup"><span data-stu-id="515c2-104">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="515c2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="515c2-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="515c2-106">描述 PowerShell 中使用的語法圖表。</span><span class="sxs-lookup"><span data-stu-id="515c2-106">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="515c2-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="515c2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="515c2-108">[Get-help](xref:Microsoft.PowerShell.Core.Get-Help)和[get 命令](xref:Microsoft.PowerShell.Core.Get-Command)Cmdlet 會顯示語法圖表，以協助您正確地建立命令。</span><span class="sxs-lookup"><span data-stu-id="515c2-108">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="515c2-109">本主題說明如何解讀語法圖表。</span><span class="sxs-lookup"><span data-stu-id="515c2-109">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="515c2-110">語法圖表</span><span class="sxs-lookup"><span data-stu-id="515c2-110">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="515c2-111">命令語法圖表中的每個段落都代表一種有效的命令格式。</span><span class="sxs-lookup"><span data-stu-id="515c2-111">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="515c2-112">若要建立命令，請從左至右追蹤語法圖表。</span><span class="sxs-lookup"><span data-stu-id="515c2-112">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="515c2-113">從選擇性參數中選取，並提供預留位置的值。</span><span class="sxs-lookup"><span data-stu-id="515c2-113">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="515c2-114">PowerShell 會針對語法圖表使用下列標記法。</span><span class="sxs-lookup"><span data-stu-id="515c2-114">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="515c2-115">以下是 [新別名](xref:Microsoft.PowerShell.Utility.New-Alias) Cmdlet 的語法。</span><span class="sxs-lookup"><span data-stu-id="515c2-115">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="515c2-116">為了方便起見，語法是大寫的，但 PowerShell 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="515c2-116">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="515c2-117">語法圖表有下列元素。</span><span class="sxs-lookup"><span data-stu-id="515c2-117">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="515c2-118">命令名稱</span><span class="sxs-lookup"><span data-stu-id="515c2-118">Command name</span></span>

<span data-ttu-id="515c2-119">命令的開頭一律是命令名稱，例如 `New-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="515c2-119">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="515c2-120">輸入命令名稱或其別名，例如的 "gcm" `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="515c2-120">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="515c2-121">參數</span><span class="sxs-lookup"><span data-stu-id="515c2-121">Parameters</span></span>

<span data-ttu-id="515c2-122">命令的參數是決定命令功能的選項。</span><span class="sxs-lookup"><span data-stu-id="515c2-122">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="515c2-123">某些參數會採用「值」，這是使用者輸入的命令。</span><span class="sxs-lookup"><span data-stu-id="515c2-123">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="515c2-124">例如， `Get-Help` 命令具有 **Name** 參數，可讓您指定說明顯示的主題名稱。</span><span class="sxs-lookup"><span data-stu-id="515c2-124">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="515c2-125">主題名稱是 **name** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="515c2-125">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="515c2-126">在 PowerShell 命令中，參數名稱的開頭一律為連字號。</span><span class="sxs-lookup"><span data-stu-id="515c2-126">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="515c2-127">連字號會告訴 PowerShell 命令中的專案是參數名稱。</span><span class="sxs-lookup"><span data-stu-id="515c2-127">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="515c2-128">例如，若要使用的 Name 參數 `New-Alias` ，請輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="515c2-128">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="515c2-129">參數可以是強制性或選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-129">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="515c2-130">在語法圖中，選擇性的專案會以括弧括住 `[ ]` 。</span><span class="sxs-lookup"><span data-stu-id="515c2-130">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="515c2-131">如需參數的詳細資訊，請參閱 [about_Parameters](about_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="515c2-131">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="515c2-132">參數值</span><span class="sxs-lookup"><span data-stu-id="515c2-132">Parameter Values</span></span>

<span data-ttu-id="515c2-133">參數值是參數所採用的輸入。</span><span class="sxs-lookup"><span data-stu-id="515c2-133">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="515c2-134">因為 Windows PowerShell 是以 Microsoft .NET Framework 為基礎，所以參數值會以其 .NET 類型以語法圖表表示。</span><span class="sxs-lookup"><span data-stu-id="515c2-134">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="515c2-135">例如，的 Name 參數會 `Get-Help` 採用「字串」值，這是一個文字字串，例如以引號括住的單一單字或多個字。</span><span class="sxs-lookup"><span data-stu-id="515c2-135">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="515c2-136">參數值的 .NET 類型會以角括弧括住， `< >` 表示它是值的預留位置，而不是您在命令中輸入的常值。</span><span class="sxs-lookup"><span data-stu-id="515c2-136">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="515c2-137">若要使用參數，請將 .NET 型別預留位置取代為具有指定 .NET 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="515c2-137">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="515c2-138">例如，若要使用 **Name** 參數，請輸入 "-Name"，後面接著字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="515c2-138">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="515c2-139">沒有值的參數</span><span class="sxs-lookup"><span data-stu-id="515c2-139">Parameters with no values</span></span>

<span data-ttu-id="515c2-140">某些參數不接受輸入，因此沒有參數值。</span><span class="sxs-lookup"><span data-stu-id="515c2-140">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="515c2-141">沒有值的參數稱為「切換參數」，因為它們的運作方式就像是開啟/關閉切換參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-141">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="515c2-142">您可以將它們包含在) 上 (，或將它們從命令) 略過 (。</span><span class="sxs-lookup"><span data-stu-id="515c2-142">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="515c2-143">若要使用切換參數，請只輸入參數名稱，並在前面加上連字號。</span><span class="sxs-lookup"><span data-stu-id="515c2-143">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="515c2-144">例如，若要使用 Cmdlet 的 **WhatIf** 參數 `New-Alias` ，請輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="515c2-144">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="515c2-145">參數集</span><span class="sxs-lookup"><span data-stu-id="515c2-145">Parameter Sets</span></span>

<span data-ttu-id="515c2-146">命令的參數會列在參數集合中。</span><span class="sxs-lookup"><span data-stu-id="515c2-146">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="515c2-147">參數集看起來像是語法圖的段落。</span><span class="sxs-lookup"><span data-stu-id="515c2-147">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="515c2-148">`New-Alias`Cmdlet 有一個參數集，但許多 Cmdlet 都有多個參數集。</span><span class="sxs-lookup"><span data-stu-id="515c2-148">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="515c2-149">某些 Cmdlet 參數是參數集的唯一參數，而其他參數則出現在多個參數集內。</span><span class="sxs-lookup"><span data-stu-id="515c2-149">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="515c2-150">每個參數集都代表有效命令的格式。</span><span class="sxs-lookup"><span data-stu-id="515c2-150">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="515c2-151">參數集只包含可在命令中一起使用的參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-151">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="515c2-152">如果參數無法在相同的命令中使用，它們會出現在不同的參數集中。</span><span class="sxs-lookup"><span data-stu-id="515c2-152">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="515c2-153">例如， [取得隨機](xref:Microsoft.PowerShell.Utility.Get-Random) Cmdlet 具有下列參數集：</span><span class="sxs-lookup"><span data-stu-id="515c2-153">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="515c2-154">第一個參數集（傳回亂數字）有 **最小** 和 **最大** 參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-154">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="515c2-155">第二個參數集會從一組物件傳回隨機選取的物件，包含 **InputObject** 和 **Count** 參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-155">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="515c2-156">這兩個參數集都有 **SetSeed** 參數和一般參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-156">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="515c2-157">這些參數集會指出您可以在同一個命令中使用 **InputObject** 和 **count** 參數，但不能在同一個命令中使用 **Maximum** 和 **count** 參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-157">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="515c2-158">您可以使用該參數集中的參數，指出您想要使用的參數集。</span><span class="sxs-lookup"><span data-stu-id="515c2-158">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="515c2-159">不過，每個 Cmdlet 也都有預設參數集。</span><span class="sxs-lookup"><span data-stu-id="515c2-159">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="515c2-160">當您未指定參數集的唯一參數時，就會使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="515c2-160">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="515c2-161">例如，如果您不使用 `Get-Random` 參數，Windows PowerShell 會假設您使用的是 **number** 參數集，而且會傳回一個亂數字。</span><span class="sxs-lookup"><span data-stu-id="515c2-161">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="515c2-162">在每個參數集，參數會以位置順序顯示。</span><span class="sxs-lookup"><span data-stu-id="515c2-162">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="515c2-163">只有當您省略選擇性參數名稱時，命令中的參數順序才有意義。</span><span class="sxs-lookup"><span data-stu-id="515c2-163">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="515c2-164">當省略參數名稱時，PowerShell 會依位置和類型將值指派給參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-164">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="515c2-165">如需參數位置的詳細資訊，請參閱 `about_Parameters` 。</span><span class="sxs-lookup"><span data-stu-id="515c2-165">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="515c2-166">語法圖表中的符號</span><span class="sxs-lookup"><span data-stu-id="515c2-166">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="515c2-167">語法圖表會列出命令名稱、命令參數和參數值。</span><span class="sxs-lookup"><span data-stu-id="515c2-167">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="515c2-168">它也會使用符號來示範如何建立有效的命令。</span><span class="sxs-lookup"><span data-stu-id="515c2-168">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="515c2-169">語法圖表會使用下列符號：</span><span class="sxs-lookup"><span data-stu-id="515c2-169">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="515c2-170">連字號 `-` 表示參數名稱。</span><span class="sxs-lookup"><span data-stu-id="515c2-170">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="515c2-171">在命令中，于參數名稱前面輸入連字號，但不含中間的空格，如語法圖所示。</span><span class="sxs-lookup"><span data-stu-id="515c2-171">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="515c2-172">例如，若要使用的 **Name** 參數 `New-Alias` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="515c2-172">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="515c2-173">角括弧 `<>` 表示預留位置文字。</span><span class="sxs-lookup"><span data-stu-id="515c2-173">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="515c2-174">您未在命令中輸入角括弧或預留位置文字。</span><span class="sxs-lookup"><span data-stu-id="515c2-174">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="515c2-175">相反地，您會將它取代為它所描述的專案。</span><span class="sxs-lookup"><span data-stu-id="515c2-175">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="515c2-176">角括弧用來識別參數所採用之值的 .NET 型別。</span><span class="sxs-lookup"><span data-stu-id="515c2-176">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="515c2-177">例如，若要使用 Cmdlet 的 **Name** 參數 `New-Alias` ，請將取代為 `<string>` 字串，也就是以引號括住的單一單字或單字群組。</span><span class="sxs-lookup"><span data-stu-id="515c2-177">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="515c2-178">括弧 `[ ]` 表示選擇性的專案。</span><span class="sxs-lookup"><span data-stu-id="515c2-178">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="515c2-179">參數和其值可以是選擇性的，或必要參數的名稱可以是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="515c2-179">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="515c2-180">例如，的 **Description** 參數 `New-Alias` 和其值會以括弧括住，因為兩者都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="515c2-180">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="515c2-181">括弧也指出 Name 參數值 `<string>` 是必要的，但參數名稱 "name" 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="515c2-181">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="515c2-182">附加至 .NET 類型的右括弧和左括弧 `[]` ，表示參數可以接受該類型的一或多個值。</span><span class="sxs-lookup"><span data-stu-id="515c2-182">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="515c2-183">以逗號分隔的清單方式輸入值。</span><span class="sxs-lookup"><span data-stu-id="515c2-183">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="515c2-184">例如，Cmdlet 的 **name** 參數 `New-Alias` 只接受一個字串，但 [Get 進程](xref:Microsoft.PowerShell.Management.Get-Process)的 **name** 參數可以接受一或多個字串。</span><span class="sxs-lookup"><span data-stu-id="515c2-184">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="515c2-185">括弧 `{}` 表示「列舉」，這是參數的一組有效值。</span><span class="sxs-lookup"><span data-stu-id="515c2-185">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="515c2-186">大括弧中的值是以分隔號分隔 `|` 。</span><span class="sxs-lookup"><span data-stu-id="515c2-186">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="515c2-187">這些橫條表示「專有」或「選擇」，這表示您只能從大括弧內所列的一組值中選擇一個值。</span><span class="sxs-lookup"><span data-stu-id="515c2-187">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="515c2-188">例如，指令程式的語法 `New-Alias` 包含下列 **選項** 參數的列舉值：</span><span class="sxs-lookup"><span data-stu-id="515c2-188">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="515c2-189">大括弧和垂直線指出您可以為 **Option** 參數選擇任何一個列出的值，例如 "ReadOnly" 或 "AllScope"。</span><span class="sxs-lookup"><span data-stu-id="515c2-189">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="515c2-190">選擇性專案</span><span class="sxs-lookup"><span data-stu-id="515c2-190">Optional Items</span></span>

<span data-ttu-id="515c2-191">括弧 `[]` 括住選擇性專案。</span><span class="sxs-lookup"><span data-stu-id="515c2-191">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="515c2-192">例如，在 `New-Alias` Cmdlet 語法描述中， **範圍** 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="515c2-192">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="515c2-193">這在語法中是以括弧括住參數名稱和類型來表示：</span><span class="sxs-lookup"><span data-stu-id="515c2-193">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="515c2-194">下列兩個範例都是正確的 `New-Alias` Cmdlet 用法：</span><span class="sxs-lookup"><span data-stu-id="515c2-194">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="515c2-195">即使該參數的值為必要，參數名稱也可以是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="515c2-195">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="515c2-196">這是以括弧括住參數名稱（而不是參數類型）的語法指出，如此範例中的 `New-Alias` Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="515c2-196">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="515c2-197">下列命令會正確地使用 `New-Alias` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="515c2-197">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="515c2-198">命令會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="515c2-198">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="515c2-199">如果參數名稱未包含在語句中做為輸入，Windows PowerShell 會嘗試使用引數的位置，將值指派給參數。</span><span class="sxs-lookup"><span data-stu-id="515c2-199">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="515c2-200">下列範例不完整：</span><span class="sxs-lookup"><span data-stu-id="515c2-200">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="515c2-201">此 Cmdlet 需要 **名稱** 和 **值** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="515c2-201">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="515c2-202">在語法範例中，括弧也用於命名和轉換成 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="515c2-202">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="515c2-203">在此內容中，括弧不表示元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="515c2-203">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="515c2-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515c2-204">SEE ALSO</span></span>

- [<span data-ttu-id="515c2-205">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="515c2-205">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="515c2-206">Get-Command</span><span class="sxs-lookup"><span data-stu-id="515c2-206">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="515c2-207">Get-Help</span><span class="sxs-lookup"><span data-stu-id="515c2-207">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)
