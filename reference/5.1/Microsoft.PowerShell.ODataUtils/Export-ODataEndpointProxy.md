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
# Export-ODataEndpointProxy

## 概要
產生包含 Cmdlet 的模組，以管理 OData 端點。

## SYNTAX

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Export-ODataEndpointProxy` Cmdlet 會使用 OData 端點的中繼資料來產生包含 Cmdlet 的模組，您可以使用這些 Cmdlet 來管理該 OData 端點。 此模組是以 CDXML 為基礎。 在此 Cmdlet 產生模組之後，它會將該模組儲存至 **OutputModule** 參數所指定的路徑和檔案名。

`Export-ODataEndpointProxy` 產生用來建立、讀取、更新和刪除 (CRUD) 作業、非 CRUD 動作和關聯操作的 Cmdlet。

`Export-ODataEndpointProxy` 針對每個端點資源產生一個 CDXML 檔案。 您可以在產生模組之後編輯這些 CDXML 檔案。 例如，如果您想要變更 Cmdlet 的名詞或動詞名稱，使其符合 Windows PowerShell Cmdlet 命名方針，您可以修改檔案。

產生的模組中的每個 Cmdlet 都必須包含 **ConnectionURI** 參數，才能連接到模組所管理的端點。

## 範例

### 範例1：產生用來管理零售 web 服務端點的模組

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

此命令會產生模組來管理零售服務端點。 此命令會指定端點的 URI 和端點中繼資料的 URI。 此命令也會提供輸出路徑和腳本模組名稱作為 **OutputModule** 參數的值。 針對 **ResourceNameMapping** 參數的值，此命令會提供雜湊表，以將資源集合名稱對應至 Cmdlet 集合所需的名詞。 在此範例中，產品是資源集合名稱，而 **商品** 是名詞。 若要允許與非 SSL 網站的連線，HTTP，而不是 HTTPS，請新增 **AllowUnsecureConnection** 參數。

## PARAMETERS

### -AllowClobber

指出此 Cmdlet 會取代現有的模組。

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

### -AllowUnsecureConnection

指出此模組可以連接至不受 SSL 保護的 Uri。 除了 HTTPS 網站之外，模組還可以管理 HTTP 網站。

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

### -CmdletAdapter

指定 Cmdlet 介面卡。 此參數可接受的值為： ODataAdapter 和 NetworkControllerAdapter。

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

### -CreateRequestMethod

指定要求方法。 此參數可接受的值包括： PUT、POST 和 PATCH。

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

### -Credential

指定可存取 OData 端點的使用者帳戶。 預設值為目前使用者。 如果遠端電腦執行 Windows Vista 或更新版本的 Windows 作業系統，此 Cmdlet 會提示您輸入認證。

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

### -CustomData

指定自訂資料的雜湊表。

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

### -Force

指出此 Cmdlet 會覆寫現有資料夾中相同名稱的現有已產生模組 `Modules` 。

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

### -Headers

指定 Web 要求的標頭。 輸入雜湊表或字典。

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

### -MetadataUri

指定端點之中繼資料的 URI。

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

### -OutputModule

指定此 Cmdlet 用來儲存所產生之 proxy 命令模組的路徑和模組名稱。

此 Cmdlet 會將二進位模組、模組資訊清單以及格式化檔案（如果適用的話）複製到指定的資料夾。 如果您只指定模組的名稱，則會將 `Export-ODataEndpointProxy` 模組儲存在 `$home\Documents\WindowsPowerShell\Modules` 資料夾中。 如果您指定路徑，Cmdlet 會在該路徑中建立模組資料夾。

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

### -ResourceNameMapping

指定包含對應的雜湊表，可讓您自訂產生的 Cmdlet。 在此雜湊表中，資源集合名稱是索引鍵。 所需的 Cmdlet 名詞是值。

例如，在雜湊表中 `@{Products = 'Merchandise'}` ， **Products** 是作為索引鍵的資源集合名稱。 **貨品** 是產生的 Cmdlet 名詞。 產生的 Cmdlet 名稱可能不會與 Windows PowerShell Cmdlet 命名指導方針一致。 您可以修改資源 CDXML 檔案，以在此 Cmdlet 建立模組之後變更 Cmdlet 名稱。 如需詳細資訊，請參閱 [強烈建議的開發指導方針](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines)。

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

### -UpdateRequestMethod

指定更新要求方法。 此參數可接受的值包括： PUT、POST 和 PATCH。

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

### -Uri

指定端點的 URI。

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

### -Confirm

在執行 Cmdlet 前提示您確認。

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

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[OData 程式庫](https://technet.microsoft.com/windowsserver/hh525392(v=vs.85).aspx?f=255&MSPPError=-2147217396)

[什麼是 OData 通訊協定？](https://www.odata.org/)

[Invoke-RestMethod](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
