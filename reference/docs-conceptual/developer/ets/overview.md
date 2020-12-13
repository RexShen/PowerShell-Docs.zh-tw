---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統總覽
description: 擴充類型系統總覽
ms.openlocfilehash: f4a789f779fa8a52f0fe524abff7ec3311e93b6c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655730"
---
# <a name="extended-type-system-overview"></a>擴充類型系統總覽

PowerShell 使用其 **PSObject** 物件以兩種方式擴充物件的類型。 首先， **PSObject** 物件會提供一種方式來顯示特定物件類型的不同視圖。 這稱為顯示物件的調整視圖。 其次， **PSObject** 物件提供將成員新增至現有物件的方法。 藉由包裝現有的物件（稱為基底物件）， **PSObject** 物件會提供擴充類型系統 (ETS) ，腳本和 Cmdlet 開發人員可以使用該介面來操作 shell 內的 .net 物件。

## <a name="cmdlet-and-script-development-issues"></a>Cmdlet 和腳本開發問題

ETS 可解決兩個基本問題：

首先，某些 .NET 物件沒有必要的預設行為，可作為 Cmdlet 之間的資料。

- 某些 .NET 物件是 "meta" 物件 (例如： WMI 物件、ADO 物件和 XML 物件) 其成員描述其包含的資料。 不過，在腳本環境中，它是包含最重要的資料，而不是包含資料的描述。 ETS 藉由引進調整基礎 .NET 物件以具有預期預設語義的介面卡概念來解決此問題。
- 某些 .NET 物件成員的名稱不一致、提供的公用成員集不足，或提供的功能不足。 ETS 藉由引進擴充 .NET 物件與其他成員的功能來解決此問題。

其次，PowerShell 腳本 _語言是無型別，因為_ 變數不需要宣告特定型別。 也就是說，腳本開發人員所建立的變數 _是本質上_ 的類型。 不過，PowerShell 系統是「型別驅動」，因為它相依于具有可針對基本作業（例如輸出結果或排序）進行操作的型別名稱。

因此，腳本開發人員必須能夠陳述其中一個變數的類型，並建立自己的一組動態類型「物件」，其中包含屬性和方法，而且可以參與型別驅動系統。 ETS 可解決這個問題，方法是提供指令碼語言的通用物件，讓它能夠動態地指出其型別並動態新增成員。

基本上，ETS 會藉由提供 **PSObject** 物件來解決先前所述的問題，該物件會作為從指令碼語言存取所有物件的基礎，並為 Cmdlet 開發人員提供標準的抽象概念。

### <a name="cmdlet-developers"></a>Cmdlet 開發人員

針對 Cmdlet 開發人員，ETS 提供下列支援：

- 使用 **PSObject** 物件以一般方式處理物件的抽象概念。 ETS 也可讓您視需要深入瞭解這些抽象概念。
- 使用已知的擴充成員集合，為物件類型的格式設定、排序、序列化和其他系統操作建立預設行為的機制。
- 使用 Languageprimitives.physicalequality 物件，針對使用與指令碼語言相同之語義的任何物件進行操作的方法。
- 以動態方式「輸入」雜湊表的方式，讓系統的其餘部分可以有效地操作。

### <a name="script-developers"></a>腳本開發人員

針對腳本開發人員，ETS 提供下列支援：

- 使用相同語法 () 來參考任何基礎物件類型的能力 `$a.x` 。
- 存取 **PSObject** 物件所提供之抽象概念以外的能力 (例如只存取調整的成員，或存取基底物件本身) 。
- 能夠定義知名的成員，以控制物件實例或型別的格式化、排序、序列化和其他操作。
- 將物件命名為特定類型，進而控制其型別型成員繼承的方法。
- 新增、移除和修改擴充成員的能力。
- 必要時操作 **PSObject** 物件本身的能力。

## <a name="the-psobject-class"></a>PSObject 類別

**PSObject** 物件是從指令碼語言存取所有物件的基礎，並且為 Cmdlet 開發人員提供標準的抽象概念。 它包含一個基底物件， (.NET 物件) ，以及在特定物件實例上的任何實例成員 (成員（特別是擴充成員），而不一定會出現在相同類型) 的其他物件上。 根據基底物件的類型而定， **PSObject** 物件也可能會對調整的成員以及任何以類型為基礎的擴充成員提供隱含且明確的存取權。

**PSObject** 物件提供下列機制：

- 使用或不含基底物件來建立 **PSObject** 的能力。
- 透過一般查閱演算法來存取每個已建立之 **PSObject** 物件的所有成員，以及在必要時覆寫該演算法的能力。
- 取得和設定所建立之 **psobject** 物件的型別名稱的能力，讓腳本和 Cmdlet 可以參考相同型別名稱的類似 **PSObject** 物件，不論其基底物件的型別為何。

### <a name="how-to-construct-a-psobject"></a>如何建立 PSObject

下列清單描述建立 **PSObject** 物件的方式：

- 呼叫 **PSObject** . #ctor 的函式會使用 PSCustomObject 的基底物件來建立新的 **PSObject** 物件。 這個型別的基底物件表示 **PSObject** 物件沒有有意義的基底物件。 不過，具有這種類型之基底物件的 **PSObject** 物件確實提供了一個屬性包，讓指令程式開發人員可以藉由新增擴充成員找到實用的功能。

開發人員也可以指定物件類型名稱，以允許此物件與相同類型名稱的其他 **PSObject** 物件共用其擴充成員。

- 呼叫 **PSObject** . #ctor (system.string) 的函式會建立一個新的 **PSObject** 物件，其基底物件為 system.object 類型。

  在此情況下，所建立物件的型別名稱就是基底物件之衍生階層的集合。 例如，包含 ProcessInfo 基底物件之 **PSObject** 的類型名稱會包含下列名稱：

  - System.Diagnostics.Process
  - ComponentModel 元件
  - System.MarshalByRefObject
  - System.Object

- 呼叫 **PSObject** 。AsPSObject (System.object) 方法會根據提供的物件建立新的 **PSObject** 物件。

  如果提供的物件為 system.string 類型，則會使用提供的物件做為新 **PSObject** 物件的基底物件。 如果提供的物件已經是 **PSObject** 物件，則會以原樣傳回提供的物件。

### <a name="base-adapted-and-extended-members"></a>基底、調整及擴充成員

就概念而言，ETS 會使用下列詞彙來顯示基底物件的原始成員與 PowerShell 新增的成員之間的關聯性。 如需 **psobject** 物件所使用之特定類型成員的詳細資訊，請參閱 [psobject 類別](/dotnet/api/system.management.automation.psobject)。

#### <a name="base-object-members"></a>基底物件成員

如果在建立 **PSObject** 物件時指定了基底物件，則基底物件的成員可透過 members 屬性取得。

#### <a name="adapted-members"></a>改編的成員

當基底物件是中繼物件時，其中一個物件會以一般方式（其屬性「描述」其包含的資料）來包含資料，ETS 會將這些物件調整為可讓您透過調整的 **PSObject** 物件成員直接存取資料的視圖。 您可以透過 Members 屬性來存取調整的成員和基底物件成員。

#### <a name="extended-members"></a>擴充成員

除了從基底物件或由 PowerShell 所建立的調整成員中提供的成員之外， **PSObject** 也可以定義擴充成員，以擴充原始的基底物件與腳本環境中有用的其他資訊。

例如，PowerShell 提供的所有核心 Cmdlet （例如 Get-Content 和 Set-Content Cmdlet）都會採用 path 參數。 為了確保這些 Cmdlet 和其他 Cmdlet 可以針對不同類型的物件來工作，您可以將路徑成員新增至這些物件，讓它們都能以一般方式來陳述其資訊。 這個擴充路徑成員可以確保 Cmdlet 可以針對所有這些類型運作，即使基類可能沒有路徑成員也一樣。

擴充的成員、調整的成員和基底物件成員都是透過 Members 屬性來存取。
