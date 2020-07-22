---
title: 如何為可更新說明 CAB 檔案命名
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892994"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>如何為可更新說明 CAB 檔案命名

本主題說明可更新的說明封包（）檔案的必要名稱格式 `.CAB` 。

## <a name="how-to-name-an-updatable-help-cab-file"></a>如何為可更新說明 CAB 檔案命名

可更新的封包（ `.CAB` ）檔案必須具有下列格式的名稱。

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

名稱的元素如下所示。

- `<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 所傳回之**ModuleInfo**物件的**Name**屬性值。
- `<ModuleGUID>`-模組資訊清單中**GUID**索引鍵的值。
- `<UICulture>`-CAB 檔案中說明檔的 UI 文化特性。 這個值必須符合模組的 HelpInfo XML 檔案中其中一個**UICulture**元素的值。

例如，如果模組名稱是 "TestModule"，則模組 GUID 為 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，而 UI 文化特性為 "en-us"，則 CAB 檔案的名稱會是：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
