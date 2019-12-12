---
title: 如何命名可更新的說明 CAB 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367157"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>如何為可更新說明 CAB 檔案命名

本主題說明可更新的說明封包（的必要名稱格式。CAB）檔案。

## <a name="how-to-name-an-updatable-help-cab-file"></a>如何為可更新說明 CAB 檔案命名

可更新的封包（。CAB）檔案的名稱必須是下列格式。

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

名稱的元素如下所示。

ModuleName **ModuleInfo**物件的**Name**屬性值，以[取得模組](/powershell/module/Microsoft.PowerShell.Core/Get-Module)Cmdlet 傳回。

ModuleGUID 模組資訊清單中**GUID**金鑰的值。

UICulture CAB 檔案中說明檔的 UI 文化特性。 這個值必須符合模組的 HelpInfo XML 檔案中其中一個**UICulture**元素的值。

例如，如果模組名稱是 "TestModule"，則模組 GUID 為 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，而 UI 文化特性為 "en-us"，則 CAB 檔案的名稱會是：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`