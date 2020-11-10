---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: ecf83a4dbf267fe105673e062740876156d18d49
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389771"
---
# <span data-ttu-id="7c847-103">Add-Member</span><span class="sxs-lookup"><span data-stu-id="7c847-103">Add-Member</span></span>

## <span data-ttu-id="7c847-104">概要</span><span class="sxs-lookup"><span data-stu-id="7c847-104">SYNOPSIS</span></span>
<span data-ttu-id="7c847-105">將自訂屬性和方法新增至 PowerShell 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="7c847-105">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="7c847-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7c847-106">SYNTAX</span></span>

### <span data-ttu-id="7c847-107">TypeNameSet (預設) </span><span class="sxs-lookup"><span data-stu-id="7c847-107">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="7c847-108">NotePropertyMultiMemberSet</span><span class="sxs-lookup"><span data-stu-id="7c847-108">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="7c847-109">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="7c847-109">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="7c847-110">MemberSet</span><span class="sxs-lookup"><span data-stu-id="7c847-110">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="7c847-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7c847-111">DESCRIPTION</span></span>

<span data-ttu-id="7c847-112">此 `Add-Member` Cmdlet 可讓您將成員 (屬性和方法) 加入至 PowerShell 物件的實例。</span><span class="sxs-lookup"><span data-stu-id="7c847-112">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="7c847-113">例如，您可以加入包含物件描述的 NoteProperty 成員，或是執行腳本來變更物件的 **ScriptMethod** 成員。</span><span class="sxs-lookup"><span data-stu-id="7c847-113">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="7c847-114">若要使用 `Add-Member` ，請使用管線將物件傳送至 `Add-Member` ，或使用 **InputObject** 參數指定物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-114">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="7c847-115">**MemberType** 參數會指出您要加入的成員類型。</span><span class="sxs-lookup"><span data-stu-id="7c847-115">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="7c847-116">**Name** 參數會指派名稱給新的成員，而 **Value** 參數會設定成員的值。</span><span class="sxs-lookup"><span data-stu-id="7c847-116">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="7c847-117">您新增的屬性和方法只會新增到您指定之物件特定的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7c847-117">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="7c847-118">`Add-Member` 不會變更物件類型。</span><span class="sxs-lookup"><span data-stu-id="7c847-118">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="7c847-119">若要建立新的物件類型，請使用 `Add-Type` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c847-119">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="7c847-120">您也可以使用 `Export-Clixml` Cmdlet，將物件的實例（包括其他成員）儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="7c847-120">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="7c847-121">然後，您可以使用 `Import-Clixml` Cmdlet，從儲存在匯出檔案中的資訊重新建立物件的實例。</span><span class="sxs-lookup"><span data-stu-id="7c847-121">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="7c847-122">從 Windows PowerShell 3.0 開始， `Add-Member` 有新功能可讓您更輕鬆地將附注屬性新增至物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-122">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="7c847-123">您可以使用 **NotePropertyName** 和 **NotePropertyValue** 參數來定義附註屬性，或使用 **NotePropertyMembers** 參數以採用附註屬性名稱和值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="7c847-123">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="7c847-124">此外，自 Windows PowerShell 3.0 起，需使用會產生輸出物件之 **PassThru** 參數的頻率較少。</span><span class="sxs-lookup"><span data-stu-id="7c847-124">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="7c847-125">`Add-Member` 現在將新成員直接新增至更多類型的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-125">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="7c847-126">如需詳細資訊，請參閱 **PassThru** 參數描述。</span><span class="sxs-lookup"><span data-stu-id="7c847-126">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="7c847-127">範例</span><span class="sxs-lookup"><span data-stu-id="7c847-127">EXAMPLES</span></span>

### <span data-ttu-id="7c847-128">範例1：將附注屬性新增至 PSObject</span><span class="sxs-lookup"><span data-stu-id="7c847-128">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="7c847-129">下列範例會將值為 "Done" 的 **狀態** 附注屬性新增至代表檔案的 **FileInfo** 物件 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-129">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="7c847-130">第一個命令會使用 `Get-ChildItem` Cmdlet 取得代表檔案的 **FileInfo** 物件 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-130">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="7c847-131">它會將它儲存在 `$a` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7c847-131">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="7c847-132">第二個命令會將附注屬性新增至中的物件 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-132">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="7c847-133">第三個命令使用點標記法來取得中物件的 **Status** 屬性值 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-133">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="7c847-134">如輸出所示，值為「完成」。</span><span class="sxs-lookup"><span data-stu-id="7c847-134">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="7c847-135">範例2：將別名屬性新增至 PSObject</span><span class="sxs-lookup"><span data-stu-id="7c847-135">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="7c847-136">下列範例會將 **大小** 別名屬性新增至代表檔案的物件 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-136">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="7c847-137">新屬性是 **Length** 屬性的別名。</span><span class="sxs-lookup"><span data-stu-id="7c847-137">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="7c847-138">第一個命令會使用 `Get-ChildItem` Cmdlet 來取得 `Test.txt` **FileInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-138">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="7c847-139">第二個命令會新增 [ **大小** 別名] 屬性。</span><span class="sxs-lookup"><span data-stu-id="7c847-139">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="7c847-140">第三個命令使用點標記法來取得新的 **大小** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="7c847-140">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="7c847-141">範例3：將 StringUse note 屬性新增至字串</span><span class="sxs-lookup"><span data-stu-id="7c847-141">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="7c847-142">此範例會將 **StringUse** note 屬性新增至字串。</span><span class="sxs-lookup"><span data-stu-id="7c847-142">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="7c847-143">因為 `Add-Member` 無法將類型新增至 **字串** 輸入物件，所以您可以指定 **PassThru** 參數來產生輸出物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-143">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="7c847-144">範例中的最後一個命令會顯示新的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c847-144">The last command in the example displays the new property.</span></span>

<span data-ttu-id="7c847-145">此範例使用 **NotePropertyMembers** 參數。</span><span class="sxs-lookup"><span data-stu-id="7c847-145">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="7c847-146">**NotePropertyMembers** 參數的值為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="7c847-146">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="7c847-147">索引鍵是附注屬性名稱 **StringUse** ，而值則是附注屬性值 [ **顯示** ]。</span><span class="sxs-lookup"><span data-stu-id="7c847-147">The key is the note property name, **StringUse** , and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="7c847-148">範例4：將腳本方法新增至 FileInfo 物件</span><span class="sxs-lookup"><span data-stu-id="7c847-148">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="7c847-149">此範例會將 **SizeInMB** 腳本方法新增至 **FileInfo** 物件，此物件會將檔案大小計算為最接近的 mb。</span><span class="sxs-lookup"><span data-stu-id="7c847-149">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="7c847-150">第二個命令會建立 **ScriptBlock** ，以使用類型的 **round** 靜態方法，將檔案 `[math]` 大小舍入至第二個小數位數。</span><span class="sxs-lookup"><span data-stu-id="7c847-150">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="7c847-151">**Value** 參數也會使用 `$This` 代表目前物件的自動變數。</span><span class="sxs-lookup"><span data-stu-id="7c847-151">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="7c847-152">`$This`變數只有在定義新屬性和方法的腳本區塊中才有效。</span><span class="sxs-lookup"><span data-stu-id="7c847-152">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="7c847-153">最後一個命令會使用點標記法，在變數中的物件上呼叫新的 **SizeInMB** 腳本方法 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-153">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="7c847-154">範例5：將物件的所有屬性複製到另一個</span><span class="sxs-lookup"><span data-stu-id="7c847-154">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="7c847-155">此函式會將一個物件的所有屬性複製到另一個物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-155">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="7c847-156">`foreach`迴圈會使用 `Get-Member` Cmdlet 來取得 **From** 物件的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="7c847-156">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="7c847-157">迴圈內的命令 `foreach` 會在每個屬性的數列中執行。</span><span class="sxs-lookup"><span data-stu-id="7c847-157">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="7c847-158">此 `Add-Member` 命令會將 **From** 物件的屬性新增至 **To** 物件做為 **NoteProperty** 。</span><span class="sxs-lookup"><span data-stu-id="7c847-158">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="7c847-159">使用 **value** 參數來複製值。</span><span class="sxs-lookup"><span data-stu-id="7c847-159">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="7c847-160">它會使用 **Force** 參數來加入具有相同成員名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="7c847-160">It uses the **Force** parameter to add members with the same member name.</span></span>

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### <span data-ttu-id="7c847-161">範例6：建立自訂物件</span><span class="sxs-lookup"><span data-stu-id="7c847-161">Example 6: Create a custom object</span></span>

<span data-ttu-id="7c847-162">這個範例會建立 **資產** 自訂物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-162">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="7c847-163">`New-Object`Cmdlet 會建立 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="7c847-163">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="7c847-164">此範例會將 **PSObject** 儲存在 `$Asset` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7c847-164">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="7c847-165">第二個命令使用 `[ordered]` 類型加速器來建立名稱和值的已排序字典。</span><span class="sxs-lookup"><span data-stu-id="7c847-165">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="7c847-166">命令會將結果儲存在 `$D` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7c847-166">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="7c847-167">第三個命令會使用 Cmdlet 的 **NotePropertyMembers** 參數 `Add-Member` ，將變數中的字典新增 `$D` 至 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="7c847-167">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="7c847-168">**TypeName** 屬性會將新的名稱、 **資產** 指派給 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="7c847-168">The **TypeName** property assigns a new name, **Asset** , to the **PSObject**.</span></span>

<span data-ttu-id="7c847-169">最後一個命令會將新 **資產** 物件輸送至 `Get-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c847-169">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="7c847-170">輸出顯示物件具有 **資產** 的類型名稱，以及我們在排序的字典中定義的附注屬性。</span><span class="sxs-lookup"><span data-stu-id="7c847-170">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## <span data-ttu-id="7c847-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c847-171">PARAMETERS</span></span>

### <span data-ttu-id="7c847-172">-Force</span><span class="sxs-lookup"><span data-stu-id="7c847-172">-Force</span></span>

<span data-ttu-id="7c847-173">指出此 Cmdlet 會加入新成員，即使該物件具有相同名稱的自訂成員。</span><span class="sxs-lookup"><span data-stu-id="7c847-173">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="7c847-174">您無法使用 **Force** 參數來取代型別的標準成員。</span><span class="sxs-lookup"><span data-stu-id="7c847-174">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-175">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7c847-175">-InputObject</span></span>

<span data-ttu-id="7c847-176">指定要新增成員的物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-176">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="7c847-177">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="7c847-177">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-178">-MemberType</span><span class="sxs-lookup"><span data-stu-id="7c847-178">-MemberType</span></span>

<span data-ttu-id="7c847-179">指定要加入之成員的類型。</span><span class="sxs-lookup"><span data-stu-id="7c847-179">Specifies the type of the member to add.</span></span>
<span data-ttu-id="7c847-180">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="7c847-180">This parameter is required.</span></span>
<span data-ttu-id="7c847-181">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="7c847-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7c847-182">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="7c847-182">NoteProperty</span></span>
- <span data-ttu-id="7c847-183">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="7c847-183">AliasProperty</span></span>
- <span data-ttu-id="7c847-184">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="7c847-184">ScriptProperty</span></span>
- <span data-ttu-id="7c847-185">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="7c847-185">CodeProperty</span></span>
- <span data-ttu-id="7c847-186">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="7c847-186">ScriptMethod</span></span>
- <span data-ttu-id="7c847-187">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="7c847-187">CodeMethod</span></span>

<span data-ttu-id="7c847-188">如需這些值的詳細資訊，請參閱 PowerShell SDK 中的 [ Psmembertypes 列舉](/dotnet/api/system.management.automation.psmembertypes) 。</span><span class="sxs-lookup"><span data-stu-id="7c847-188">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the PowerShell SDK.</span></span>

<span data-ttu-id="7c847-189">並非所有物件都有每個類型的成員。</span><span class="sxs-lookup"><span data-stu-id="7c847-189">Not all objects have every type of member.</span></span>
<span data-ttu-id="7c847-190">如果您指定物件沒有的成員類型，PowerShell 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7c847-190">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-191">-Name</span><span class="sxs-lookup"><span data-stu-id="7c847-191">-Name</span></span>

<span data-ttu-id="7c847-192">指定此 Cmdlet 新增的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="7c847-192">Specifies the name of the member that this cmdlet adds.</span></span>

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-193">-NotePropertyMembers</span><span class="sxs-lookup"><span data-stu-id="7c847-193">-NotePropertyMembers</span></span>

<span data-ttu-id="7c847-194">指定內容是附註屬性名稱和值的雜湊表或排序的字典。</span><span class="sxs-lookup"><span data-stu-id="7c847-194">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="7c847-195">輸入其中的索引鍵為附註屬性名稱且值為附註屬性值的雜湊表或字典。</span><span class="sxs-lookup"><span data-stu-id="7c847-195">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="7c847-196">如需 PowerShell 中雜湊表和已排序字典的詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="7c847-196">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="7c847-197">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="7c847-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-198">-NotePropertyName</span><span class="sxs-lookup"><span data-stu-id="7c847-198">-NotePropertyName</span></span>

<span data-ttu-id="7c847-199">指定附注屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7c847-199">Specifies the note property name.</span></span>

<span data-ttu-id="7c847-200">請使用此參數搭配 **NotePropertyValue** 參數。</span><span class="sxs-lookup"><span data-stu-id="7c847-200">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="7c847-201">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="7c847-201">This parameter is optional.</span></span>

<span data-ttu-id="7c847-202">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="7c847-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-203">-NotePropertyValue</span><span class="sxs-lookup"><span data-stu-id="7c847-203">-NotePropertyValue</span></span>

<span data-ttu-id="7c847-204">指定附注屬性值。</span><span class="sxs-lookup"><span data-stu-id="7c847-204">Specifies the note property value.</span></span>

<span data-ttu-id="7c847-205">使用此參數搭配 **NotePropertyName** 參數。</span><span class="sxs-lookup"><span data-stu-id="7c847-205">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="7c847-206">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="7c847-206">This parameter is optional.</span></span>

<span data-ttu-id="7c847-207">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="7c847-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-208">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7c847-208">-PassThru</span></span>

<span data-ttu-id="7c847-209">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-209">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="7c847-210">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="7c847-210">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="7c847-211">針對大部分的物件， `Add-Member` 將新成員新增至輸入物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-211">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="7c847-212">但是，當輸入物件是字串時， `Add-Member` 無法將成員加入至輸入物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-212">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="7c847-213">對於這些物件，使用 **PassThru** 參數可建立輸出物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-213">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="7c847-214">在 Windows PowerShell 2.0 中， `Add-Member` 僅將成員新增至物件的 **PSObject** 包裝函式，而非物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-214">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="7c847-215">使用 **PassThru** 參數，為具有 **PSObject** 包裝函式的任何物件建立輸出物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-215">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

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

### <span data-ttu-id="7c847-216">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="7c847-216">-SecondValue</span></span>

<span data-ttu-id="7c847-217">指定與 **AliasProperty** 、 **ScriptProperty** 、 **CodeProperty** 或 **CodeMethod** 成員相關的其他選擇性資訊。</span><span class="sxs-lookup"><span data-stu-id="7c847-217">Specifies optional additional information about **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="7c847-218">如果在加入 **AliasProperty** 時使用，則這個參數必須是資料類型。</span><span class="sxs-lookup"><span data-stu-id="7c847-218">If used when adding an **AliasProperty** , this parameter must be a data type.</span></span>
<span data-ttu-id="7c847-219">將轉換成指定的資料類型會新增至 **AliasProperty** 的值。</span><span class="sxs-lookup"><span data-stu-id="7c847-219">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="7c847-220">例如，如果您加入的 **AliasProperty** 會為字串屬性提供替代名稱，您也可以指定 System.string 的 **SecondValue** 參數 **，以指出** 在使用對應的 **AliasProperty** 存取時，該字串屬性的值應轉換成整數。</span><span class="sxs-lookup"><span data-stu-id="7c847-220">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="7c847-221">新增 **ScriptProperty** 成員時，您可以使用 **SecondValue** 參數來指定額外的 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="7c847-221">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="7c847-222">在 **Value** 參數中指定的第一個 **ScriptBlock** 會用來取得變數的值。</span><span class="sxs-lookup"><span data-stu-id="7c847-222">The first **ScriptBlock** , specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="7c847-223">在 **SecondValue** 參數中指定的第二個 **ScriptBlock** 會用來設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="7c847-223">The second **ScriptBlock** , specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-224">-Value</span><span class="sxs-lookup"><span data-stu-id="7c847-224">-Value</span></span>

<span data-ttu-id="7c847-225">指定已新增成員的初始值。</span><span class="sxs-lookup"><span data-stu-id="7c847-225">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="7c847-226">如果您加入 **AliasProperty** 、 **CodeProperty** 、 **ScriptProperty** 或 **CodeMethod** 成員，您可以使用 **SecondValue** 參數來提供選擇性的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="7c847-226">If you add an **AliasProperty** , **CodeProperty** , **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-227">-TypeName</span><span class="sxs-lookup"><span data-stu-id="7c847-227">-TypeName</span></span>

<span data-ttu-id="7c847-228">指定類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c847-228">Specifies a name for the type.</span></span>

<span data-ttu-id="7c847-229">當類型是 **System** 命名空間中的類別或具有類型加速器的類型時，您可以輸入類型的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="7c847-229">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="7c847-230">否則，需要完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="7c847-230">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="7c847-231">只有當 **InputObject** 為 **PSObject** 時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="7c847-231">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="7c847-232">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="7c847-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c847-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c847-233">CommonParameters</span></span>

<span data-ttu-id="7c847-234">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7c847-234">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c847-235">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7c847-235">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7c847-236">輸入</span><span class="sxs-lookup"><span data-stu-id="7c847-236">INPUTS</span></span>

### <span data-ttu-id="7c847-237">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="7c847-237">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7c847-238">您可以透過管線將任何物件類型傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7c847-238">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="7c847-239">輸出</span><span class="sxs-lookup"><span data-stu-id="7c847-239">OUTPUTS</span></span>

### <span data-ttu-id="7c847-240">None 或 System.object</span><span class="sxs-lookup"><span data-stu-id="7c847-240">None or System.Object</span></span>

<span data-ttu-id="7c847-241">當您使用 **PassThru** 參數時，此 Cmdlet 會傳回新擴充的物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-241">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="7c847-242">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="7c847-242">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7c847-243">注意</span><span class="sxs-lookup"><span data-stu-id="7c847-243">NOTES</span></span>

<span data-ttu-id="7c847-244">您只能將成員新增到 **PSObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="7c847-244">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="7c847-245">若要判斷物件是否為 **PSObject** 物件，請使用 `-is` 運算子。</span><span class="sxs-lookup"><span data-stu-id="7c847-245">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="7c847-246">例如，若要測試儲存在變數中的物件 `$obj` ，請輸入 `$obj -is [PSObject]` 。</span><span class="sxs-lookup"><span data-stu-id="7c847-246">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="7c847-247">**MemberType** 、 **Name** 、 **Value** 和 **SecondValue** 參數的名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="7c847-247">The names of the **MemberType** , **Name** , **Value** , and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="7c847-248">如果您省略參數名稱，未命名的參數值必須以下列順序顯示： **MemberType** 、 **Name** 、 **Value** 和 **SecondValue** 。</span><span class="sxs-lookup"><span data-stu-id="7c847-248">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType** , **Name** , **Value** , and **SecondValue**.</span></span>

<span data-ttu-id="7c847-249">如果包含參數名稱，參數可以任何順序顯示。</span><span class="sxs-lookup"><span data-stu-id="7c847-249">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="7c847-250">您可以 `$this` 在定義新屬性和方法之值的腳本區塊中使用自動變數。</span><span class="sxs-lookup"><span data-stu-id="7c847-250">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="7c847-251">`$this`變數是指要加入屬性和方法之物件的實例。</span><span class="sxs-lookup"><span data-stu-id="7c847-251">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="7c847-252">如需變數的詳細資訊 `$this` ，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="7c847-252">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="7c847-253">相關連結</span><span class="sxs-lookup"><span data-stu-id="7c847-253">RELATED LINKS</span></span>

[<span data-ttu-id="7c847-254">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="7c847-254">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="7c847-255">Get-Member</span><span class="sxs-lookup"><span data-stu-id="7c847-255">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="7c847-256">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="7c847-256">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="7c847-257">New-Object</span><span class="sxs-lookup"><span data-stu-id="7c847-257">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="7c847-258">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="7c847-258">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)
