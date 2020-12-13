---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統中的錯誤和例外狀況
description: 擴充類型系統中的錯誤和例外狀況
ms.openlocfilehash: 295c16ad9abb67b0c4967bf32125bfc7ee0a35da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652478"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>擴充類型系統中的錯誤和例外狀況

在初始化類型資料時，以及存取 **PSObject** 物件的成員或使用其中一個公用程式類別（例如 **languageprimitives.physicalequality**）時，ETS 中可能會發生錯誤。

## <a name="runtime-errors"></a>執行階段錯誤

除了一個例外狀況，轉換時，在執行時間期間從 ETS 擲回的所有例外狀況都是 **ExtendedTypeSystemException** 例外狀況或衍生自 **ExtendedTypeSystemException** 類別的例外狀況。 這可讓腳本開發人員使用其腳本中的語句來攔截這些例外狀況 `Trap` 。

## <a name="errors-getting-member-values"></a>取得成員值時發生錯誤

取得 ETS 成員的值時所發生的所有錯誤 (屬性、方法或參數化屬性) 會導致擲回 **GetValueException** 或 **GetValueInvocationException** 例外狀況。
當 ETS 辨識出發生錯誤時，就會擲回 **GetValueException** 例外狀況。 當參考成員的基礎 getter 辨識出發生錯誤時，會擲回 **GetValueInvocationException** 例外狀況，而不一定會包含造成 get 調用錯誤的內部例外狀況。

## <a name="errors-setting-member-values"></a>設定成員值時發生錯誤

當設定 ETS 屬性的值時，所發生的所有錯誤都會擲回 **SetValueException** 或 **SetValueInvocationException** 例外狀況。 當 ETS 辨識出發生錯誤時，就會擲回 **SetValueException** 例外狀況。 當參考屬性的基礎 setter 辨識出發生錯誤時，就會擲回 **SetValueInvocationException** 例外狀況，而不一定會包含造成集合調用錯誤的內部例外狀況。

## <a name="errors-invoking-a-method"></a>叫用方法時發生錯誤

叫用 ETS 方法時所發生的所有錯誤都會擲回 **MethodException** 或 **MethodInvocationException** 例外狀況。 當 ETS 辨識出發生錯誤時，就會擲回 **MethodException** 例外狀況。 當參考的方法辨識出發生錯誤時，就會擲回 **MethodInvocationException** 例外狀況，而不一定會包含導致叫用錯誤的內部例外狀況。

## <a name="casting-errors"></a>轉換錯誤

嘗試不正確轉換時，會擲回 **PSInvalidCastException** 。 因為這個例外狀況是衍生自 **InvalidCastException**，所以無法從腳本中直接將它捕捉。 請注意，嘗試轉換的實體需要將 **PSInvalidCastException** 包裝在 **PSRuntimeException** 中，如此腳本才能將其進行可捕獲。 如果嘗試設定 **PSPropertySet**、 **PSMemberSet**、 **PSMethodInfo** 或 **ReadOnlyPSMemberInfoCollection ' 1** 的成員值，則會擲回 **NotSupportedException** 。

## <a name="common-runtime-errors"></a>常見的執行階段錯誤

任何其他發生的常見執行階段錯誤都屬於類型 **ExtendedTypeSystemException** 例外狀況，而且沒有其他特定的例外狀況類型。

## <a name="initialization-errors"></a>初始化錯誤

初始化時可能會發生錯誤 `types.ps1xml` 。 一般而言，這些錯誤會在 PowerShell 執行時間啟動時顯示。 不過，它們也可以在載入模組時顯示。
