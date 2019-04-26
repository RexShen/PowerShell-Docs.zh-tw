---
title: 如何命名 HelpInfo XML 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082391"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>如何為 HelpInfo XML 檔案命名

本主題說明可更新的說明資訊檔案，通常稱為 HelpInfo XML 檔案的必要的名稱格式。

## <a name="how-to-name-a-helpinfo-xml-file"></a>如何為 HelpInfo XML 檔案命名

HelpInfo XML 檔案必須具有下列格式的名稱。

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

名稱的項目如下所示。

模組名稱值的**名稱**屬性**ModuleInfo**物件[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 會傳回。

ModuleGUID 值的**GUID**模組資訊清單中的索引鍵。

比方說，如果模組名稱是"TestModule 」，此模組的 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 模組 HelpInfo XML 檔案的名稱將會是：

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`