---
ms.date: 03/22/2012
ms.topic: reference
title: 可更新的說明 CAB 檔案中允許的檔案類型
description: 可更新的說明 CAB 檔案中允許的檔案類型
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654745"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>可更新的說明 CAB 檔案中允許的檔案類型

未壓縮的 CAB 檔案內容預設限制為 1 GB。 若要略過此限制，使用者必須使用 Update-help **參數和** [get-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) [Cmdlet。](/powershell/module/Microsoft.PowerShell.Core/Save-Help)

為了確保從網際網路下載說明檔的安全性，可更新的說明封包檔只能包含以下所列的檔案類型。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 會針對說明主題架構驗證所有檔案。 如果 `Update-Help` Cmdlet 遇到無效或不是允許的類型的檔案，則不會安裝不正確檔案，也不會在使用者電腦上的 CAB 中停止安裝檔案。

- Cmdlet 的 XML 型說明主題。
- 腳本和函式的 XML 型說明主題。
- PowerShell 提供者的 XML 型說明主題。
- 以文字為基礎的說明主題，例如「關於」主題。

[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)會在解壓縮 cab 時驗證 cab 內容。 如果 `Update-Help` 在可更新的說明 CAB 檔案中找到不符合規範的檔案類型，它會產生終止錯誤並停止作業。 它不會從 CAB 安裝任何說明檔，即使是符合規範的檔案類型。
