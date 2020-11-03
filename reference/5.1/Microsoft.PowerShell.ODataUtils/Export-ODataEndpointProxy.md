---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 7550e2df319e5f195e65609ae29ebb00830ec8d2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203432"
---
# <span data-ttu-id="be3b4-103">Export-ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="be3b4-103">Export-ODataEndpointProxy</span></span>

## <span data-ttu-id="be3b4-104">概要</span><span class="sxs-lookup"><span data-stu-id="be3b4-104">SYNOPSIS</span></span>
<span data-ttu-id="be3b4-105">產生包含 Cmdlet 的模組，以管理 OData 端點。</span><span class="sxs-lookup"><span data-stu-id="be3b4-105">Generates a module that contains cmdlets to manage an OData endpoint.</span></span>

## <span data-ttu-id="be3b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="be3b4-106">SYNTAX</span></span>

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="be3b4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="be3b4-107">DESCRIPTION</span></span>

<span data-ttu-id="be3b4-108">此 `Export-ODataEndpointProxy` Cmdlet 會使用 OData 端點的中繼資料來產生包含 Cmdlet 的模組，您可以使用這些 Cmdlet 來管理該 OData 端點。</span><span class="sxs-lookup"><span data-stu-id="be3b4-108">The `Export-ODataEndpointProxy` cmdlet uses the metadata of an OData endpoint to generate a module that contains cmdlets you can use to manage that OData endpoint.</span></span> <span data-ttu-id="be3b4-109">此模組是以 CDXML 為基礎。</span><span class="sxs-lookup"><span data-stu-id="be3b4-109">The module is based on CDXML.</span></span> <span data-ttu-id="be3b4-110">在此 Cmdlet 產生模組之後，它會將該模組儲存至 **OutputModule** 參數所指定的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="be3b4-110">After this cmdlet generates the module, it saves that module to the path and file name specified by the **OutputModule** parameter.</span></span>

<span data-ttu-id="be3b4-111">`Export-ODataEndpointProxy` 產生用來建立、讀取、更新和刪除 (CRUD) 作業、非 CRUD 動作和關聯操作的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="be3b4-111">`Export-ODataEndpointProxy` generates cmdlets for create, read, update, and delete (CRUD) operations, non-CRUD actions, and association manipulation.</span></span>

<span data-ttu-id="be3b4-112">`Export-ODataEndpointProxy` 針對每個端點資源產生一個 CDXML 檔案。</span><span class="sxs-lookup"><span data-stu-id="be3b4-112">`Export-ODataEndpointProxy` generates one CDXML file per endpoint resource.</span></span> <span data-ttu-id="be3b4-113">您可以在產生模組之後編輯這些 CDXML 檔案。</span><span class="sxs-lookup"><span data-stu-id="be3b4-113">You can edit these CDXML files after the module is generated.</span></span> <span data-ttu-id="be3b4-114">例如，如果您想要變更 Cmdlet 的名詞或動詞名稱，使其符合 Windows PowerShell Cmdlet 命名方針，您可以修改檔案。</span><span class="sxs-lookup"><span data-stu-id="be3b4-114">For example, if you want to change the noun or verb names of the cmdlets to align with Windows PowerShell cmdlet naming guidelines, you can modify the file.</span></span>

<span data-ttu-id="be3b4-115">產生的模組中的每個 Cmdlet 都必須包含 **ConnectionURI** 參數，才能連接到模組所管理的端點。</span><span class="sxs-lookup"><span data-stu-id="be3b4-115">Every cmdlet in a generated module must include a **ConnectionURI** parameter in order to connect to the endpoint that the module manages.</span></span>

## <span data-ttu-id="be3b4-116">範例</span><span class="sxs-lookup"><span data-stu-id="be3b4-116">EXAMPLES</span></span>

### <span data-ttu-id="be3b4-117">範例1：產生用來管理零售 web 服務端點的模組</span><span class="sxs-lookup"><span data-stu-id="be3b4-117">Example 1: Generate a module to manage a retail web service endpoint</span></span>

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

<span data-ttu-id="be3b4-118">此命令會產生模組來管理零售服務端點。</span><span class="sxs-lookup"><span data-stu-id="be3b4-118">This command generates a module to manage a retail service endpoint.</span></span> <span data-ttu-id="be3b4-119">此命令會指定端點的 URI 和端點中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="be3b4-119">The command specifies the URI of the endpoint and the URI of the endpoint metadata.</span></span> <span data-ttu-id="be3b4-120">此命令也會提供輸出路徑和腳本模組名稱作為 **OutputModule** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="be3b4-120">The command also provides an output path and script module name as the value of the **OutputModule** parameter.</span></span> <span data-ttu-id="be3b4-121">針對 **ResourceNameMapping** 參數的值，此命令會提供雜湊表，以將資源集合名稱對應至 Cmdlet 集合所需的名詞。</span><span class="sxs-lookup"><span data-stu-id="be3b4-121">For the value of the **ResourceNameMapping** parameter, the command provides a hashtable that maps the resource collection name to the desired noun for the cmdlet set.</span></span> <span data-ttu-id="be3b4-122">在此範例中，產品是資源集合名稱，而 **商品** 是名詞。</span><span class="sxs-lookup"><span data-stu-id="be3b4-122">In this example, Products is the resource collection name and **Merchandise** is the noun.</span></span> <span data-ttu-id="be3b4-123">若要允許與非 SSL 網站的連線，HTTP，而不是 HTTPS，請新增 **AllowUnsecureConnection** 參數。</span><span class="sxs-lookup"><span data-stu-id="be3b4-123">To allow connections to non-SSL sites, HTTP, as opposed to HTTPS, add the **AllowUnsecureConnection** parameter.</span></span>

## <span data-ttu-id="be3b4-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="be3b4-124">PARAMETERS</span></span>

### <span data-ttu-id="be3b4-125">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="be3b4-125">-AllowClobber</span></span>

<span data-ttu-id="be3b4-126">指出此 Cmdlet 會取代現有的模組。</span><span class="sxs-lookup"><span data-stu-id="be3b4-126">Indicates that this cmdlet replaces an existing module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-127">-AllowUnsecureConnection</span><span class="sxs-lookup"><span data-stu-id="be3b4-127">-AllowUnsecureConnection</span></span>

<span data-ttu-id="be3b4-128">指出此模組可以連接至不受 SSL 保護的 Uri。</span><span class="sxs-lookup"><span data-stu-id="be3b4-128">Indicates that this module can connect to URIs that are not SSL-secured.</span></span> <span data-ttu-id="be3b4-129">除了 HTTPS 網站之外，模組還可以管理 HTTP 網站。</span><span class="sxs-lookup"><span data-stu-id="be3b4-129">The module can manage HTTP sites in addition to HTTPS sites.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-130">-CmdletAdapter</span><span class="sxs-lookup"><span data-stu-id="be3b4-130">-CmdletAdapter</span></span>

<span data-ttu-id="be3b4-131">指定 Cmdlet 介面卡。</span><span class="sxs-lookup"><span data-stu-id="be3b4-131">Specifies the cmdlet adapter.</span></span> <span data-ttu-id="be3b4-132">此參數可接受的值為： ODataAdapter 和 NetworkControllerAdapter。</span><span class="sxs-lookup"><span data-stu-id="be3b4-132">The acceptable values for this parameter are: ODataAdapter and NetworkControllerAdapter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-133">-CreateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="be3b4-133">-CreateRequestMethod</span></span>

<span data-ttu-id="be3b4-134">指定要求方法。</span><span class="sxs-lookup"><span data-stu-id="be3b4-134">Specifies the request method.</span></span> <span data-ttu-id="be3b4-135">此參數可接受的值包括： PUT、POST 和 PATCH。</span><span class="sxs-lookup"><span data-stu-id="be3b4-135">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="be3b4-136">-Credential</span></span>

<span data-ttu-id="be3b4-137">指定可存取 OData 端點的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="be3b4-137">Specifies a user account that has access to the OData endpoint.</span></span> <span data-ttu-id="be3b4-138">預設值為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="be3b4-138">The default value is the current user.</span></span> <span data-ttu-id="be3b4-139">如果遠端電腦執行 Windows Vista 或更新版本的 Windows 作業系統，此 Cmdlet 會提示您輸入認證。</span><span class="sxs-lookup"><span data-stu-id="be3b4-139">If a remote computer runs Windows Vista or a later release of the Windows operating system, the cmdlet prompts you for credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-140">-CustomData</span><span class="sxs-lookup"><span data-stu-id="be3b4-140">-CustomData</span></span>

<span data-ttu-id="be3b4-141">指定自訂資料的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="be3b4-141">Specifies a hash table of custom data.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-142">-Force</span><span class="sxs-lookup"><span data-stu-id="be3b4-142">-Force</span></span>

<span data-ttu-id="be3b4-143">指出此 Cmdlet 會覆寫現有資料夾中相同名稱的現有已產生模組 `Modules` 。</span><span class="sxs-lookup"><span data-stu-id="be3b4-143">Indicates that this cmdlet overwrites an existing generated module of the same name in an existing `Modules` folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-144">-Headers</span><span class="sxs-lookup"><span data-stu-id="be3b4-144">-Headers</span></span>

<span data-ttu-id="be3b4-145">指定 Web 要求的標頭。</span><span class="sxs-lookup"><span data-stu-id="be3b4-145">Specifies the headers of the web request.</span></span> <span data-ttu-id="be3b4-146">輸入雜湊表或字典。</span><span class="sxs-lookup"><span data-stu-id="be3b4-146">Enter a hash table or dictionary.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-147">-MetadataUri</span><span class="sxs-lookup"><span data-stu-id="be3b4-147">-MetadataUri</span></span>

<span data-ttu-id="be3b4-148">指定端點之中繼資料的 URI。</span><span class="sxs-lookup"><span data-stu-id="be3b4-148">Specifies the URI of the metadata of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-149">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="be3b4-149">-OutputModule</span></span>

<span data-ttu-id="be3b4-150">指定此 Cmdlet 用來儲存所產生之 proxy 命令模組的路徑和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="be3b4-150">Specifies the path and module name to which this cmdlet saves the generated module of proxy commands.</span></span>

<span data-ttu-id="be3b4-151">此 Cmdlet 會將二進位模組、模組資訊清單以及格式化檔案（如果適用的話）複製到指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="be3b4-151">This cmdlet copies a binary module, module manifest, and formatting file, if applicable, to the specified folder.</span></span> <span data-ttu-id="be3b4-152">如果您只指定模組的名稱，則會將 `Export-ODataEndpointProxy` 模組儲存在 `$home\Documents\WindowsPowerShell\Modules` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="be3b4-152">If you specify only the name of the module, `Export-ODataEndpointProxy` saves the module in the `$home\Documents\WindowsPowerShell\Modules` folder.</span></span> <span data-ttu-id="be3b4-153">如果您指定路徑，Cmdlet 會在該路徑中建立模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="be3b4-153">If you specify a path, the cmdlet creates the module folder in that path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-154">-ResourceNameMapping</span><span class="sxs-lookup"><span data-stu-id="be3b4-154">-ResourceNameMapping</span></span>

<span data-ttu-id="be3b4-155">指定包含對應的雜湊表，可讓您自訂產生的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="be3b4-155">Specifies a hashtable that contains mappings that let you customize the generated cmdlets.</span></span> <span data-ttu-id="be3b4-156">在此雜湊表中，資源集合名稱是索引鍵。</span><span class="sxs-lookup"><span data-stu-id="be3b4-156">In this hashtable, the resource collection name is the key.</span></span> <span data-ttu-id="be3b4-157">所需的 Cmdlet 名詞是值。</span><span class="sxs-lookup"><span data-stu-id="be3b4-157">The desired cmdlet noun is the value.</span></span>

<span data-ttu-id="be3b4-158">例如，在雜湊表中 `@{Products = 'Merchandise'}` ， **Products** 是作為索引鍵的資源集合名稱。</span><span class="sxs-lookup"><span data-stu-id="be3b4-158">For example, in the hash table `@{Products = 'Merchandise'}`, **Products** is the resource collection name that serves as the key.</span></span> <span data-ttu-id="be3b4-159">**貨品** 是產生的 Cmdlet 名詞。</span><span class="sxs-lookup"><span data-stu-id="be3b4-159">**Merchandise** is the resulting cmdlet noun.</span></span> <span data-ttu-id="be3b4-160">產生的 Cmdlet 名稱可能不會與 Windows PowerShell Cmdlet 命名指導方針一致。</span><span class="sxs-lookup"><span data-stu-id="be3b4-160">The generated cmdlet names might not align to Windows PowerShell cmdlet naming guidelines.</span></span> <span data-ttu-id="be3b4-161">您可以修改資源 CDXML 檔案，以在此 Cmdlet 建立模組之後變更 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="be3b4-161">You can modify the resource CDXML file to change the cmdlet names after this cmdlet creates the module.</span></span> <span data-ttu-id="be3b4-162">如需詳細資訊，請參閱 [強烈建議的開發指導方針](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines)。</span><span class="sxs-lookup"><span data-stu-id="be3b4-162">For more information, see [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-163">-UpdateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="be3b4-163">-UpdateRequestMethod</span></span>

<span data-ttu-id="be3b4-164">指定更新要求方法。</span><span class="sxs-lookup"><span data-stu-id="be3b4-164">Specifies the update request method.</span></span> <span data-ttu-id="be3b4-165">此參數可接受的值包括： PUT、POST 和 PATCH。</span><span class="sxs-lookup"><span data-stu-id="be3b4-165">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-166">-Uri</span><span class="sxs-lookup"><span data-stu-id="be3b4-166">-Uri</span></span>

<span data-ttu-id="be3b4-167">指定端點的 URI。</span><span class="sxs-lookup"><span data-stu-id="be3b4-167">Specifies the URI of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="be3b4-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="be3b4-168">-Confirm</span></span>

<span data-ttu-id="be3b4-169">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="be3b4-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="be3b4-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="be3b4-170">-WhatIf</span></span>

<span data-ttu-id="be3b4-171">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="be3b4-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="be3b4-172">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="be3b4-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="be3b4-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be3b4-173">CommonParameters</span></span>

<span data-ttu-id="be3b4-174">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="be3b4-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be3b4-175">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="be3b4-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be3b4-176">輸入</span><span class="sxs-lookup"><span data-stu-id="be3b4-176">INPUTS</span></span>

## <span data-ttu-id="be3b4-177">輸出</span><span class="sxs-lookup"><span data-stu-id="be3b4-177">OUTPUTS</span></span>

## <span data-ttu-id="be3b4-178">注意</span><span class="sxs-lookup"><span data-stu-id="be3b4-178">NOTES</span></span>

## <span data-ttu-id="be3b4-179">相關連結</span><span class="sxs-lookup"><span data-stu-id="be3b4-179">RELATED LINKS</span></span>

<span data-ttu-id="be3b4-180">[OData 程式庫](https://technet.microsoft.com/windowsserver/hh525392(v=vs.85).aspx?f=255&MSPPError=-2147217396)</span><span class="sxs-lookup"><span data-stu-id="be3b4-180">[OData Library](https://technet.microsoft.com/windowsserver/hh525392(v=vs.85).aspx?f=255&MSPPError=-2147217396)</span></span>

[<span data-ttu-id="be3b4-181">什麼是 OData 通訊協定？</span><span class="sxs-lookup"><span data-stu-id="be3b4-181">What is the OData Protocol?</span></span>](https://www.odata.org/)

[<span data-ttu-id="be3b4-182">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="be3b4-182">Invoke-RestMethod</span></span>](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
