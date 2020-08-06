---
title: 擴充類型系統中的錯誤和例外狀況
ms.date: 07/09/2020
ms.openlocfilehash: f60c53e33c031168eda53726e0d296bf91139fda
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786283"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>擴充類型系統中的錯誤和例外狀況

在初始化類型資料時，以及存取**PSObject**物件的成員或使用其中一個公用程式類別（例如**languageprimitives.physicalequality**）時，ETS 可能會發生錯誤。

## <a name="runtime-errors"></a>執行階段錯誤

有一個例外狀況，在轉換時，在執行時間期間從 ETS 擲回的所有例外狀況都是**ExtendedTypeSystemException**例外狀況或衍生自**ExtendedTypeSystemException**類別的例外狀況。 這可讓腳本開發人員使用其腳本中的語句來攔截這些例外狀況 `Trap` 。

## <a name="errors-getting-member-values"></a>取得成員值時發生錯誤

取得 ETS 成員的值 (屬性、方法或參數化屬性時，所發生的所有錯誤) 會擲回**GetValueException**或**GetValueInvocationException**例外狀況。
當 ETS 辨識出錯誤發生時，就會擲回**GetValueException**例外狀況。 當參考成員的基礎 getter 辨識出錯誤時，會擲回**GetValueInvocationException**例外狀況，而不一定會包含造成 get 調用錯誤的內部例外狀況。

## <a name="errors-setting-member-values"></a>設定成員值時發生錯誤

設定 ETS 屬性的值時所發生的所有錯誤都會導致擲回**SetValueException**或**SetValueInvocationException**例外狀況。 當 ETS 辨識出錯誤發生時，就會擲回**SetValueException**例外狀況。 當所參考屬性的基礎 setter 發現發生錯誤時，會擲回**SetValueInvocationException**例外狀況，而不一定會包含造成設定調用錯誤的內部例外狀況。

## <a name="errors-invoking-a-method"></a>叫用方法時發生錯誤

叫用 ETS 方法時所發生的所有錯誤都會導致擲回**MethodException**或**MethodInvocationException**例外狀況。 當 ETS 辨識出錯誤發生時，就會擲回**MethodException**例外狀況。 當參考的方法辨識出錯誤時，會擲回**MethodInvocationException**例外狀況，而不一定會包含造成調用錯誤的內部例外狀況。

## <a name="casting-errors"></a>轉換錯誤

當嘗試不正確轉換時，就會擲回**PSInvalidCastException** 。 因為此例外狀況衍生自**InvalidCastException**，所以無法直接從腳本中攔截。 請注意，嘗試轉換的實體必須將**PSInvalidCastException**包裝在**PSRuntimeException**中，才能由腳本加以捕獲。 如果嘗試設定**PSPropertySet**、 **PSMemberSet**、 **PSMethodInfo**或**ReadOnlyPSMemberInfoCollection ' 1**成員的值，則會擲回**NotSupportedException** 。

## <a name="common-runtime-errors"></a>常見的執行階段錯誤

發生的任何其他常見執行階段錯誤都屬於類型**ExtendedTypeSystemException**例外狀況，且沒有其他特定的例外狀況類型。

## <a name="initialization-errors"></a>初始化錯誤

初始化時，可能會發生錯誤 `types.ps1xml` 。 這些錯誤通常會在 PowerShell 執行時間啟動時顯示。 不過，也可以在載入模組時顯示。
