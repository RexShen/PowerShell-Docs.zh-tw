---
title: "使用印表機"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 27d3d11b71b95cd79817449cf8bdb1a0a26936bd

---

# 使用印表機
您可以使用 WMI 和 WSH 的 WScript.Network COM 物件，用 Windows PowerShell 來管理印表機。 我們會混合使用這兩種工具，來示範特定的工作。

### 列出印表機連線
使用 WMI **Win32\_Printer** 類別是列出電腦上已安裝印表機的最簡單方法︰

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

您也可以使用 WSH 指令碼通常使用的 **WScript.Network** COM 物件列出印表機︰

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

因為這個命令會傳回簡單的連接埠名稱和印表機裝置名稱字串集合，但沒有任何特殊的標籤，所以不容易解譯。

### 新增網路印表機
若要新增網路印表機，請使用 **WScript.Network**：

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### 設定預設印表機
若要使用 WMI 設定預設印表機，請在 **Win32\_Printer** 集合中找出印表機，然後叫用 **SetDefaultPrinter** 方法：

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** 較容易使用，因為它有 **SetDefaultPrinter** 方法，只使用印表機名稱作為引數︰

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### 移除印表機連線
若要移除印表機連線，請使用 **WScript.Network RemovePrinterConnection** 方法︰

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```




<!--HONumber=Jun16_HO4-->


