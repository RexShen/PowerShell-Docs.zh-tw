---
title: 可更新的說明 CAB 檔案中允許的檔案類型 |Microsoft Docs
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
ms.openlocfilehash: 6e9e51a50226430465726d27874e02e98ee67672
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811537"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>可更新的說明 CAB 檔案中允許的檔案類型

本主題列出並描述可更新的說明 CAB 檔案的內容需求。

## <a name="updatable-help-cab-file-requirements"></a>可更新的說明 CAB 檔案需求

未壓縮的 CAB 檔案內容預設限制為 1 GB。 若要略過這項限制，使用者必須使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 的**Force**參數。

若要確保從網際網路下載之說明檔的安全性，可更新的說明 CAB 檔案只能包含以下所列的檔案類型。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 會根據說明主題架構來驗證所有檔案。 如果 `Update-Help` Cmdlet 遇到無效或不是允許類型的檔案，則不會安裝不正確檔案，而且會在使用者的電腦上停止從 CAB 安裝檔案。

- Cmdlet 的 XML 為基礎說明主題。

- 腳本和函式的 XML 為基礎的說明主題。

- Windows PowerShell 提供者的 XML 型說明主題。

- 以文字為基礎的說明主題，例如關於主題。

當解壓縮 CAB 時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)會驗證 cab 內容。 如果 `Update-Help` 在可更新的說明 CAB 檔案中找到不符合規範的檔案類型，它會產生終止錯誤，並停止作業。 它不會從 CAB 安裝任何說明檔，即使是符合規範的檔案類型也一樣。
