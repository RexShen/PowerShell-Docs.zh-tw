---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用印表機
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954495"
---
# <a name="working-with-printers"></a><span data-ttu-id="33e45-103">使用印表機</span><span class="sxs-lookup"><span data-stu-id="33e45-103">Working with Printers</span></span>

<span data-ttu-id="33e45-104">您可以使用 WMI 和 WSH 的 WScript.Network COM 物件，用 Windows PowerShell 來管理印表機。</span><span class="sxs-lookup"><span data-stu-id="33e45-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="33e45-105">我們會混合使用這兩種工具，來示範特定的工作。</span><span class="sxs-lookup"><span data-stu-id="33e45-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="33e45-106">列出印表機連線</span><span class="sxs-lookup"><span data-stu-id="33e45-106">Listing Printer Connections</span></span>

<span data-ttu-id="33e45-107">使用 WMI **Win32_Printer** 類別是列出電腦上已安裝印表機的最簡單方法︰</span><span class="sxs-lookup"><span data-stu-id="33e45-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="33e45-108">您也可以使用 WSH 指令碼通常使用的 **WScript.Network** COM 物件列出印表機︰</span><span class="sxs-lookup"><span data-stu-id="33e45-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="33e45-109">因為這個命令會傳回簡單的連接埠名稱和印表機裝置名稱字串集合，但沒有任何特殊的標籤，所以不容易解譯。</span><span class="sxs-lookup"><span data-stu-id="33e45-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="33e45-110">新增網路印表機</span><span class="sxs-lookup"><span data-stu-id="33e45-110">Adding a Network Printer</span></span>

<span data-ttu-id="33e45-111">若要新增網路印表機，請使用 **WScript.Network**：</span><span class="sxs-lookup"><span data-stu-id="33e45-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="33e45-112">設定預設印表機</span><span class="sxs-lookup"><span data-stu-id="33e45-112">Setting a Default Printer</span></span>

<span data-ttu-id="33e45-113">若要使用 WMI 設定預設印表機，請在 **Win32_Printer** 集合中找出印表機，然後叫用 **SetDefaultPrinter** 方法：</span><span class="sxs-lookup"><span data-stu-id="33e45-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="33e45-114">**WScript.Network** 較容易使用，因為它有 **SetDefaultPrinter** 方法，只使用印表機名稱作為引數︰</span><span class="sxs-lookup"><span data-stu-id="33e45-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="33e45-115">移除印表機連線</span><span class="sxs-lookup"><span data-stu-id="33e45-115">Removing a Printer Connection</span></span>

<span data-ttu-id="33e45-116">若要移除印表機連線，請使用 **WScript.Network RemovePrinterConnection** 方法︰</span><span class="sxs-lookup"><span data-stu-id="33e45-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```