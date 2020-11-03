---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204024"
---
# <span data-ttu-id="3c919-103">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="3c919-103">Get-ControlPanelItem</span></span>

## <span data-ttu-id="3c919-104">概要</span><span class="sxs-lookup"><span data-stu-id="3c919-104">SYNOPSIS</span></span>
<span data-ttu-id="3c919-105">取得控制台項目。</span><span class="sxs-lookup"><span data-stu-id="3c919-105">Gets control panel items.</span></span>

## <span data-ttu-id="3c919-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c919-106">SYNTAX</span></span>

### <span data-ttu-id="3c919-107">RegularName (預設值)</span><span class="sxs-lookup"><span data-stu-id="3c919-107">RegularName (Default)</span></span>

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3c919-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="3c919-108">CanonicalName</span></span>

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="3c919-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3c919-109">DESCRIPTION</span></span>

<span data-ttu-id="3c919-110">`Get-ControlPanelItem`Cmdlet 會取得本機電腦上的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-110">The `Get-ControlPanelItem` cmdlet gets control panel items on the local computer.</span></span> <span data-ttu-id="3c919-111">您可以用它來依據名稱、類別或描述來尋找控制台項目，即使在沒有使用者介面的系統上也可以。</span><span class="sxs-lookup"><span data-stu-id="3c919-111">You can use it to find control panel items by name, category, or description, even on systems that do not have a user interface.</span></span>

<span data-ttu-id="3c919-112">此 Cmdlet 只會取得可在系統上開啟的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-112">This cmdlet gets only the control panel items that can be opened on the system.</span></span> <span data-ttu-id="3c919-113">在沒有主控台或檔案總管的電腦上，此 Cmdlet 只會取得可在沒有這些元件的情況下開啟的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-113">On computers that do not have Control Panel or File Explorer, this cmdlet gets only control panel items that can open without these components.</span></span>

<span data-ttu-id="3c919-114">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3c919-114">This cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="3c919-115">它只適用于 Windows 8 和 Windows Server 2012 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3c919-115">It works only on Windows 8 and Windows Server 2012 and newer.</span></span>

## <span data-ttu-id="3c919-116">範例</span><span class="sxs-lookup"><span data-stu-id="3c919-116">EXAMPLES</span></span>

### <span data-ttu-id="3c919-117">範例 1：取得所有控制台項目</span><span class="sxs-lookup"><span data-stu-id="3c919-117">Example 1: Get all control panel items</span></span>

<span data-ttu-id="3c919-118">此命令會取得本機電腦上的所有控制台項目。</span><span class="sxs-lookup"><span data-stu-id="3c919-118">This command gets all control panel items on the local computer.</span></span>

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### <span data-ttu-id="3c919-119">範例 2：依名稱取得控制台項目</span><span class="sxs-lookup"><span data-stu-id="3c919-119">Example 2: Get control panel items by name</span></span>

<span data-ttu-id="3c919-120">此範例會取得名稱中有程式或應用程式的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-120">This example gets control panel items that have Program or App in their names.</span></span>

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### <span data-ttu-id="3c919-121">範例 3：依類別取得控制台項目</span><span class="sxs-lookup"><span data-stu-id="3c919-121">Example 3: Get control panel items by category</span></span>

<span data-ttu-id="3c919-122">此命令會取得名稱中具有安全性之類別目錄中的所有控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-122">This command gets all control panel items in categories that have Security in their names.</span></span>

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### <span data-ttu-id="3c919-123">範例 4：開啟控制台項目</span><span class="sxs-lookup"><span data-stu-id="3c919-123">Example 4: Open a control panel item</span></span>

<span data-ttu-id="3c919-124">此範例會開啟本機電腦上的 Windows 防火牆控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-124">This example opens the Windows Firewall control panel item on the local computer.</span></span>

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="3c919-125">`Get-ControlPanelItem`Cmdlet 會取得 [控制台] 專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-125">The `Get-ControlPanelItem` cmdlet gets the control panel item.</span></span> <span data-ttu-id="3c919-126">`Show-ControlPanelItem`Cmdlet 會將其開啟。</span><span class="sxs-lookup"><span data-stu-id="3c919-126">The `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="3c919-127">範例 5：取得遠端電腦上的控制台項目</span><span class="sxs-lookup"><span data-stu-id="3c919-127">Example 5: Get control panel items on a remote computer</span></span>

<span data-ttu-id="3c919-128">此範例會取得 Server01 遠端電腦上的 BitLocker 磁碟機加密控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-128">This example gets the BitLocker Drive Encryption control panel item on the Server01 remote computer.</span></span>
<span data-ttu-id="3c919-129">`Invoke-Command`Cmdlet 會 `Get-ControlPanelItem` 從遠端執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c919-129">The `Invoke-Command` cmdlet runs the `Get-ControlPanelItem` cmdlet remotely.</span></span>

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### <span data-ttu-id="3c919-130">範例 6：搜尋控制台項目的描述</span><span class="sxs-lookup"><span data-stu-id="3c919-130">Example 6: Search the descriptions of control panel items</span></span>

<span data-ttu-id="3c919-131">此範例會搜尋控制台專案的 **Description** 屬性，只取得包含名稱 **裝置** 的專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-131">This example searches the **Description** property of the control panel items to get only those that contain the name **Device** .</span></span>

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

<span data-ttu-id="3c919-132">`Get-ControlPanelItem`Cmdlet 會取得所有的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-132">The `Get-ControlPanelItem` cmdlet gets all control panel items.</span></span> <span data-ttu-id="3c919-133">此 `Where-Object` Cmdlet 會依 **Description** 屬性的值篩選項目。</span><span class="sxs-lookup"><span data-stu-id="3c919-133">The `Where-Object` cmdlet filters the items by the value of the **Description** property.</span></span>

## <span data-ttu-id="3c919-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c919-134">PARAMETERS</span></span>

### <span data-ttu-id="3c919-135">-CanonicalName</span><span class="sxs-lookup"><span data-stu-id="3c919-135">-CanonicalName</span></span>

<span data-ttu-id="3c919-136">依此 Cmdlet 取得的標準名稱或名稱模式，以字串陣列的形式指定控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-136">Specifies, as a string array, the control panel items by their canonical names or name patterns that this cmdlet gets.</span></span> <span data-ttu-id="3c919-137">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3c919-137">Wildcards are permitted.</span></span> <span data-ttu-id="3c919-138">如果您輸入多個名稱，此 Cmdlet 會取得符合任何名稱的控制台專案，如同名稱清單中的專案是以 "or" 運算子分隔。</span><span class="sxs-lookup"><span data-stu-id="3c919-138">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span>

<span data-ttu-id="3c919-139">根據預設，此 Cmdlet 會取得系統中的所有控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-139">By default, this cmdlet gets all control panel items in the system.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3c919-140">-Category</span><span class="sxs-lookup"><span data-stu-id="3c919-140">-Category</span></span>

<span data-ttu-id="3c919-141">以字串陣列指定此 Cmdlet 取得之指定類別中的 [控制台] 專案類別。</span><span class="sxs-lookup"><span data-stu-id="3c919-141">Specifies, as a string array, the categories of the control panel items in the specified categories that this cmdlet gets.</span></span> <span data-ttu-id="3c919-142">輸入類別名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="3c919-142">Enter a category name or name pattern.</span></span> <span data-ttu-id="3c919-143">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3c919-143">Wildcards are permitted.</span></span> <span data-ttu-id="3c919-144">如果您輸入多個名稱，此 Cmdlet 會取得符合任何名稱的控制台專案，如同名稱清單中的專案是以 "or" 運算子分隔。</span><span class="sxs-lookup"><span data-stu-id="3c919-144">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span> <span data-ttu-id="3c919-145">根據預設，此 Cmdlet 會取得系統中的所有控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-145">By default, this cmdlet gets all control panel items in the system.</span></span>

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

### <span data-ttu-id="3c919-146">-Name</span><span class="sxs-lookup"><span data-stu-id="3c919-146">-Name</span></span>

<span data-ttu-id="3c919-147">以字串陣列指定此 Cmdlet 取得之控制台的名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="3c919-147">Specifies, as a string array, the names or name patterns of the control panel that this cmdlet gets.</span></span>
<span data-ttu-id="3c919-148">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3c919-148">Wildcards are permitted.</span></span> <span data-ttu-id="3c919-149">您也可以使用管線將名稱或名稱模式傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c919-149">You can also pipe a name or name pattern to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3c919-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c919-150">CommonParameters</span></span>

<span data-ttu-id="3c919-151">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3c919-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c919-152">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3c919-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c919-153">輸入</span><span class="sxs-lookup"><span data-stu-id="3c919-153">INPUTS</span></span>

### <span data-ttu-id="3c919-154">System.String</span><span class="sxs-lookup"><span data-stu-id="3c919-154">System.String</span></span>

<span data-ttu-id="3c919-155">您可以使用管線將名稱或名稱模式傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c919-155">You can pipe a name or name pattern to this cmdlet.</span></span>

## <span data-ttu-id="3c919-156">輸出</span><span class="sxs-lookup"><span data-stu-id="3c919-156">OUTPUTS</span></span>

### <span data-ttu-id="3c919-157">Microsoft.PowerShell.Commands.ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="3c919-157">Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="3c919-158">此 Cmdlet 會取得本機電腦上的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="3c919-158">This cmdlet gets control panel items on the local computer.</span></span>

## <span data-ttu-id="3c919-159">注意</span><span class="sxs-lookup"><span data-stu-id="3c919-159">NOTES</span></span>

## <span data-ttu-id="3c919-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="3c919-160">RELATED LINKS</span></span>

[<span data-ttu-id="3c919-161">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="3c919-161">Show-ControlPanelItem</span></span>](Show-ControlPanelItem.md)
