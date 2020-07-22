---
title: 如何為 HelpInfo XML 檔案命名
ms.date: 09/12/2016
ms.openlocfilehash: 9505a7f66852a569d25ac0c1be86e68f870a7930
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892926"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>如何為 HelpInfo XML 檔案命名

本主題說明可更新的說明資訊檔案（通常稱為 HelpInfo XML 檔案）所需的名稱格式。

## <a name="how-to-name-a-helpinfo-xml-file"></a>如何為 HelpInfo XML 檔案命名

HelpInfo XML 檔案的名稱必須是下列格式。

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

名稱的元素如下所示。

- `<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 所傳回之**ModuleInfo**物件的**Name**屬性值。

- `<ModuleGUID>`-模組資訊清單中**GUID**索引鍵的值。

例如，如果模組名稱是 "TestModule"，而模組 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，則模組的 HelpInfo XML 檔案名稱會是：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
