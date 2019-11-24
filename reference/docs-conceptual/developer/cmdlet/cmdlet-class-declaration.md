---
title: Cmdlet 類別宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363517"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet 類別宣告

Microsoft .NET Framework 類別會將**Cmdlet**屬性指定為類別的中繼資料，以宣告為 Cmdlet。 （ **Cmdlet**屬性是所有 Cmdlet 的唯一必要屬性）。 當您指定**Cmdlet**屬性時，您必須指定指示 Cmdlet 給使用者的動詞和名詞配對。 而且，您必須描述 Cmdlet 支援的 Windows PowerShell 功能。 如需用來指定**Cmdlet**屬性之宣告語法的詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。

> [!NOTE]
> **Cmdlet**屬性是由[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)類別所定義。 這個類別的屬性會對應至宣告屬性時所使用的宣告參數。

## <a name="nouns"></a>名詞

Cmdlet 的名詞會指定 Cmdlet 作用所在的資源。 名詞會區分您的 Cmdlet 與其他 Cmdlet。

Cmdlet 名稱中的名詞必須是特定的，而且在一般名詞（例如*伺服器*）的情況下，最好是新增簡短的前置詞，以區分您的資源與其他類似的資源。 例如，包含具有前置詞之名詞的 Cmdlet 名稱是 `Get-SQLServer`。 具有較通用動詞的特定名片語合，可讓使用者快速地依其動作尋找 Cmdlet，然後依其資源識別 Cmdlet，同時避免不必要的 Cmdlet 名稱重複。

如需無法在 Cmdlet 名稱中使用的特殊字元清單，請參閱[必要的開發指導方針](./required-development-guidelines.md)。

## <a name="verbs"></a>動詞

當您指定動詞時，開發指導方針會要求您使用 Windows PowerShell 所提供的其中一個預先定義動詞命令。 藉由使用其中一個預先定義的動詞，您將可確保您撰寫的 Cmdlet 與由 Microsoft 和其他人撰寫的 Cmdlet 之間的一致性。 例如，「Get」動詞用於抓取資料的 Cmdlet。

如需動詞指導方針的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。 如需無法在 Cmdlet 名稱中使用的特殊字元清單，請參閱[必要的開發指導方針](./required-development-guidelines.md)。

## <a name="supporting-windows-powershell-functionality"></a>支援 Windows PowerShell 功能

**Cmdlet**屬性也可讓您指定您的 Cmdlet 支援 Windows PowerShell 所提供的一些常見功能。 這包括對一般功能的支援，例如使用者意見確認（稱為 ShouldProcess 功能的支援）和交易支援。 （Windows PowerShell 2.0 中引進了交易的支援）。

如需用來指定**Cmdlet**屬性之宣告語法的詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。

## <a name="cmdlet-class-definition"></a>Cmdlet 類別定義

下列程式碼是 GetProc Cmdlet 類別的定義。 請注意，使用 Pascal 大小寫，且類別的名稱包含 Cmdlet 的動詞和名詞。

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal 大小寫

當您命名 Cmdlet 時，請使用 Pascal 大小寫。 例如，當您命名 Cmdlet 時，`Get-Item` 和 `Get-ItemProperty` Cmdlet 會顯示使用大小寫的正確方式。

## <a name="see-also"></a>另請參閱

[CmdletAttribute。](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute 宣告](./cmdlet-attribute-declaration.md)

[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
