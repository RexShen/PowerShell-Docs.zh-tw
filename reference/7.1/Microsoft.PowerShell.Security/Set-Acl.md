---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: a4c25d199b97be24277092bcb815a640a09360dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202467"
---
# <span data-ttu-id="4e9b0-103">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="4e9b0-103">Set-Acl</span></span>

## <span data-ttu-id="4e9b0-104">概要</span><span class="sxs-lookup"><span data-stu-id="4e9b0-104">SYNOPSIS</span></span>
<span data-ttu-id="4e9b0-105">變更指定項目的安全性描述元，例如檔案或登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-105">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

## <span data-ttu-id="4e9b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e9b0-106">SYNTAX</span></span>

### <span data-ttu-id="4e9b0-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="4e9b0-107">ByPath (Default)</span></span>

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e9b0-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="4e9b0-108">ByInputObject</span></span>

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e9b0-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="4e9b0-109">ByLiteralPath</span></span>

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4e9b0-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4e9b0-110">DESCRIPTION</span></span>

<span data-ttu-id="4e9b0-111">指令程式會 `Set-Acl` 變更指定專案（例如，檔案或登錄機碼）的安全描述項，以符合您提供的安全描述項中的值。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-111">The `Set-Acl` cmdlet changes the security descriptor of a specified item, such as a file or a registry key, to match the values in a security descriptor that you supply.</span></span>

<span data-ttu-id="4e9b0-112">若要使用 `Set-Acl` ，請使用 **Path** 或 **InputObject** 參數來識別您想要變更其安全描述項的專案。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-112">To use `Set-Acl`, use the **Path** or **InputObject** parameter to identify the item whose security descriptor you want to change.</span></span> <span data-ttu-id="4e9b0-113">然後使用 **AclObject** 或 **SecurityDescriptor** 參數，提供擁有您想要套用之值的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-113">Then, use the **AclObject** or **SecurityDescriptor** parameters to supply a security descriptor that has the values you want to apply.</span></span> <span data-ttu-id="4e9b0-114">`Set-Acl` 套用提供的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-114">`Set-Acl` applies the security descriptor that is supplied.</span></span> <span data-ttu-id="4e9b0-115">它使用 **AclObject** 參數的值作為模型，並變更項目安全性描述元中的值，以符合 **AclObject** 參數中的值。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-115">It uses the value of the **AclObject** parameter as a model and changes the values in the item's security descriptor to match the values in the **AclObject** parameter.</span></span>

## <span data-ttu-id="4e9b0-116">範例</span><span class="sxs-lookup"><span data-stu-id="4e9b0-116">EXAMPLES</span></span>

### <span data-ttu-id="4e9b0-117">範例1：將安全描述項從一個檔案複製到另一個檔案</span><span class="sxs-lookup"><span data-stu-id="4e9b0-117">Example 1: Copy a security descriptor from one file to another</span></span>

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

<span data-ttu-id="4e9b0-118">這些命令會將值從 Dog.txt 檔案的安全性描述元複製到 Cat.txt 檔案的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-118">These commands copy the values from the security descriptor of the Dog.txt file to the security descriptor of the Cat.txt file.</span></span> <span data-ttu-id="4e9b0-119">當命令完成時，Dog.txt 和 Cat.txt 檔案的安全性描述元會完全相同。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-119">When the commands complete, the security descriptors of the Dog.txt and Cat.txt files are identical.</span></span>

<span data-ttu-id="4e9b0-120">第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>
<span data-ttu-id="4e9b0-121">指派運算子 () 會將 `=` 安全描述項儲存在 $DogACL 變數的值中。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-121">The assignment operator (`=`) stores the security descriptor in the value of the $DogACL variable.</span></span>

<span data-ttu-id="4e9b0-122">第二個命令會使用 `Set-Acl` 將 Cat.txt 之 ACL 中的值變更為中的值 `$DogACL` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-122">The second command uses `Set-Acl` to change the values in the ACL of Cat.txt to the values in `$DogACL`.</span></span>

<span data-ttu-id="4e9b0-123">**Path** 參數的值是 Cat.txt 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-123">The value of the **Path** parameter is the path to the Cat.txt file.</span></span> <span data-ttu-id="4e9b0-124">**AclObject** 參數的值為模型 acl，在此案例中，會將 Dog.txt 的 acl 儲存在 `$DogACL` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-124">The value of the **AclObject** parameter is the model ACL, in this case, the ACL of Dog.txt as saved in the `$DogACL` variable.</span></span>

### <span data-ttu-id="4e9b0-125">範例2：使用管線運算子來傳遞描述項</span><span class="sxs-lookup"><span data-stu-id="4e9b0-125">Example 2: Use the pipeline operator to pass a descriptor</span></span>

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

<span data-ttu-id="4e9b0-126">此命令與上一個範例中的命令幾乎相同，不同之處在于它會使用管線運算子 (`|`) 將安全描述項從 `Get-Acl` 命令傳送至 `Set-Acl` 命令。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-126">This command is almost the same as the command in the previous example, except that it uses a pipeline operator (`|`) to send the security descriptor from a `Get-Acl` command to a `Set-Acl` command.</span></span>

<span data-ttu-id="4e9b0-127">第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-127">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span> <span data-ttu-id="4e9b0-128">管線運算子 (`|`) 會將代表 Dog.txt 安全描述項的物件傳遞給 `Set-Acl` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-128">The pipeline operator (`|`) passes an object that represents the Dog.txt security descriptor to the `Set-Acl` cmdlet.</span></span>

<span data-ttu-id="4e9b0-129">第二個命令會使用將 `Set-Acl` Dog.txt 的安全描述項套用至 Cat.txt。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-129">The second command uses `Set-Acl` to apply the security descriptor of Dog.txt to Cat.txt.</span></span>
<span data-ttu-id="4e9b0-130">當命令完成時，Dog.txt 和 Cat.txt 檔案的 ACL 會完全相同。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-130">When the command completes, the ACLs of the Dog.txt and Cat.txt files are identical.</span></span>

### <span data-ttu-id="4e9b0-131">範例3：將安全描述項套用至多個檔案</span><span class="sxs-lookup"><span data-stu-id="4e9b0-131">Example 3: Apply a security descriptor to multiple files</span></span>

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

<span data-ttu-id="4e9b0-132">這些命令會將 File0.txt 檔案中的安全描述項套用至 `C:\Temp` 目錄及其所有子目錄中的所有文字檔。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-132">These commands apply the security descriptors in the File0.txt file to all text files in the `C:\Temp` directory and all of its subdirectories.</span></span>

<span data-ttu-id="4e9b0-133">第一個命令會取得目前目錄中 File0.txt 檔案的安全描述項，並使用指派運算子 (`=`) 將它儲存在 `$NewACL` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-133">The first command gets the security descriptor of the File0.txt file in the current directory and uses the assignment operator (`=`) to store it in the `$NewACL` variable.</span></span>

<span data-ttu-id="4e9b0-134">管線中的第一個命令會使用 Get-ChildItem Cmdlet 來取得目錄中的所有文字檔 `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-134">The first command in the pipeline uses the Get-ChildItem cmdlet to get all of the text files in the `C:\Temp` directory.</span></span> <span data-ttu-id="4e9b0-135">**遞迴** 參數會將命令延伸至的所有子目錄 `C:\temp` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-135">The **Recurse** parameter extends the command to all subdirectories of `C:\temp`.</span></span> <span data-ttu-id="4e9b0-136">**Include** 參數會將取出的檔案限制為副檔名為的檔案 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-136">The **Include** parameter limits the files retrieved to those with the `.txt` file name extension.</span></span> <span data-ttu-id="4e9b0-137">**Force** 參數可取得隱藏的檔案，若沒有使用此參數則會排除這些檔案。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-137">The **Force** parameter gets hidden files, which would otherwise be excluded.</span></span> <span data-ttu-id="4e9b0-138"> (您無法使用 `c:\temp\*.txt` ，因為 **遞迴** 參數適用于目錄，而不是在檔案上。 ) </span><span class="sxs-lookup"><span data-stu-id="4e9b0-138">(You cannot use `c:\temp\*.txt`, because the **Recurse** parameter works on directories, not on files.)</span></span>

<span data-ttu-id="4e9b0-139">管線運算子 () 會將代表抓取之檔案的 `|` 物件傳送至 `Set-Acl` Cmdlet，此 Cmdlet 會將 **AclObject** 參數中的安全描述項套用至管線中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-139">The pipeline operator (`|`) sends the objects representing the retrieved files to the `Set-Acl` cmdlet, which applies the security descriptor in the **AclObject** parameter to all of the files in the pipeline.</span></span>

<span data-ttu-id="4e9b0-140">在實務上，最好是將 **WhatIf** 參數與所有 `Set-Acl` 可能影響一個以上專案的命令搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-140">In practice, it is best to use the **WhatIf** parameter with all `Set-Acl` commands that can affect more than one item.</span></span> <span data-ttu-id="4e9b0-141">在此情況下，管線中的第二個命令會是 `Set-Acl -AclObject $NewAcl -WhatIf` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-141">In this case, the second command in the pipeline would be `Set-Acl -AclObject $NewAcl -WhatIf`.</span></span> <span data-ttu-id="4e9b0-142">此命令可列出會受命令影響的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-142">This command lists the files that would be affected by the command.</span></span> <span data-ttu-id="4e9b0-143">查看結果之後，您可以在沒有 **WhatIf** 參數的情況下再次執行命令。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-143">After reviewing the result, you can run the command again without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="4e9b0-144">範例4：停用繼承並保留繼承的存取規則</span><span class="sxs-lookup"><span data-stu-id="4e9b0-144">Example 4: Disable inheritance and preserve inherited access rules</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="4e9b0-145">這些命令會停用從父資料夾繼承的存取，同時仍然保留現有的繼承存取規則。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-145">These commands is will disable access inheritance from parent folders, while still preserving the existing inherited access rules.</span></span>

<span data-ttu-id="4e9b0-146">第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-146">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="4e9b0-147">接下來，會建立變數，以將繼承的存取規則轉換成明確的存取規則。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-147">Next, variables are created to convert the inherited access rules to explicit access rules.</span></span> <span data-ttu-id="4e9b0-148">若要保護與這個繼承的存取規則，請將 `$isProtected` 變數設為 `$true` 。若要允許繼承，請將設定 `$isProtected` 為 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-148">To protect the access rules associated with this from inheritance, set the `$isProtected` variable to `$true`.to allow inheritance, set `$isProtected` to `$false`.</span></span> <span data-ttu-id="4e9b0-149">如需詳細資訊，請參閱 [設定存取規則保護](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-149">For more information, see [set access rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span></span>
<span data-ttu-id="4e9b0-150">將 `$preserveInheritance` 變數設為 `$true` 以保留繼承的存取規則; false 則會移除繼承的存取規則。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-150">The `$preserveInheritance` variable set to `$true` to preserve inherited access rules; false to remove inherited access rules.</span></span> <span data-ttu-id="4e9b0-151">然後使用 **SetAccessRuleProtection ( # B1** 方法更新存取規則保護。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-151">Then the access rule protection is updated using the **SetAccessRuleProtection()** method.</span></span>

<span data-ttu-id="4e9b0-152">最後一個命令會使用將的 `Set-Acl` 安全描述項套用至 Dog.txt。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-152">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="4e9b0-153">當命令完成時，繼承自 [寵物] 資料夾的 Dog.txt Acl 將會直接套用至 Dog.txt，而新增至寵物的新存取原則將不會變更 Dog.txt 的存取權。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-153">When the command completes, the ACLs of the Dog.txt that were inherited from the Pets folder will be applied directly to Dog.txt, and new access policies added to Pets will not change the access to Dog.txt.</span></span>

### <span data-ttu-id="4e9b0-154">範例5：將檔案的完整控制權授與系統管理員</span><span class="sxs-lookup"><span data-stu-id="4e9b0-154">Example 5: Grant Administrators Full Control of the file</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="4e9b0-155">此命令會將 Dog.txt 檔案的完整控制權授與 **BUILTIN\Administrators** 群組。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-155">This command will grant the **BUILTIN\Administrators** group Full control of the Dog.txt file.</span></span>

<span data-ttu-id="4e9b0-156">第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-156">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="4e9b0-157">系統會建立下一個變數，以授與 **BUILTIN\Administrators** 群組 Dog.txt 檔案的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-157">Next variables are created to grant the **BUILTIN\Administrators** group full control of the Dog.txt file.</span></span> <span data-ttu-id="4e9b0-158">`$identity`設定為[使用者帳戶](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-158">The `$identity` variable set to the name of a [user account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span></span>
<span data-ttu-id="4e9b0-159">將 `$fileSystemRights` 變數設定為 FullControl，而且可以是任何一個指定與存取規則相關聯之作業類型的 [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) 值。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-159">The `$fileSystemRights` variable set to FullControl, and can be any one of the [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) values that specifies the type of operation associated with the access rule.</span></span> <span data-ttu-id="4e9b0-160">將 `$type` 變數設定為「允許」以指定是否要允許或拒絕作業。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-160">The `$type` variable set to "Allow" to specifies whether to allow or deny the operation.</span></span> <span data-ttu-id="4e9b0-161">`$fileSystemAccessRuleArgumentList`變數是在建立新的 **system.security.accesscontrol.filesystemaccessrule** 物件時，要傳遞的引數清單。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-161">The `$fileSystemAccessRuleArgumentList` variable is an argument list is to be passed when making the new **FileSystemAccessRule** object.</span></span> <span data-ttu-id="4e9b0-162">然後會建立新的 **system.security.accesscontrol.filesystemaccessrule** 物件，並將 **system.security.accesscontrol.filesystemaccessrule** 物件傳遞給 **SetAccessRule ( # B1** 方法，以加入新的存取規則。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-162">Then a new **FileSystemAccessRule** object is created, and the **FileSystemAccessRule** object is passed to the **SetAccessRule()** method, adds the new access rule.</span></span>

<span data-ttu-id="4e9b0-163">最後一個命令會使用將的 `Set-Acl` 安全描述項套用至 Dog.txt。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-163">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span>
<span data-ttu-id="4e9b0-164">當命令完成時， **BUILTIN\Administrators** 群組將擁有 Dog.txt 的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-164">When the command completes, the **BUILTIN\Administrators** group will have full control of the Dog.txt.</span></span>

## <span data-ttu-id="4e9b0-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e9b0-165">PARAMETERS</span></span>

### <span data-ttu-id="4e9b0-166">-AclObject</span><span class="sxs-lookup"><span data-stu-id="4e9b0-166">-AclObject</span></span>

<span data-ttu-id="4e9b0-167">將所要的屬性值指定給 ACL。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-167">Specifies an ACL with the desired property values.</span></span> <span data-ttu-id="4e9b0-168">`Set-Acl` 變更 **Path** 或 **InputObject** 參數所指定之專案的 ACL，以符合指定之安全性物件中的值。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-168">`Set-Acl` changes the ACL of item specified by the **Path** or **InputObject** parameter to match the values in the specified security object.</span></span>

<span data-ttu-id="4e9b0-169">您可以將命令的輸出儲存 `Get-Acl` 在變數中，然後使用 **AclObject** 參數傳遞變數或輸入 `Get-Acl` 命令。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-169">You can save the output of a `Get-Acl` command in a variable and then use the **AclObject** parameter to pass the variable, or type a `Get-Acl` command.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4e9b0-170">-ClearCentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="4e9b0-170">-ClearCentralAccessPolicy</span></span>

<span data-ttu-id="4e9b0-171">從指定項目移除集中存取原則。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-171">Removes the central access policy from the specified item.</span></span>

<span data-ttu-id="4e9b0-172">從 Windows Server 2012 開始，系統管理員可以使用 Active Directory 和群組原則為使用者和群組設定集中存取原則。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-172">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="4e9b0-173">如需詳細資訊，請參閱 [動態存取控制：案例總覽](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-173">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="4e9b0-174">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e9b0-175">-Exclude</span><span class="sxs-lookup"><span data-stu-id="4e9b0-175">-Exclude</span></span>

<span data-ttu-id="4e9b0-176">省略指定的項目。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-176">Omits the specified items.</span></span> <span data-ttu-id="4e9b0-177">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-177">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4e9b0-178">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-178">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4e9b0-179">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-179">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4e9b0-180">-Filter</span><span class="sxs-lookup"><span data-stu-id="4e9b0-180">-Filter</span></span>

<span data-ttu-id="4e9b0-181">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-181">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="4e9b0-182">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4e9b0-183">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-183">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="4e9b0-184">篩選比其他參數更有效率，因為提供者會在抓取物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-184">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4e9b0-185">-Include</span><span class="sxs-lookup"><span data-stu-id="4e9b0-185">-Include</span></span>

<span data-ttu-id="4e9b0-186">只變更指定的項目。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-186">Changes only the specified items.</span></span> <span data-ttu-id="4e9b0-187">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-187">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="4e9b0-188">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4e9b0-189">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-189">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4e9b0-190">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4e9b0-190">-InputObject</span></span>

<span data-ttu-id="4e9b0-191">變更指定物件的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-191">Changes the security descriptor of the specified object.</span></span> <span data-ttu-id="4e9b0-192">輸入包含物件的變數，或輸入可取得物件的命令。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-192">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="4e9b0-193">您無法將要變更的物件傳送至 `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-193">You cannot pipe the object to be changed to `Set-Acl`.</span></span> <span data-ttu-id="4e9b0-194">請改為在命令中明確地使用 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-194">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="4e9b0-195">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4e9b0-196">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4e9b0-196">-LiteralPath</span></span>

<span data-ttu-id="4e9b0-197">變更指定項目的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-197">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="4e9b0-198">與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-198">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="4e9b0-199">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-199">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4e9b0-200">如果路徑包含 escape 字元，請將它括在單引號中 (`'`) 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-200">If the path includes escape characters, enclose it in single quotation marks (`'`).</span></span>
<span data-ttu-id="4e9b0-201">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="4e9b0-202">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="4e9b0-203">-Passthru</span><span class="sxs-lookup"><span data-stu-id="4e9b0-203">-Passthru</span></span>

<span data-ttu-id="4e9b0-204">傳回代表已變更安全性描述元的物件。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-204">Returns an object that represents the security descriptor that was changed.</span></span> <span data-ttu-id="4e9b0-205">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-205">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4e9b0-206">-Path</span><span class="sxs-lookup"><span data-stu-id="4e9b0-206">-Path</span></span>

<span data-ttu-id="4e9b0-207">變更指定項目的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-207">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="4e9b0-208">輸入項目的路徑，例如檔案或登錄機碼的路徑。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-208">Enter the path to an item, such as a path to a file or registry key.</span></span> <span data-ttu-id="4e9b0-209">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-209">Wildcards are permitted.</span></span>

<span data-ttu-id="4e9b0-210">如果您 `Set-Acl` 使用 **AclObject** 或 **SecurityDescriptor** 參數將安全性物件傳遞給 (，或將安全性物件從 Get-Acl 傳遞至 `Set-Acl`) ，而您省略 **路徑** 參數 (名稱和值) ，則 `Set-Acl` 會使用安全性物件中包含的路徑。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-210">If you pass a security object to `Set-Acl` (either by using the **AclObject** or **SecurityDescriptor** parameters or by passing a security object from Get-Acl to `Set-Acl`), and you omit the **Path** parameter (name and value), `Set-Acl` uses the path that is included in the security object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4e9b0-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e9b0-211">-Confirm</span></span>

<span data-ttu-id="4e9b0-212">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-212">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e9b0-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e9b0-213">-WhatIf</span></span>

<span data-ttu-id="4e9b0-214">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-214">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4e9b0-215">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-215">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e9b0-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e9b0-216">CommonParameters</span></span>

<span data-ttu-id="4e9b0-217">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e9b0-218">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e9b0-219">輸入</span><span class="sxs-lookup"><span data-stu-id="4e9b0-219">INPUTS</span></span>

### <span data-ttu-id="4e9b0-220">AccessControl. ObjectSecurity，AccessControl.. CommonSecurityDescriptor</span><span class="sxs-lookup"><span data-stu-id="4e9b0-220">System.Security.AccessControl.ObjectSecurity, System.Security.AccessControl.CommonSecurityDescriptor</span></span>

<span data-ttu-id="4e9b0-221">您可以使用管線將 ACL 物件或安全描述項傳送至 `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-221">You can pipe an ACL object or a security descriptor to `Set-Acl`.</span></span>

## <span data-ttu-id="4e9b0-222">輸出</span><span class="sxs-lookup"><span data-stu-id="4e9b0-222">OUTPUTS</span></span>

### <span data-ttu-id="4e9b0-223">AccessControl. System.security.accesscontrol.filesecurity</span><span class="sxs-lookup"><span data-stu-id="4e9b0-223">System.Security.AccessControl.FileSecurity</span></span>

<span data-ttu-id="4e9b0-224">依預設，不 `Set-Acl` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-224">By default, `Set-Acl` does not generate any output.</span></span>
<span data-ttu-id="4e9b0-225">不過，如果您使用 **Passthru** 參數，它會產生安全性物件。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-225">However, if you use the **Passthru** parameter, it generates a security object.</span></span>
<span data-ttu-id="4e9b0-226">安全性物件的類型需視項目的類型而定。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-226">The type of the security object depends on the type of the item.</span></span>

## <span data-ttu-id="4e9b0-227">注意</span><span class="sxs-lookup"><span data-stu-id="4e9b0-227">NOTES</span></span>

 <span data-ttu-id="4e9b0-228">`Set-Acl`PowerShell 檔案系統和登錄提供者支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-228">The `Set-Acl` cmdlet is supported by the PowerShell file system and registry providers.</span></span> <span data-ttu-id="4e9b0-229">這表示您可以用它來變更檔案、目錄和登錄機碼的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="4e9b0-229">As such, you can use it to change the security descriptors of files, directories, and registry keys.</span></span>

## <span data-ttu-id="4e9b0-230">相關連結</span><span class="sxs-lookup"><span data-stu-id="4e9b0-230">RELATED LINKS</span></span>

[<span data-ttu-id="4e9b0-231">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="4e9b0-231">Get-Acl</span></span>](Get-Acl.md)

[<span data-ttu-id="4e9b0-232">System.security.accesscontrol.filesystemaccessrule</span><span class="sxs-lookup"><span data-stu-id="4e9b0-232">FileSystemAccessRule</span></span>](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[<span data-ttu-id="4e9b0-233">ObjectSecurity. SetAccessRuleProtection</span><span class="sxs-lookup"><span data-stu-id="4e9b0-233">ObjectSecurity.SetAccessRuleProtection</span></span>](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[<span data-ttu-id="4e9b0-234">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="4e9b0-234">FileSystemRights</span></span>](/dotnet/api/system.security.accesscontrol.filesystemrights)
