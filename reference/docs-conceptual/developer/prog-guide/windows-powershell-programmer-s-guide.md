---
title: Windows PowerShell 程式設計人員&#39;s 指南 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.openlocfilehash: 64feb66b8e42ab12b279025ebe6c86d7f91ecae5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771561"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell 程式設計人員&#39;s 指南

這個程式設計人員指南的目標物件是有興趣為系統管理員提供命令列管理環境的開發人員。 Windows PowerShell 提供簡單的方法，讓您建立可公開 .NET 物件的管理命令，同時允許 Windows PowerShell 為您執行大部分的工作。

在傳統的命令開發中，您必須撰寫參數剖析器、參數系結器、篩選，以及每個命令所公開的所有其他功能。 Windows PowerShell 提供下列各項，讓您可以輕鬆地撰寫命令：

- 功能強大的 Windows PowerShell 執行時間 (執行引擎) 本身的剖析器，以及自動系結命令參數的機制。

- 使用命令列解譯器來格式化和顯示命令結果的公用程式 (CLI) 。

- 支援透過 Windows PowerShell 提供者 (的高階功能，) 可讓您輕鬆存取儲存的資料。

  就成本而言，您可以透過豐富的命令或一組命令來呈現 .NET 物件，以提供系統管理員完整的命令列體驗。

  下一節將討論 Windows PowerShell 的重要概念和詞彙。 開始開發之前，請先熟悉這些概念和詞彙。

## <a name="about-windows-powershell"></a>關於 Windows PowerShell

Windows PowerShell 定義數種可在開發中使用的命令類型。 這些命令包括：函式、篩選器、腳本、別名和可執行檔 (應用程式) 。 本指南中所討論的主要命令類型是簡單、小型的命令，稱為「Cmdlet」。 Windows PowerShell 會 furnishes 一組 Cmdlet，並完全支援 Cmdlet 自訂以符合您的環境。 Windows PowerShell 執行時間會處理所有命令類型，就如同使用管線執行 Cmdlet 一樣。

除了命令之外，Windows PowerShell 還支援各種可自訂的 Windows PowerShell 提供者，可讓您使用特定的 Cmdlet 集。 Shell 會在 Windows PowerShell 提供的主應用程式 (Windows PowerShell.exe) 中運作，但同樣可從您可以開發以符合特定需求的自訂主應用程式存取。 如需詳細資訊，請參閱[Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))。

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet

Cmdlet 是在 Windows PowerShell 環境中使用的輕量命令。 Windows PowerShell 執行時間會在命令列提供的自動化腳本內容中叫用這些 Cmdlet，而 Windows PowerShell 執行時間也會透過 Windows PowerShell Api 以程式設計方式叫用這些指令程式。

如需 Cmdlet 的詳細資訊，請參閱[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

### <a name="windows-powershell-providers"></a>Windows PowerShell 提供者

在執行系統管理工作時，使用者可能需要檢查儲存在資料存放區中的資料 (例如，檔案系統、Windows 登錄或憑證存放區) 。 為了讓這些作業更容易，Windows PowerShell 會定義一個稱為 Windows PowerShell 提供者的模組，可用來存取特定的資料存放區，例如 Windows 登錄。 每個提供者都支援一組相關的 Cmdlet，讓使用者對存放區中的資料進行對稱的查看。

Windows PowerShell 提供數個預設的 Windows PowerShell 提供者。 例如，登錄提供者支援 Windows 登錄的流覽和操作。 登錄機碼會以專案表示，而登錄值會被視為屬性。

如果您公開使用者將需要存取的資料存放區，您可能需要撰寫自己的 Windows PowerShell 提供者，如[建立 Windows Powershell 提供者](./how-to-create-a-windows-powershell-provider.md)中所述。 如需 aboutWindows PowerShell 提供者的詳細資訊，請參閱[Windows powershell 的運作方式](/previous-versions//ms714658(v=vs.85))。

### <a name="host-application"></a>主機應用程式

Windows PowerShell 包含預設的主應用程式 powershell.exe，這是一個主控台應用程式，可與使用者互動，並使用主控台視窗裝載 Windows PowerShell 執行時間。

雖然支援自訂，但您只需要為 Windows PowerShell 撰寫自己的主應用程式。 您可能需要自己應用程式的情況之一，就是當您的 GUI 介面需求比預設主應用程式所提供的介面更豐富時。 當您在命令列上建立 GUI 的基礎時，您可能也會想要自訂應用程式。 如需詳細資訊，請參閱[如何建立 Windows PowerShell 主應用程式](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)。

### <a name="windows-powershell-runtime"></a>Windows PowerShell 執行時間

Windows PowerShell 執行時間是執行命令處理的執行引擎。 其中包含的類別可提供主機應用程式和 Windows PowerShell 命令和提供者之間的介面。 Windows PowerShell 執行時間會實作為目前 Windows PowerShell 會話的執行時間物件，這是執行 shell 和命令的操作環境。 如需操作詳細資料，請參閱[Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))。

### <a name="windows-powershell-language"></a>Windows PowerShell 語言

Windows PowerShell 語言提供用來叫用命令的腳本功能和機制。 如需完整的腳本資訊，請參閱 windows PowerShell 隨附的 Windows PowerShell 語言參考。

### <a name="extended-type-system-ets"></a>擴充類型系統 (ETS) 

Windows PowerShell 可讓您存取各種不同的物件，例如 .NET 和 XML 物件。 因此，若要呈現所有物件類型的通用抽象概念，shell 會使用其擴充類型系統 (ETS) 。 大部分的 ETS 功能對使用者而言是透明的，但腳本或 .NET 開發人員會使用它來執行下列動作：

- 查看特定物件的成員子集。 Windows PowerShell 提供數個特定物件類型的「調整」視圖。

- 將成員加入至現有的物件。

- 序列化物件的存取權。

- 撰寫自訂物件。

  使用 ETS，您可以建立與 Windows PowerShell 語言相容的彈性新「類型」。 如果您是 .NET 開發人員，您可以使用與 Windows PowerShell 語言適用的相同語義來處理物件，例如，用來判斷物件是否評估為 `true` 。

  如需 ETS 以及 Windows PowerShell 如何使用物件的詳細資訊，請參閱[Windows Powershell 物件概念](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6)。

## <a name="programming-for-windows-powershell"></a>Windows PowerShell 程式設計

Windows PowerShell 會使用 .NET Framework，為命令、提供者和其他程式模組定義其程式碼。 雖然本指南中所提供的範例已知可在此工具中執行，但您不限於使用 Microsoft Visual Studio 建立 Windows PowerShell 的自訂模組。 您可以使用任何支援類別繼承的 .NET 語言，以及使用屬性。 在某些情況下，Windows PowerShell Api 要求程式設計語言必須能夠存取泛型型別。

## <a name="programmers-reference"></a>程式設計人員參考

如需針對 Windows PowerShell 進行開發的參考，請參閱[Windows POWERSHELL SDK](../windows-powershell-reference.md)。

## <a name="getting-started-using-windows-powershell"></a>使用 Windows PowerShell 消費者入門

如需有關如何開始使用 Windows PowerShell shell 的詳細資訊，請參閱 Windows powershell 隨附的[Windows powershell 消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。 同時也提供快速參考三折檔，作為 Cmdlet 使用的入門。

## <a name="contents-of-this-guide"></a>本指南的內容

|主題|定義|
|-----------|----------------|
|[如何建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)|本節說明如何建立 windows PowerShell 的 Windows PowerShell 提供者。|
|[如何建立 Windows PowerShell 主應用程式](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)|本節說明如何撰寫主應用程式來操控執行時間，以及如何撰寫裝載應用程式來執行自己的自訂主機。|
|[如何建立 Windows PowerShell 嵌入式管理單元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|本節說明如何建立嵌入式管理單元，用來在元件中註冊所有 Cmdlet 和提供者，以及如何建立自訂嵌入式管理單元。|
|[如何建立主控台殼層](./how-to-create-a-console-shell.md)|本節說明如何建立不可延伸的主控台 shell。|
|[Windows PowerShell 概念](./windows-powershell-concepts.md)|本節包含的概念資訊，可協助您從開發人員的觀點來瞭解 Windows PowerShell。|

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
