---
title: Windows PowerShell 程式設計&#39;指南 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: 0ca836d1044e46d3a7dcbc69fa93d84f74848559
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920385"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell 程式設計&#39;指南

此程式設計人員指南的適用對象是開發人員感興趣的系統管理員提供的命令列管理環境。 Windows PowerShell 提供簡單的方法，讓您建立公開.NET 物件，同時允許 Windows PowerShell，為您執行大部分工作的管理命令。

傳統的命令在開發中，您必須將參數剖析器、 參數繫結器、 篩選和每個命令所公開的所有其他功能。 Windows PowerShell 提供下列內容，讓您輕鬆地撰寫命令：

- 功能強大 Windows PowerShell 執行階段 （執行引擎） 與它自己的剖析器會自動繫結命令參數的機制。

- 格式化及顯示使用命令列解譯器 (CLI) 命令結果的公用程式。

- 支援的功能 （透過 Windows PowerShell 提供者） 可讓您輕鬆地存取儲存的資料達到更高層級。

  較少的成本，您可以表示的.NET 物件，藉由豐富的命令或一組將提供完整的命令列體驗，以系統管理員的命令。

  下一節涵蓋重要的 Windows PowerShell 概念和詞彙。 熟悉這些概念和條款，然後才能開始開發。

## <a name="about-windows-powershell"></a>關於 Windows PowerShell

Windows PowerShell 在開發過程中定義命令，您可以使用數種的類型。 這些命令包括： 函式、 篩選、 指令碼、 別名和可執行檔 （應用程式）。 本指南中討論的主要命令類型是簡單、 小型命令，稱為 「 cmdlet 」。 Windows PowerShell 提供一組指令程式，並完全支援 cmdlet 自訂以符合您的環境。 Windows PowerShell 執行階段會處理所有命令類型，就如同 cmdlet，使用管線。

除了命令之外，Windows PowerShell 支援各種可自訂 Windows PowerShell 提供者，可以使用特定的 cmdlet 集。 在 Windows PowerShell 提供的主機應用程式 (Windows PowerShell.exe) 內設置殼層的作業，但同樣可以存取從自訂主應用程式，您可以開發以符合特定需求。 如需詳細資訊，請參閱 < [Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlets

Cmdlet 是 Windows PowerShell 環境中使用的輕量型命令。 Windows PowerShell 執行階段會叫用的命令列中，在提供的自動化指令碼內容中的這些 cmdlet 與 Windows PowerShell 執行階段也會叫用它們以程式設計方式透過 Windows PowerShell Api。

如需有關 cmdlet 的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

### <a name="windows-powershell-providers"></a>Windows PowerShell 提供者

在執行系統管理工作，使用者可能需要檢查儲存在資料存放區 （例如，檔案系統、 Windows 登錄中或憑證存放區） 中的資料。 若要簡化這些作業，Windows PowerShell 會定義可用來存取特定資料存放區，例如 Windows 登錄的 Windows PowerShell 提供者會呼叫的模組。 每個提供者支援一組相關的 cmdlet，來授與使用者存放區中資料的對稱式檢視。

Windows PowerShell 提供數個預設的 Windows PowerShell 提供者。 例如，登錄提供者所支援的瀏覽和操作的 Windows 登錄。 登錄機碼以項目，並登錄值會被視為屬性。

如果您公開使用者需要存取的資料存放區，您可能需要撰寫自己的 Windows PowerShell 提供者中所述[建立的 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)。 如需詳細資訊 aboutWindows PowerShell 提供者，請參閱 < [Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

### <a name="host-application"></a>主應用程式

Windows PowerShell 包含預設主控件應用程式 powershell.exe，這是主控台應用程式與使用者互動和裝載 Windows PowerShell 執行階段使用的主控台視窗。

很少會您要撰寫您自己的主應用程式，適用於 Windows PowerShell，雖然支援自訂。 您可能需要自己的應用程式的其中一種情況時，您有預設主控件應用程式所提供的介面比更豐富的 GUI 介面的需求。 當您要根據命令列中的 GUI，您可能也想自訂的應用程式。 如需詳細資訊，請參閱 <<c0> [ 如何建立 Windows PowerShell 主應用程式](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)。

### <a name="windows-powershell-runtime"></a>Windows PowerShell 執行階段

Windows PowerShell 執行階段是實作命令處理的執行引擎。 它包含的類別提供的主應用程式和 Windows PowerShell 命令和提供者之間的介面。 Windows PowerShell 執行階段會實作為 runspace 物件，目前的 Windows PowerShell 工作階段，也就是殼層和命令執行的操作環境。 作業的詳細資訊，請參閱[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

### <a name="windows-powershell-language"></a>Windows PowerShell 語言

Windows PowerShell 語言提供指令碼的函式和機制，以叫用命令。 如需完整的指令碼資訊，請參閱 Windows PowerShell 語言參考隨附於 Windows PowerShell。

### <a name="extended-type-system-ets"></a>擴充的型別系統 (ETS)

Windows PowerShell 提供各種不同的物件，例如.NET 和 XML 物件的存取。 如此一來，呈現所有物件類型的通用抽象概念殼層會使用其擴充型別系統 (ETS)。 大部分的 ETS 功能而言是透明的使用者，但指令碼或.NET 開發人員會將它用於下列用途：

- 檢視特定物件的成員子集。 Windows PowerShell 提供數個特定物件類型的 「 調整 」 檢視。

- 將成員加入至現有的物件。

- 若要存取序列化的物件。

- 撰寫自訂物件。

  ETS，您可以使用建立有彈性的新 「 類型 」，與 Windows PowerShell 語言相容。 如果您是.NET 開發人員，也可以搭配物件使用相同的語意，在 Windows PowerShell 語言套用至指令碼，例如，若要判斷物件是否評估為`true`。

  如需有關 ETS 和 Windows PowerShell 如何使用物件的詳細資訊，請參閱[Windows PowerShell 物件概念](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)。

## <a name="programming-for-windows-powershell"></a>適用於 Windows PowerShell 的程式設計

Windows PowerShell 會定義它的程式碼的命令、 提供者，以及其他使用.NET Framework 的應用程式模組。 您是不受限於使用 Microsoft Visual Studio 中適用於 Windows PowerShell 建立自訂的模組雖然已知此工具中執行本指南中提供的範例。 您可以使用任何.NET 語言支援類別繼承和使用的屬性。 在某些情況下，Windows PowerShell Api 會需要能夠存取的泛型類型的程式設計語言。

## <a name="programmers-reference"></a>程式設計人員參考

如需開發適用於 Windows PowerShell 時的參考，請參閱[Windows PowerShell SDK](../windows-powershell-reference.md)。

## <a name="getting-started-using-windows-powershell"></a>使用 Windows PowerShell 入門

如需有關如何開始使用 Windows PowerShell 殼層的詳細資訊，請參閱 < [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)隨附於 Windows PowerShell。 快速參考三摺式文件也會提供方式 cmdlet 使用的入門。

## <a name="contents-of-this-guide"></a>本指南的內容

|主題|定義|
|-----------|----------------|
|[如何建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)|本節說明如何建置適用於 Windows PowerShell 的 Windows PowerShell 提供者。|
|[如何建立 Windows PowerShell 主應用程式](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|本章節描述如何撰寫操作 runspace 的主應用程式，以及撰寫實作自己的自訂主機的主機應用程式。|
|[如何建立 Windows PowerShell 嵌入式管理單元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|本章節描述如何建立一個嵌入式管理單元，可用來註冊組件中的所有 cmdlet 和提供者，以及如何建立自訂的嵌入式管理單元。|
|[如何建立主控台殼層](./how-to-create-a-console-shell.md)|本節說明如何建立不是可延伸的主控台介面。|
|[Windows PowerShell 概念](./windows-powershell-concepts.md)|本節包含可協助您了解 Windows PowerShell，從開發人員的觀點來看的概念性資訊。|

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
