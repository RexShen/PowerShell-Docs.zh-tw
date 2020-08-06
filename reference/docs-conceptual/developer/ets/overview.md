---
title: 擴充類型系統總覽
ms.date: 07/09/2020
ms.openlocfilehash: 5c190f0d9b852a4b5658227085092f33d71453c9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786215"
---
# <a name="extended-type-system-overview"></a>擴充類型系統總覽

PowerShell 會使用其**PSObject**物件，以兩種方式擴充物件的類型。 首先， **PSObject**物件提供一種方式來顯示特定物件類型的不同視圖。 這稱為顯示物件的改編視圖。 第二， **PSObject**物件提供將成員加入至現有物件的方法。 藉由包裝現有的物件（稱為基底物件）， **PSObject**物件會提供擴充型別系統 (ETS) 供腳本和 Cmdlet 開發人員用來在 shell 中操作 .net 物件。

## <a name="cmdlet-and-script-development-issues"></a>Cmdlet 和腳本開發問題

ETS 可解決兩個基本問題：

首先，有些 .NET 物件並沒有必要的預設行為，無法做為 Cmdlet 之間的資料。

- 有些 .NET 物件是「中繼」物件 (例如： WMI 物件、ADO 物件和 XML 物件) 其成員會描述所包含的資料。 不過，在腳本環境中，它是最有趣的資料，而不是包含資料的描述。 ETS 藉由引進介面卡概念來解決此問題，使基礎 .NET 物件能夠具有預期的預設語義。
- 有些 .NET 物件成員的名稱不一致，提供的公用成員集不足，或提供的功能不足。 ETS 藉由引進擴充 .NET 物件與其他成員的功能來解決此問題。

第二，PowerShell 腳本_語言是無類型的，因為_變數不需要宣告特定類型。 也就是說，腳本開發人員所建立的_變數本質上_是無類型的。 不過，PowerShell 系統是「型別導向」，因為它相依于針對基本作業（例如輸出結果或排序）操作型別名稱。

因此，腳本開發人員必須能夠陳述其中一個變數的型別，並建立自己的一組動態類型「物件」，其中包含屬性和方法，而且可以參與型別驅動系統。 ETS 可解決這個問題，方法是提供指令碼語言的通用物件，讓它能夠動態地陳述其型別，以及動態新增成員。

基本上，ETS 會解決先前所述的問題，方法是提供**PSObject**物件，以作為所有從指令碼語言存取物件的基礎，並為 Cmdlet 開發人員提供標準的抽象概念。

### <a name="cmdlet-developers"></a>Cmdlet 開發人員

對於 Cmdlet 開發人員，ETS 提供下列支援：

- 使用**PSObject**物件以一般方式處理物件的抽象概念。 ETS 也可讓您在必要時，深入探索這些抽象概念。
- 使用一組知名的擴充成員，為其物件類型的格式、排序、序列化和其他系統操作建立預設行為的機制。
- 使用與使用 Languageprimitives.physicalequality 物件之指令碼語言相同的語義，針對任何物件操作的方式。
- 動態「輸入」雜湊表的方法，讓系統的其餘部分可以有效地對它進行操作。

### <a name="script-developers"></a>腳本開發人員

針對腳本開發人員，ETS 提供下列支援：

- 使用相同的語法 () 來參考任何基礎物件類型的能力 `$a.x` 。
- 存取不是**PSObject**物件所提供之抽象概念的能力 (例如僅存取調整的成員，或存取基底物件本身) 。
- 能夠定義已知的成員，以控制物件實例或類型的格式設定、排序、序列化和其他操作。
- 表示將物件命名為特定類型，進而控制其型別型成員的繼承。
- 新增、移除和修改擴充成員的能力。
- 必要時操作**PSObject**物件本身的功能。

## <a name="the-psobject-class"></a>PSObject 類別

**PSObject**物件是所有從指令碼語言存取物件的基礎，並為 Cmdlet 開發人員提供標準的抽象概念。 它包含一個基底物件 (.NET 物件) 和任何實例成員 (成員（特別是擴充成員）存在於特定物件實例上，而不一定是相同類型) 的其他物件。 根據基底物件的類型而定， **PSObject**物件也可能提供對調整成員的隱含和明確存取權，以及任何以類型為基礎的擴充成員。

**PSObject**物件提供下列機制：

- 能夠在不使用基底物件的情況下，建立**PSObject** 。
- 透過一般查閱演算法存取每個已建立之**PSObject**物件的所有成員，以及在需要時覆寫該演算法的功能。
- 能夠取得和設定所建立之**psobject**物件的型別名稱，讓腳本和 Cmdlet 可以根據相同的型別名稱來參考類似的**PSObject**物件，而不論其基底物件的型別為何。

### <a name="how-to-construct-a-psobject"></a>如何建立 PSObject

下列清單描述建立**PSObject**物件的方式：

- 呼叫**PSObject** . #ctor 的函式會使用 PSCustomObject 的基底物件來建立新的**PSObject**物件。 這個類型的基底物件表示**PSObject**物件沒有有意義的基底物件。 不過，此類型為基底物件的**PSObject**物件確實提供了屬性包，Cmdlet 開發人員可以藉由新增擴充成員來尋找有用的功能。

開發人員也可以指定物件類型名稱，讓這個物件可以與相同類型名稱的其他**PSObject**物件共用其擴充成員。

- 呼叫**PSObject** . #ctor (system.object) 的函式會使用 system.object 類型的基底物件來建立新的**PSObject**物件。

  在此情況下，所建立物件的類型名稱是基底物件之衍生階層的集合。 例如，包含 ProcessInfo 基底物件之**PSObject**的類型名稱會包含下列名稱：

  - System.Diagnostics.Process
  - System.workflow.componentmodel.activity 元件
  - System.MarshalByRefObject
  - System.Object

- 呼叫**PSObject** 。AsPSObject (System.object) 方法會根據提供的物件建立新的**PSObject**物件。

  如果提供的物件為 System.object 類型，則會使用提供的物件做為新**PSObject**物件的基底物件。 如果提供的物件已經是**PSObject**物件，則提供的物件會以 is 的方式傳回。

### <a name="base-adapted-and-extended-members"></a>Base、改編和擴充成員

在概念上，ETS 會使用下列詞彙來顯示基底物件的原始成員與 PowerShell 新增的成員之間的關聯性。 如需**PSObject**物件所使用之特定成員類型的詳細資訊，請參閱[psobject 類別](/dotnet/api/system.management.automation.psobject)。

#### <a name="base-object-members"></a>基底物件成員

如果在建立**PSObject**物件時指定了基底物件，則會透過 members 屬性來提供基底物件的成員。

#### <a name="adapted-members"></a>改編的成員

當基底物件是中繼物件時，其中一個會以一般的方式包含資料，而其屬性「描述」其包含的資料，ETS 會將這些物件調整為可透過調整的**PSObject**物件成員直接存取資料的視圖。 調整的成員和基底物件成員是透過 Members 屬性來存取。

#### <a name="extended-members"></a>擴充成員

除了從基底物件或由 PowerShell 所建立的調整成員所提供的成員之外， **PSObject**也可以定義擴充成員，以擴充原始的基底物件，以及在腳本環境中有用的其他資訊。

例如，PowerShell 提供的所有核心 Cmdlet （例如 Get-Content 和 Set-Content Cmdlet）都會採用 path 參數。 為了確保這些指令程式和其他 Cmdlet 可以處理不同類型的物件，可以將路徑成員新增至這些物件，使其以一般方式將其資訊全部陳述。 這個擴充路徑成員可確保 Cmdlet 可以針對所有類型執行，即使基類可能沒有路徑成員也一樣。

擴充的成員、調整的成員和基底物件成員都是透過 Members 屬性來存取。
