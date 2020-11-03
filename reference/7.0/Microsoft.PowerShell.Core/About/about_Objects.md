---
description: 提供 PowerShell 中物件的基本資訊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: b845dc8b55a19bb642c194398b0c9f5f13d24cb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208119"
---
# <a name="about-objects"></a>關於物件

## <a name="short-description"></a>簡短描述
提供 PowerShell 中物件的基本資訊。

## <a name="long-description"></a>完整描述

您在 PowerShell 中採取的每個動作都是在物件的內容中進行。 當資料從某個命令移至下一個命令時，會移動為一或多個可識別的物件。 物件，則是代表專案的資料集合。 物件是由三種類型的資料所組成：物件類型、其方法和屬性。

## <a name="types-methods-and-properties"></a>類型、方法和屬性

物件類型會告訴它是哪種類型的物件。 例如，代表檔案的物件是 FileInfo 物件。

物件方法是您可以在物件上執行的動作。
例如，FileInfo 物件具有可供您用來複製檔案的 CopyTo 方法。

物件屬性會儲存物件的相關資訊。 例如，FileInfo 物件具有 LastWriteTime 屬性，可儲存最近存取檔案的日期和時間。

使用物件時，您可以在命令中使用其方法和屬性，以採取動作和管理資料。

## <a name="objects-in-pipelines"></a>管線中的物件

當命令在管線中合併時，它們會將資訊以物件的形式傳遞給彼此。 當第一個命令執行時，它會將一個或多個物件向下傳送至第二個命令。 第二個命令會從第一個命令接收物件、處理物件，然後將新的或修改過的物件傳遞至管線中的下一個命令。
這會繼續執行，直到管線中的所有命令都執行為止。

下列範例示範如何從一個命令傳遞物件到下一個命令：

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

第一個命令會 `Get-ChildItem C:` 針對檔案系統根目錄中的每個專案傳回檔案或目錄物件。 檔案和目錄物件會沿著管線向下傳遞至第二個命令。

第二個命令 `where { $_.PsIsContainer -eq $false }` 會使用所有檔案系統物件的 PsIsContainer 屬性，只選取檔案，其 PsIsContainer 屬性中的值為 false (\$ false) 。 在 PsIsContainer 屬性中，資料夾（容器和）的值為 True (\$ true) ，則不會選取。

第二個命令只會將檔案物件傳遞至第三個命令 `Format-List` ，這會在清單中顯示檔案物件。

## <a name="see-also"></a>另請參閱

[about_Methods](about_Methods.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)
