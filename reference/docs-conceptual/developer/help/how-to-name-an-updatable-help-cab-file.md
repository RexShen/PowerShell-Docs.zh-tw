---
ms.date: 09/12/2016
ms.topic: reference
title: 如何為可更新說明 CAB 檔案命名
description: 如何為可更新說明 CAB 檔案命名
ms.openlocfilehash: 57ea188d07a382d1a986a49c9ae22c5919dafa8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658912"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>如何為可更新說明 CAB 檔案命名

本主題說明可更新的說明封包 () 檔案的必要名稱格式 `.CAB` 。

## <a name="how-to-name-an-updatable-help-cab-file"></a>如何為可更新說明 CAB 檔案命名

可更新的封包 (`.CAB`) 檔必須具有下列格式的名稱。

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

名稱的元素如下所示。

- `<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 傳回之 **ModuleInfo** 物件的 **Name** 屬性值。
- `<ModuleGUID>` -模組資訊清單中 **GUID** 索引鍵的值。
- `<UICulture>` -CAB 檔案中說明檔的 UI 文化特性。 此值必須符合模組之 HelpInfo XML 檔案中其中一個 **UICulture** 元素的值。

例如，如果模組名稱為 "TestModule"，則模組 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，而 UI 文化特性為 "en-us"，CAB 檔案的名稱會是：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
