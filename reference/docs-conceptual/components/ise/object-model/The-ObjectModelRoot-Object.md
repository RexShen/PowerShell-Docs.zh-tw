---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: ObjectModelRoot 物件
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402068"
---
# <a name="the-objectmodelroot-object"></a>ObjectModelRoot 物件

**$psISE** 物件 (Windows PowerShell® 整合式指令碼環境中 (ISE) 的主要根物件) 是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 類別的執行個體。
本主題描述 **ObjectModelRoot** 物件的屬性。

## <a name="properties"></a>Properties

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