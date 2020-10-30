---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 使用印表機
description: 本文說明如何使用 WMI 物件與 COM 介面，在 Windows 中管理印表機。
ms.openlocfilehash: 2606753783043eeae8e9d461e56f0901149cb8e3
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501077"
---
# <a name="working-with-printers-in-windows"></a>在 Windows 中使用印表機

您可以使用 PowerShell 藉由使用 WMI 和來自 WSH 的 **WScript.Network** COM 物件，來管理印表機。 我們會混合使用這兩種工具，來示範特定的工作。

## <a name="listing-printer-connections"></a>列出印表機連線

使用 WMI **Win32_Printer** 類別是列出電腦上已安裝印表機的最簡單方法︰

```powershell
Get-CimInstance -Class Win32_Printer
```

您也可以使用 WSH 指令碼通常使用的 **WScript.Network** COM 物件列出印表機︰

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

因為這個命令會傳回簡單的連接埠名稱和印表機裝置名稱字串集合，但沒有任何特殊的標籤，所以不容易解譯。

## <a name="adding-a-network-printer"></a>新增網路印表機

若要新增網路印表機，請使用 **WScript.Network** ：

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>設定預設印表機

若要使用 WMI 設定預設印表機，請在 **Win32_Printer** 集合中找出印表機，然後叫用 **SetDefaultPrinter** 方法：

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
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
