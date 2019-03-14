---
title: 允許可更新的檔案類型有助於封包檔 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794241"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>可更新的說明 CAB 檔案中允許的檔案類型

本主題列出並描述可更新說明的 CAB 檔案內容的需求。

## <a name="updatable-help-cab-file-requirements"></a>可更新的說明封包檔的需求

未壓縮的封包檔案內容是預設限制為 1 GB。 若要略過此限制，使用者必須使用**Force**的參數[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。

若要確保從網際網路下載說明檔的安全性，可更新說明的 CAB 檔案可以包含僅下面所列的檔案類型。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)指令程式會驗證所有的檔案，針對 [說明] 主題的結構描述。 如果`Update-Help`cmdlet 發生檔案無效或不允許的型別，它不會安裝無效的檔案，並停止使用者的電腦上封包從安裝檔案。

- 以 XML 為基礎之 cmdlet 說明主題。

- 以 XML 為基礎的說明主題的指令碼和函式。

- Windows PowerShell 提供者以 XML 為基礎說明主題。

- 以文字為基礎的主題，例如說明主題。

[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)驗證封包內容，當它解壓縮封包檔。 如果`Update-Help`發現不相容的檔案類型的可更新說明的 CAB 檔案中，它會產生終止錯誤並停止作業。 它不會安裝任何說明檔從封包，甚至是那些相容的檔案類型。