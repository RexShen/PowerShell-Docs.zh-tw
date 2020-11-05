---
ms.date: 12/31/2019
title: ISE 物件模型階層
description: 此文章說明屬於 Windows PowerShell ISE 一部分的物件階層。
ms.openlocfilehash: 00980cda72f05bc6ccb398079b129de13a98f783
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658332"
---
# <a name="the-ise-object-model-hierarchy"></a>ISE 物件模型階層

此文章說明屬於 Windows PowerShell 整合式指令碼環境 (ISE) 一部分的物件階層。 Windows PowerShell ISE 隨附於 Windows PowerShell 3.0、4.0 和 5.1。 按一下物件，即會帶領您進入定義物件之類別的參考文件。

## <a name="psise-object"></a>$psISE 物件

`$psISE` 物件是 Windows PowerShell ISE 物件階層的[根物件](The-ObjectModelRoot-Object.md)。 它位於最上層，可提供下列物件來編寫指令碼︰

## <a name="psisecurrentfile"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

`$psISE.CurrentFile` 物件是 [ISEFile](The-ISEFile-Object.md) 類別的執行個體。

## <a name="psisecurrentpowershelltab"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

`$psISE.CurrentPowerShellTab` 物件是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

`$psISE.CurrentVisibleHorizontalTool` 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。 它代表目前停駐於 Windows PowerShell ISE 視窗頂端的已安裝附加元件工具。

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

`$psISE.CurrentVisibleHorizontalTool` 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。 它代表目前停駐於 Windows PowerShell ISE 視窗右邊的已安裝附加元件工具。

## <a name="psiseoptions"></a>[$psISE.Options](The-ISEOptions-Object.md)

`$psISE.Options` 物件是 [ISEOptions](The-ISEOptions-Object.md) 類別的執行個體。 ISEOptions 物件代表適用於 Windows PowerShell ISE 的各種設定。 其為 Microsoft.PowerShell.Host.ISE.ISEOptions 類別的執行個體。

## <a name="psisepowershelltabs"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

`$psISE.PowerShellTabs` 物件是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 類別的執行個體。 它是所有目前開啟的 PowerShell 索引標籤集合，代表本機電腦上或連線的遠端電腦上可用的 Windows PowerShell 執行環境。 集合中的每個成員都是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
