---
ms.date: 09/12/2016
ms.topic: reference
title: 如何更新說明檔
description: 如何更新說明檔
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649591"
---
# <a name="how-to-update-help-files"></a>如何更新說明檔

本主題說明如何更新支援「可更新的說明」之模組的說明檔。

## <a name="updating-help-files"></a>正在更新說明檔

更新說明檔的原因有很多，例如更正錯誤、闡明概念、回答常見問題、新增檔案，或新增更好的範例。

若要更新說明檔：

1. 變更檔案。
1. 將檔案轉譯為其他 UI 文化特性。
1. 針對每個 UI 文化特性中的模組，收集所有說明檔 (新的、已變更和未變更的) 。
1. 針對 XML 架構驗證檔案。
1. 重建每個 UI 文化特性的 CAB 檔案。
1. 在 HelpInfo XML 檔案中，為每個 UI 文化特性遞增 CAB 檔案的版本號碼。
1. 將新的 CAB 檔案上傳至 HelpInfo XML 檔案中 **HelpContentUri** 元素的值所指定的位置。 以新的 CAB 檔案取代舊的封包檔。
1. 將更新的 HelpInfo XML 檔案上傳至模組資訊清單中 **HelpInfoUri** 索引鍵所指定的位置。 以新的檔案取代舊版的 HelpInfo XML 檔案。
