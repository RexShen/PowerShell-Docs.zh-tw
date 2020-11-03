---
description: Windows Management Instrumentation (WMI) 使用通用訊息模型 (CIM) 來代表系統、應用程式、網路、裝置，以及現代企業的其他可管理元件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207891"
---
# <a name="about-wmi"></a>關於 WMI

## <a name="short-description"></a>簡短描述

Windows Management Instrumentation (WMI) 使用通用訊息模型 (CIM) 來代表系統、應用程式、網路、裝置，以及現代企業的其他可管理元件。

## <a name="long-description"></a>詳細描述

Windows Management Instrumentation (WMI) 是 Microsoft 的 Web-Based Enterprise Management (WBEM) （業界標準）實行。

傳統 WMI 使用 DCOM 與網路裝置通訊，以管理遠端系統。 Windows PowerShell 3.0 引進了 CIM 提供者模型，此模型會使用 WinRM 來移除 DCOM 的相依性。 這個 CIM 提供者模型也會使用新的 WMI 提供者 Api，讓開發人員以機器碼撰寫 Windows PowerShell Cmdlet (C \+ \+) 。

請勿混淆 WMI 提供者與 Windows PowerShell 提供者。 許多 Windows 功能都有相關聯的 WMI 提供者，它會公開其管理功能。 若要取得 WMI 提供者，請執行 WMI 查詢來取得 __Provider WMI 類別的實例，如下列查詢所示。

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a>WMI 的三個元件

下列三個 WMI 元件會與 Windows PowerShell 互動：命名空間、提供者和類別。

WMI 命名空間會將 WMI 提供者和 WMI 類別組織成相關元件的群組。 如此一來，它們就類似 .NET Framework 命名空間。
命名空間不是實體位置，而是比較類似的邏輯資料庫。
所有 WMI 命名空間都是 __Namespace 系統類別的實例。 預設的 WMI 命名空間是 \/ Microsoft Windows 2000) 之後 (根 CIMV2。 若要使用 Windows PowerShell 取得目前會話中的 WMI 命名空間，請使用具有下列格式的命令。

```powershell
Get-WmiObject -Class __Namespace
```

若要取得其他命名空間中的 WMI 命名空間，請使用 Namespace 參數來變更搜尋的位置。 下列命令會尋找位於根/Cimv2/Applications 命名空間中的 WMI 命名空間。

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

WMI 命名空間是階層式的。 因此，若要取得特定系統上的所有命名空間清單，則必須執行從根命名空間開始的遞迴查詢。

WMI 提供者會公開 Windows 可管理物件的相關資訊。 提供者會從元件中取出資料，並透過 WMI 將該資料傳遞至管理應用程式，例如 Windows PowerShell。 大部分的 WMI 提供者都是動態提供者，這表示它們會在透過管理應用程式要求時動態取得資料。

## <a name="finding-wmi-classes"></a>尋找 WMI 類別

在 Windows 8 的預設安裝中，根 Cimv2 中有1100以上的 WMI 類別 \/ 。 有了許多 WMI 類別，挑戰就變成識別要用來執行特定工作的適當 WMI 類別。 Windows PowerShell 3.0 提供兩種方式來尋找與特定主題相關的 WMI 類別。

例如，若要在跟磁片相關的根 \\ CIMV2 wmi 命名空間中尋找 wmi 類別，您可以使用如下所示的查詢。

```powershell
Get-WmiObject -List *disk*
```

若要尋找與記憶體相關的 WMI 類別，您可以使用如下所示的查詢。

```powershell
Get-WmiObject -List *memory*
```

CIM Cmdlet 也提供探索 WMI 類別的功能。 若要這樣做，請使用 Get-CIMClass Cmdlet。 此處顯示的命令會列出與影片相關的 WMI 類別。

```powershell
Get-CimClass *video*
```

索引標籤擴充可在變更 WMI 命名空間時運作，因此使用 tab 鍵擴充可輕鬆地探索子 WMI 命名空間。 在下列範例中，Get-CimClass Cmdlet 會列出與電源設定相關的 WMI 類別。
若要找到它，請輸入 `root/CIMV2/` 命名空間，然後按下 tab 鍵數次，直到 power namespace 出現為止。 命令如下：

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
