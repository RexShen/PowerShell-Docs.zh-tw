---
ms.date: 09/12/2016
ms.topic: reference
title: 如何為 HelpInfo XML 檔案命名
description: 如何為 HelpInfo XML 檔案命名
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659035"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>如何為 HelpInfo XML 檔案命名

本主題說明可更新的說明資訊檔案（通常稱為 HelpInfo XML 檔案）所需的名稱格式。

## <a name="how-to-name-a-helpinfo-xml-file"></a>如何為 HelpInfo XML 檔案命名

HelpInfo XML 檔案的名稱必須是下列格式。

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

名稱的元素如下所示。

- `<ModuleName>`- [Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 傳回之 **ModuleInfo** 物件的 **Name** 屬性值。

- `<ModuleGUID>` -模組資訊清單中 **GUID** 索引鍵的值。

例如，如果模組名稱為 "TestModule"，且模組 GUID 為 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，則模組的 HelpInfo XML 檔案名為：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
