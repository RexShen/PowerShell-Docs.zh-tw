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
# <a name="working-with-printers-in-windows"></a><span data-ttu-id="e2e4c-104">在 Windows 中使用印表機</span><span class="sxs-lookup"><span data-stu-id="e2e4c-104">Working with Printers in Windows</span></span>

<span data-ttu-id="e2e4c-105">您可以使用 PowerShell 藉由使用 WMI 和來自 WSH 的 **WScript.Network** COM 物件，來管理印表機。</span><span class="sxs-lookup"><span data-stu-id="e2e4c-105">You can use PowerShell to manage printers by using WMI and the **WScript.Network** COM object from WSH.</span></span> <span data-ttu-id="e2e4c-106">我們會混合使用這兩種工具，來示範特定的工作。</span><span class="sxs-lookup"><span data-stu-id="e2e4c-106">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="e2e4c-107">列出印表機連線</span><span class="sxs-lookup"><span data-stu-id="e2e4c-107">Listing Printer Connections</span></span>

<span data-ttu-id="e2e4c-108">使用 WMI **Win32_Printer** 類別是列出電腦上已安裝印表機的最簡單方法︰</span><span class="sxs-lookup"><span data-stu-id="e2e4c-108">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-CimInstance -Class Win32_Printer
```

<span data-ttu-id="e2e4c-109">您也可以使用 WSH 指令碼通常使用的 **WScript.Network** COM 物件列出印表機︰</span><span class="sxs-lookup"><span data-stu-id="e2e4c-109">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="e2e4c-110">因為這個命令會傳回簡單的連接埠名稱和印表機裝置名稱字串集合，但沒有任何特殊的標籤，所以不容易解譯。</span><span class="sxs-lookup"><span data-stu-id="e2e4c-110">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="e2e4c-111">新增網路印表機</span><span class="sxs-lookup"><span data-stu-id="e2e4c-111">Adding a Network Printer</span></span>

<span data-ttu-id="e2e4c-112">若要新增網路印表機，請使用 **WScript.Network** ：</span><span class="sxs-lookup"><span data-stu-id="e2e4c-112">To add a new network printer, use **WScript.Network** :</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="e2e4c-113">設定預設印表機</span><span class="sxs-lookup"><span data-stu-id="e2e4c-113">Setting a Default Printer</span></span>

<span data-ttu-id="e2e4c-114">若要使用 WMI 設定預設印表機，請在 **Win32_Printer** 集合中找出印表機，然後叫用 **SetDefaultPrinter** 方法：</span><span class="sxs-lookup"><span data-stu-id="e2e4c-114">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
```

<span data-ttu-id="e2e4c-115">**WScript.Network** 較容易使用，因為它有 **SetDefaultPrinter** 方法，只使用印表機名稱作為引數︰</span><span class="sxs-lookup"><span data-stu-id="e2e4c-115">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="e2e4c-116">移除印表機連線</span><span class="sxs-lookup"><span data-stu-id="e2e4c-116">Removing a Printer Connection</span></span>

<span data-ttu-id="e2e4c-117">若要移除印表機連線，請使用 **WScript.Network RemovePrinterConnection** 方法︰</span><span class="sxs-lookup"><span data-stu-id="e2e4c-117">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
