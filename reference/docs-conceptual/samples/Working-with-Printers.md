---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用印表機
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: fce1bc129ada3c509c55941a59a70de230edf68f
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470947"
---
# <a name="working-with-printers"></a>使用印表機

您可以使用 WMI 和 WSH 的 WScript.Network COM 物件，用 Windows PowerShell 來管理印表機。 我們會混合使用這兩種工具，來示範特定的工作。

## <a name="listing-printer-connections"></a>列出印表機連線

使用 WMI **Win32_Printer** 類別是列出電腦上已安裝印表機的最簡單方法︰

```powershell
Get-WmiObject -Class Win32_Printer
```

您也可以使用 WSH 指令碼通常使用的 **WScript.Network** COM 物件列出印表機︰

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

因為這個命令會傳回簡單的連接埠名稱和印表機裝置名稱字串集合，但沒有任何特殊的標籤，所以不容易解譯。

## <a name="adding-a-network-printer"></a>新增網路印表機

若要新增網路印表機，請使用 **WScript.Network**：

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>設定預設印表機

若要使用 WMI 設定預設印表機，請在 **Win32_Printer** 集合中找出印表機，然後叫用 **SetDefaultPrinter** 方法：

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** 較容易使用，因為它有 **SetDefaultPrinter** 方法，只使用印表機名稱作為引數︰

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>移除印表機連線

若要移除印表機連線，請使用 **WScript.Network RemovePrinterConnection** 方法︰

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
