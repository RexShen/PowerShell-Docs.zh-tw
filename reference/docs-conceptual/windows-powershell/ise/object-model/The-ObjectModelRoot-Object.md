---
ms.date: 08/25/2017
title: ObjectModelRoot 物件
description: $psISE 物件 (PowerShell ISE 中的主體根物件) 是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 類別的執行個體。 本主題描述 ObjectModelRoot 物件的屬性。
ms.openlocfilehash: c8ae703c2663256ca037090fd3b1eb239cfc431a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660946"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot 物件

`$psISE` 物件 (Windows PowerShell&reg; 整合式指令碼環境 (ISE) 中的主體根物件) 是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 類別的執行個體。 本主題描述 **ObjectModelRoot** 物件的屬性。

## <a name="properties"></a>屬性

### <a name="currentfile"></a>CurrentFile

> 在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得目前具有焦點之主機物件相關聯的檔案。

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> 在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得具有焦點的 PowerShell 索引標籤。

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> 在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得目前顯示於編輯器底部水平工具窗格的 Windows PowerShell ISE 附加元件工具。

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> 在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得目前顯示於編輯器右邊垂直工具窗格的 Windows PowerShell ISE 附加元件工具。

### <a name="options"></a>選項

> 在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，取得可變更 Windows PowerShell ISE 中之設定的各種選項。

### <a name="powershelltabs"></a>PowerShellTabs

> 在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得 Windows PowerShell ISE 中開啟的 PowerShell 索引標籤集合。 根據預設，這個物件包含一個 PowerShell 索引標籤。不過，您可以使用指令碼，或使用 Windows PowerShell ISE 中的功能表，新增多個 PowerShell 索引標籤到此物件中。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
