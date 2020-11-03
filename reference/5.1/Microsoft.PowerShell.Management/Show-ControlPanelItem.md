---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203488"
---
# <span data-ttu-id="f7ec9-103">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="f7ec9-103">Show-ControlPanelItem</span></span>

## <span data-ttu-id="f7ec9-104">概要</span><span class="sxs-lookup"><span data-stu-id="f7ec9-104">SYNOPSIS</span></span>
<span data-ttu-id="f7ec9-105">開啟控制台項目。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-105">Opens control panel items.</span></span>

## <span data-ttu-id="f7ec9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7ec9-106">SYNTAX</span></span>

### <span data-ttu-id="f7ec9-107">RegularName (預設值)</span><span class="sxs-lookup"><span data-stu-id="f7ec9-107">RegularName (Default)</span></span>

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f7ec9-108">CanonicalName</span><span class="sxs-lookup"><span data-stu-id="f7ec9-108">CanonicalName</span></span>

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f7ec9-109">ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="f7ec9-109">ControlPanelItem</span></span>

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## <span data-ttu-id="f7ec9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f7ec9-110">DESCRIPTION</span></span>

<span data-ttu-id="f7ec9-111">`Show-ControlPanelItem`Cmdlet 會開啟本機電腦上的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-111">The `Show-ControlPanelItem` cmdlet opens control panel items on the local computer.</span></span> <span data-ttu-id="f7ec9-112">您可以使用它來依名稱、類別或描述來開啟控制台專案，即使在沒有使用者介面的系統上也一樣。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-112">You can use it to open control panel items by name, category, or description, even on systems that do not have a user interface.</span></span> <span data-ttu-id="f7ec9-113">您可以透過管線將控制台專案從 `Get-ControlPanelItem` Cmdlet 傳送至 `Show-ControlPanelItem` 。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-113">You can pipe control panel items from the `Get-ControlPanelItem` cmdlet to `Show-ControlPanelItem`.</span></span>

<span data-ttu-id="f7ec9-114">`Show-ControlPanelItem` 只會搜尋可在系統上開啟的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-114">`Show-ControlPanelItem` searches only control panel items that can be opened on the system.</span></span> <span data-ttu-id="f7ec9-115">在沒有 **主控台** 或 **檔案總管** 的電腦上， `Show-ControlPanelItem` 只會搜尋可在沒有這些元件的情況下開啟的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-115">On computers that do not have **Control Panel** or **File Explorer** , `Show-ControlPanelItem` searches only control panel items that can open without these components.</span></span>

<span data-ttu-id="f7ec9-116">此 Cmdlet 是在 Windows PowerShell 3.0 中引進，並可在 Windows 8、Windows Server 2012 和更新版本上運作。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-116">This cmdlet was introduced in Windows PowerShell 3.0 and works on Windows 8, Windows Server 2012, and higher versions.</span></span>

## <span data-ttu-id="f7ec9-117">範例</span><span class="sxs-lookup"><span data-stu-id="f7ec9-117">EXAMPLES</span></span>

### <span data-ttu-id="f7ec9-118">範例1：顯示控制台專案</span><span class="sxs-lookup"><span data-stu-id="f7ec9-118">Example 1: Show a control panel item</span></span>

<span data-ttu-id="f7ec9-119">此範例會啟動 [ **自動播放** ] 控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-119">This example launches the **AutoPlay** control panel item.</span></span>

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### <span data-ttu-id="f7ec9-120">範例2：使用管線將控制台專案輸送至此 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f7ec9-120">Example 2: Pipe a control panel item to this cmdlet</span></span>

<span data-ttu-id="f7ec9-121">此範例會在本機電腦上開啟 **Windows Defender 防火牆** 控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-121">This example opens the **Windows Defender Firewall** control panel item on the local computer.</span></span>
<span data-ttu-id="f7ec9-122">Windows 防火牆控制台專案的名稱已在 Windows 版本中變更。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-122">The name of the Windows Firewall control panel item has changed over the versions of Windows.</span></span> <span data-ttu-id="f7ec9-123">這個範例會使用萬用字元模式來尋找 [控制台] 專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-123">This example uses a wildcard pattern to find the control panel item.</span></span>

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="f7ec9-124">`Get-ControlPanelItem` 取得 [控制台] 專案，而 `Show-ControlPanelItem` Cmdlet 會開啟該專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-124">`Get-ControlPanelItem` gets the control panel item and the `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="f7ec9-125">範例 3：使用檔案名稱來開啟控制台項目</span><span class="sxs-lookup"><span data-stu-id="f7ec9-125">Example 3: Use a file name to open a control panel item</span></span>

<span data-ttu-id="f7ec9-126">此範例會使用應用程式名稱來開啟 [ **程式和功能** ] 控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-126">This example opens the **Programs and Features** control panel item by using its application name.</span></span>

```powershell
appwiz.cpl
```

<span data-ttu-id="f7ec9-127">這個方法是使用命令的替代方法 `Show-ControlPanelItem` 。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-127">This method is an alternative to using a `Show-ControlPanelItem` command.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ec9-128">在 PowerShell 中，您可以省略控制台檔案的 cpl 副檔名，因為它包含在環境變數的值中 `$env:PathExt` 。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-128">In PowerShell, you can omit the .cpl file extension for control panel files because it's included in the value of the `$env:PathExt` environment variable.</span></span>

## <span data-ttu-id="f7ec9-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7ec9-129">PARAMETERS</span></span>

### <span data-ttu-id="f7ec9-130">-CanonicalName</span><span class="sxs-lookup"><span data-stu-id="f7ec9-130">-CanonicalName</span></span>

<span data-ttu-id="f7ec9-131">使用指定的正式名稱或名稱模式來指定 [控制台] 專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-131">Specifies control panel items by using the specified canonical names or name patterns.</span></span> <span data-ttu-id="f7ec9-132">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-132">Wildcard characters are permitted.</span></span> <span data-ttu-id="f7ec9-133">如果您輸入多個名稱，此 Cmdlet 會開啟符合任何名稱的 [控制台] 專案，如同 [名稱] 清單中的專案是以 **OR** 運算子分隔。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-133">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

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

### <span data-ttu-id="f7ec9-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f7ec9-134">-InputObject</span></span>

<span data-ttu-id="f7ec9-135">藉由提交 [控制台專案] 物件，指定要開啟的控制台專案。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-135">Specifies control panel items to open by submitting control panel item objects.</span></span> <span data-ttu-id="f7ec9-136">輸入包含控制台專案物件的變數，或輸入可取得控制台專案物件的命令或運算式，例如 `Get-ControlPanelItem` 。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-136">Enter a variable that contains control panel item objects, or type a command or expression that gets control panel item objects, such as `Get-ControlPanelItem`.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f7ec9-137">-Name</span><span class="sxs-lookup"><span data-stu-id="f7ec9-137">-Name</span></span>

<span data-ttu-id="f7ec9-138">指定控制台專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-138">Specifies names of control panel items.</span></span> <span data-ttu-id="f7ec9-139">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="f7ec9-140">如果您輸入多個名稱，此 Cmdlet 會開啟符合任何名稱的 [控制台] 專案，如同 [名稱] 清單中的專案是以 **OR** 運算子分隔。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-140">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f7ec9-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7ec9-141">CommonParameters</span></span>

<span data-ttu-id="f7ec9-142">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7ec9-143">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7ec9-144">輸入</span><span class="sxs-lookup"><span data-stu-id="f7ec9-144">INPUTS</span></span>

### <span data-ttu-id="f7ec9-145">System.string、傳送至 get-controlpanelitem、。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-145">System.String, Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="f7ec9-146">您可以使用管線將名稱或控制台專案物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-146">You can pipe a name or control panel item object to this cmdlet.</span></span>

## <span data-ttu-id="f7ec9-147">輸出</span><span class="sxs-lookup"><span data-stu-id="f7ec9-147">OUTPUTS</span></span>

### <span data-ttu-id="f7ec9-148">無</span><span class="sxs-lookup"><span data-stu-id="f7ec9-148">None</span></span>

<span data-ttu-id="f7ec9-149">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f7ec9-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f7ec9-150">注意</span><span class="sxs-lookup"><span data-stu-id="f7ec9-150">NOTES</span></span>

## <span data-ttu-id="f7ec9-151">相關連結</span><span class="sxs-lookup"><span data-stu-id="f7ec9-151">RELATED LINKS</span></span>

[<span data-ttu-id="f7ec9-152">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="f7ec9-152">Get-ControlPanelItem</span></span>](Get-ControlPanelItem.md)
