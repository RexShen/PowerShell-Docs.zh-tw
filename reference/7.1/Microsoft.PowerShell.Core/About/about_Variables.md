---
description: 描述變數如何儲存可在 PowerShell 中使用的值。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 858015f42ff58baf653d8d0f1502df0f7ed4a63f
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483092"
---
# <a name="about-variables"></a><span data-ttu-id="b7544-104">關於變數</span><span class="sxs-lookup"><span data-stu-id="b7544-104">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="b7544-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b7544-105">Short description</span></span>

<span data-ttu-id="b7544-106">描述變數如何儲存可在 PowerShell 中使用的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-106">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b7544-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="b7544-107">Long description</span></span>

<span data-ttu-id="b7544-108">您可以將所有類型的值儲存在 PowerShell 變數中。</span><span class="sxs-lookup"><span data-stu-id="b7544-108">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="b7544-109">例如，儲存命令的結果，並儲存命令和運算式中使用的元素，例如名稱、路徑、設定和值。</span><span class="sxs-lookup"><span data-stu-id="b7544-109">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="b7544-110">變數是儲存值的記憶體單位。</span><span class="sxs-lookup"><span data-stu-id="b7544-110">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="b7544-111">在 PowerShell 中，變數會以文字字串表示（以貨幣符號 (`$`) ，例如 `$a` 、或） `$process` `$my_var` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-111">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="b7544-112">變數名稱不區分大小寫，而且可以包含空格和特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-112">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="b7544-113">但是，包含特殊字元和空格的變數名稱不容易使用，而且應該避免使用。</span><span class="sxs-lookup"><span data-stu-id="b7544-113">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="b7544-114">如需詳細資訊，請參閱 [包含特殊字元的變數名稱](#variable-names-that-include-special-characters)。</span><span class="sxs-lookup"><span data-stu-id="b7544-114">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="b7544-115">PowerShell 中有數種不同類型的變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-115">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="b7544-116">使用者建立的變數：使用者建立的變數由使用者建立和維護。</span><span class="sxs-lookup"><span data-stu-id="b7544-116">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="b7544-117">根據預設，您在 PowerShell 命令列建立的變數只會在 PowerShell 視窗開啟時存在。</span><span class="sxs-lookup"><span data-stu-id="b7544-117">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="b7544-118">當 PowerShell 視窗關閉時，會刪除變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-118">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="b7544-119">若要儲存變數，請將它新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b7544-119">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="b7544-120">您也可以在具有全域、腳本或區域範圍的腳本中建立變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-120">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="b7544-121">自動變數：自動變數會儲存 PowerShell 的狀態。</span><span class="sxs-lookup"><span data-stu-id="b7544-121">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="b7544-122">這些變數是由 PowerShell 所建立，而 PowerShell 則會視需要變更其值，以維持其精確度。</span><span class="sxs-lookup"><span data-stu-id="b7544-122">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="b7544-123">使用者無法變更這些變數的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-123">Users can't change the value of these variables.</span></span> <span data-ttu-id="b7544-124">例如，變數會 `$PSHOME` 儲存 PowerShell 安裝目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="b7544-124">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="b7544-125">如需詳細資訊、清單和自動變數的描述，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-125">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="b7544-126">喜好設定變數：喜好設定變數會儲存 PowerShell 的使用者喜好設定。</span><span class="sxs-lookup"><span data-stu-id="b7544-126">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="b7544-127">這些變數是由 PowerShell 所建立，並以預設值填入。</span><span class="sxs-lookup"><span data-stu-id="b7544-127">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="b7544-128">使用者可以變更這些變數的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-128">Users can change the values of these variables.</span></span> <span data-ttu-id="b7544-129">例如，變數會 `$MaximumHistoryCount` 決定會話歷程記錄中的最大專案數。</span><span class="sxs-lookup"><span data-stu-id="b7544-129">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="b7544-130">如需詳細資訊、清單和喜好設定變數的描述，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-130">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="b7544-131">使用變數</span><span class="sxs-lookup"><span data-stu-id="b7544-131">Working with variables</span></span>

<span data-ttu-id="b7544-132">若要建立新的變數，請使用指派語句將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-132">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="b7544-133">在使用變數之前，您不需要宣告該變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-133">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="b7544-134">所有變數的預設值為 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-134">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="b7544-135">若要取得 PowerShell 會話中所有變數的清單，請輸入 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-135">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="b7544-136">變數名稱顯示時，不會有之前的貨幣 (`$` 用來參考變數) 號。</span><span class="sxs-lookup"><span data-stu-id="b7544-136">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="b7544-137">例如：</span><span class="sxs-lookup"><span data-stu-id="b7544-137">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="b7544-138">變數很適合用來儲存命令的結果。</span><span class="sxs-lookup"><span data-stu-id="b7544-138">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="b7544-139">例如：</span><span class="sxs-lookup"><span data-stu-id="b7544-139">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="b7544-140">若要顯示變數的值，請輸入變數名稱，前面加上貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="b7544-140">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="b7544-141">例如：</span><span class="sxs-lookup"><span data-stu-id="b7544-141">For example:</span></span>

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

<span data-ttu-id="b7544-142">若要變更變數的值，請將新值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-142">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="b7544-143">下列範例會顯示變數的值 `$MyVariable` 、變更變數的值，然後顯示新的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-143">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

<span data-ttu-id="b7544-144">若要刪除變數的值，請使用 `Clear-Variable` Cmdlet 或將值變更為 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-144">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="b7544-145">若要刪除變數，請使用 [移除變數](xref:Microsoft.PowerShell.Utility.Remove-Variable) 或 [移除專案](xref:Microsoft.PowerShell.Management.Remove-Item)。</span><span class="sxs-lookup"><span data-stu-id="b7544-145">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="b7544-146">變數類型</span><span class="sxs-lookup"><span data-stu-id="b7544-146">Types of variables</span></span>

<span data-ttu-id="b7544-147">您可以將任何類型的物件儲存在變數中，包括整數、字串、陣列和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b7544-147">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="b7544-148">以及代表進程、服務、事件記錄和電腦的物件。</span><span class="sxs-lookup"><span data-stu-id="b7544-148">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="b7544-149">PowerShell 變數是鬆散類型，這表示它們不受限於特定類型的物件。</span><span class="sxs-lookup"><span data-stu-id="b7544-149">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="b7544-150">單一變數甚至可以同時包含不同類型之物件的集合或陣列。</span><span class="sxs-lookup"><span data-stu-id="b7544-150">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="b7544-151">變數的資料類型是由變數值的 .NET 類型所決定。</span><span class="sxs-lookup"><span data-stu-id="b7544-151">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="b7544-152">若要查看變數的物件類型，請使用 [ [取得成員](xref:Microsoft.PowerShell.Utility.Get-Member)]。</span><span class="sxs-lookup"><span data-stu-id="b7544-152">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="b7544-153">例如：</span><span class="sxs-lookup"><span data-stu-id="b7544-153">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="b7544-154">您可以使用類型屬性和轉換標記法，以確定變數只能包含可轉換成該類型的特定物件類型或物件。</span><span class="sxs-lookup"><span data-stu-id="b7544-154">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="b7544-155">如果您嘗試指派另一種類型的值，則 PowerShell 會嘗試將值轉換為其類型。</span><span class="sxs-lookup"><span data-stu-id="b7544-155">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="b7544-156">如果無法轉換類型，指派語句將會失敗。</span><span class="sxs-lookup"><span data-stu-id="b7544-156">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="b7544-157">若要使用轉型標記法，請在指派語句的左邊輸入名稱（以括弧括住），然後再 (變數名稱) 。</span><span class="sxs-lookup"><span data-stu-id="b7544-157">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="b7544-158">下列範例會建立只能包含 `$number` 整數的變數、只能包含字串的 `$words` 變數，以及只能 `$dates` 包含 **DateTime** 物件的變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-158">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="b7544-159">在命令和運算式中使用變數</span><span class="sxs-lookup"><span data-stu-id="b7544-159">Using variables in commands and expressions</span></span>

<span data-ttu-id="b7544-160">若要在命令或運算式中使用變數，請輸入變數名稱，前面加上貨幣 (`$`) 號。</span><span class="sxs-lookup"><span data-stu-id="b7544-160">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="b7544-161">如果變數名稱和貨幣符號未以引號括住，或以雙引號括住 (`"`) 標記，則會在命令或運算式中使用變數的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-161">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="b7544-162">如果變數名稱和貨幣符號以單引號括住 (`'`) 標記，就會在運算式中使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="b7544-162">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="b7544-163">如需在 PowerShell 中使用引號的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-163">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="b7544-164">此範例會取得變數的值 `$PROFILE` ，這是 powershell 主控台中 powershell 使用者設定檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="b7544-164">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="b7544-165">在此範例中，會顯示兩個命令，可在 **notepad.exe** 中開啟 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b7544-165">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="b7544-166">使用雙引號 () 標記的範例會 `"` 使用變數的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-166">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="b7544-167">下列範例會使用單引號 (`'`) 標記，將變數視為常值文字。</span><span class="sxs-lookup"><span data-stu-id="b7544-167">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="b7544-168">包含特殊字元的變數名稱</span><span class="sxs-lookup"><span data-stu-id="b7544-168">Variable names that include special characters</span></span>

<span data-ttu-id="b7544-169">變數名稱的開頭為貨幣 (`$`) 符號，而且可以包含英數位元和特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-169">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="b7544-170">變數名稱長度只受限於可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b7544-170">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="b7544-171">最佳做法是變數名稱只包含英數位元和底線 (`_`) 字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-171">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="b7544-172">包含空格和其他特殊字元的變數名稱不容易使用，而且應該避免使用。</span><span class="sxs-lookup"><span data-stu-id="b7544-172">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="b7544-173">英數位元變數名稱可以包含下列字元：</span><span class="sxs-lookup"><span data-stu-id="b7544-173">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="b7544-174">這些類別的 Unicode 字元： **Lu** 、 **Ll** 、 **Lt** 、 **Lm** 、 **Lo** 或 **Nd** 。</span><span class="sxs-lookup"><span data-stu-id="b7544-174">Unicode characters from these categories: **Lu** , **Ll** , **Lt** , **Lm** , **Lo** , or **Nd**.</span></span>
- <span data-ttu-id="b7544-175">底線 (`_`) 字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-175">Underscore (`_`) character.</span></span>
- <span data-ttu-id="b7544-176">問號 (`?`) 字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-176">Question mark (`?`) character.</span></span>

<span data-ttu-id="b7544-177">下列清單包含 Unicode 分類描述。</span><span class="sxs-lookup"><span data-stu-id="b7544-177">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="b7544-178">如需詳細資訊，請參閱 [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory)。</span><span class="sxs-lookup"><span data-stu-id="b7544-178">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="b7544-179">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="b7544-179">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="b7544-180">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="b7544-180">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="b7544-181">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="b7544-181">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="b7544-182">**Lm** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="b7544-182">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="b7544-183">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="b7544-183">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="b7544-184">**Nd** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="b7544-184">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="b7544-185">若要建立或顯示包含空格或特殊字元的變數名稱，請用大括弧括住變數名稱， (`{}`) 個字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-185">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="b7544-186">大括弧會直接將變數名稱的字元解讀為常值。</span><span class="sxs-lookup"><span data-stu-id="b7544-186">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="b7544-187">特殊字元變數名稱可以包含下列字元：</span><span class="sxs-lookup"><span data-stu-id="b7544-187">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="b7544-188">任何 Unicode 字元，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b7544-188">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="b7544-189">右大括弧 (`}`) 字元 (U + 007D) 。</span><span class="sxs-lookup"><span data-stu-id="b7544-189">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="b7544-190">倒引號 (`` ` ``) 字元 (U + 0060) 。</span><span class="sxs-lookup"><span data-stu-id="b7544-190">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="b7544-191">倒引號是用來將 Unicode 字元換成常值，因此會被視為常值。</span><span class="sxs-lookup"><span data-stu-id="b7544-191">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="b7544-192">PowerShell 有包含英數位元 `$$` `$?` `$^` `$_` 和特殊字元的保留變數，例如、、和。</span><span class="sxs-lookup"><span data-stu-id="b7544-192">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="b7544-193">如需詳細資訊，請參閱 [about_Automatic_Variables](about_automatic_variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-193">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="b7544-194">例如，下列命令會建立名為的變數 `save-items` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-194">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="b7544-195">需要大括弧 (`{}`) ，因為變數名稱包含連字號 (`-`) 特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b7544-195">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="b7544-196">下列命令會取得環境變數所表示之目錄中的子專案 `ProgramFiles(x86)` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-196">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="b7544-197">若要參考包含大括弧的變數名稱，請以大括弧括住變數名稱，並使用倒引號字元來將大括弧換用。</span><span class="sxs-lookup"><span data-stu-id="b7544-197">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="b7544-198">例如，若要建立名為 type 的變數 `this{value}is` ：</span><span class="sxs-lookup"><span data-stu-id="b7544-198">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="b7544-199">變數和範圍</span><span class="sxs-lookup"><span data-stu-id="b7544-199">Variables and scope</span></span>

<span data-ttu-id="b7544-200">根據預設，變數僅適用于其建立所在的範圍。</span><span class="sxs-lookup"><span data-stu-id="b7544-200">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="b7544-201">例如，您在函式中建立的變數只能在函式內使用。</span><span class="sxs-lookup"><span data-stu-id="b7544-201">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="b7544-202">您在腳本中建立的變數只能在腳本中使用。</span><span class="sxs-lookup"><span data-stu-id="b7544-202">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="b7544-203">如果您是以點為來源的腳本，則會將變數加入至目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="b7544-203">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="b7544-204">如需詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-204">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="b7544-205">您可以使用範圍修飾符來變更變數的預設範圍。</span><span class="sxs-lookup"><span data-stu-id="b7544-205">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="b7544-206">下列運算式會建立名為的變數 `Computers` 。</span><span class="sxs-lookup"><span data-stu-id="b7544-206">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="b7544-207">變數有全域範圍，即使是在腳本或函式中建立也一樣。</span><span class="sxs-lookup"><span data-stu-id="b7544-207">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="b7544-208">針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="b7544-208">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="b7544-209">如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-209">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="b7544-210">儲存變數</span><span class="sxs-lookup"><span data-stu-id="b7544-210">Saving variables</span></span>

<span data-ttu-id="b7544-211">您建立的變數只能在您建立變數的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="b7544-211">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="b7544-212">當您關閉會話時，它們就會遺失。</span><span class="sxs-lookup"><span data-stu-id="b7544-212">They're lost when you close your session.</span></span>

<span data-ttu-id="b7544-213">若要在每個您啟動的 PowerShell 會話中建立變數，請將變數新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b7544-213">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="b7544-214">例如，若要變更 `$VerbosePreference` 每個 powershell 會話中的變數值，請將下列命令新增至您的 powershell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b7544-214">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="b7544-215">您可以 `$PROFILE` 在文字編輯器中開啟檔案（例如 **notepad.exe** ），將此命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b7544-215">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="b7544-216">如需 PowerShell 設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="b7544-216">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="b7544-217">Variable：磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="b7544-217">The Variable: drive</span></span>

<span data-ttu-id="b7544-218">PowerShell 變數提供者所建立的 `Variable:` 磁片磁碟機會像檔案系統磁片磁碟機一樣，但會包含會話中的變數及其值。</span><span class="sxs-lookup"><span data-stu-id="b7544-218">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="b7544-219">若要變更為 `Variable:` 磁片磁碟機，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="b7544-219">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="b7544-220">若要列出磁片磁碟機中的專案和變數 `Variable:` ，請使用 `Get-Item` 或 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7544-220">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="b7544-221">若要取得特定變數的值，請使用檔案系統標記法來指定磁片磁碟機的名稱和變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7544-221">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="b7544-222">例如，若要取得 `$PSCulture` 自動變數，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="b7544-222">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="b7544-223">若要顯示 `Variable:` 磁片磁碟機和 PowerShell 變數提供者的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b7544-223">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="b7544-224">具有提供者路徑的變數語法</span><span class="sxs-lookup"><span data-stu-id="b7544-224">Variable syntax with provider paths</span></span>

<span data-ttu-id="b7544-225">您可以在提供者路徑前面加上貨幣 (`$`) 號，並存取任何實 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 介面的提供者的內容。</span><span class="sxs-lookup"><span data-stu-id="b7544-225">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="b7544-226">下列內建 PowerShell 提供者支援此標記法：</span><span class="sxs-lookup"><span data-stu-id="b7544-226">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="b7544-227">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="b7544-227">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="b7544-228">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="b7544-228">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="b7544-229">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="b7544-229">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="b7544-230">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="b7544-230">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="b7544-231">變數 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b7544-231">The variable cmdlets</span></span>

<span data-ttu-id="b7544-232">PowerShell 包含一組設計來管理變數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b7544-232">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="b7544-233">若要列出 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b7544-233">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="b7544-234">若要取得特定 Cmdlet 的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b7544-234">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="b7544-235">指令程式名稱</span><span class="sxs-lookup"><span data-stu-id="b7544-235">Cmdlet Name</span></span>       | <span data-ttu-id="b7544-236">描述</span><span class="sxs-lookup"><span data-stu-id="b7544-236">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="b7544-237">刪除變數的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-237">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="b7544-238">取得目前主控台中的變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-238">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="b7544-239">建立新變數。</span><span class="sxs-lookup"><span data-stu-id="b7544-239">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="b7544-240">刪除變數和它的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-240">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="b7544-241">變更變數的值。</span><span class="sxs-lookup"><span data-stu-id="b7544-241">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="b7544-242">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7544-242">See also</span></span>

[<span data-ttu-id="b7544-243">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b7544-243">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="b7544-244">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="b7544-244">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="b7544-245">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="b7544-245">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="b7544-246">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="b7544-246">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="b7544-247">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="b7544-247">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="b7544-248">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b7544-248">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="b7544-249">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="b7544-249">about_Remote_Variables</span></span>](about_Remote_Variables.md)

