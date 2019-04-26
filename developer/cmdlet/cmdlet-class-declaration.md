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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068635"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet 類別宣告

Microsoft.NET Framework 類別，會藉由指定宣告為 cmdlet **Cmdlet**做為中繼資料類別的屬性。 ( **Cmdlet**屬性是唯一的必要的屬性，針對所有的 cmdlet)。 當您指定**Cmdlet**屬性，您必須指定可識別使用者 cmdlet 動詞和名詞 」 組。 而且，您必須描述 cmdlet 支援 Windows PowerShell 功能。 如需有關用來指定的宣告語法**Cmdlet**屬性，請參閱[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。

> [!NOTE]
> **Cmdlet**屬性由定義[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)類別。 此類別的屬性對應到宣告屬性時所使用的宣告參數。

## <a name="nouns"></a>名詞

Cmdlet 名詞會指定此 cmdlet 所處理的資源。 名詞會區分您的 cmdlet 與其他 cmdlet。

Cmdlet 名稱中的名詞必須是特有的而且在一般的名詞，例如*server*，建議您最好將簡短的前置詞不同之處來自其他類似的資源的資源。 例如，包含具有前置詞的名詞的 cmdlet 名稱是`Get-SQLServer`。 一個特定名詞與更多一般動詞命令的組合可讓使用者快速找出其動作的 cmdlet，然後依其資源識別指令程式，同時還能避免不必要的 cmdlet 名稱重複。

如需不使用 cmdlet 名稱中的特殊字元的清單，請參閱 <<c0> [ 所需的開發指導方針](./required-development-guidelines.md)。

## <a name="verbs"></a>動詞

當您指定的動詞命令時，開發指導方針會要求您使用其中一個預先定義 Windows PowerShell 所提供的指令動詞。 藉由使用其中一個這些預先定義的指令動詞，您可確保您所撰寫的 cmdlet 與 cmdlet 所撰寫，由 Microsoft 和其他項目之間的一致性。 例如，"Get"動詞命令用於擷取資料的 cmdlet。

如需詳細的指導方針的動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。 如需不使用 cmdlet 名稱中的特殊字元的清單，請參閱 <<c0> [ 所需的開發指導方針](./required-development-guidelines.md)。

## <a name="supporting-windows-powershell-functionality"></a>支援的 Windows PowerShell 功能

**Cmdlet**屬性也可讓您指定您的指令程式支援的一些常見功能所提供的 Windows PowerShell。 這包括支援常見的功能，例如使用者意見反應確認 （又稱為 ShouldProcess 功能的支援） 和交易支援。 （交易的支援是在 Windows PowerShell 2.0 中推出）。

如需有關用來指定的宣告語法**Cmdlet**屬性，請參閱[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。

## <a name="cmdlet-class-definition"></a>Cmdlet 類別定義

下列程式碼是 GetProc cmdlet 類別定義。 請注意，依照 pascal 命名法大小寫會使用與類別的名稱，包含動詞和名詞的 cmdlet。

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal 命名法大小寫

當您命名 cmdlet 時，使用 pascal 命名法大小寫。 例如，`Get-Item`和`Get-ItemProperty`cmdlet 顯示當您命名為 cmdlet 時，請使用大小寫的正確方式。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute Declaration](./cmdlet-attribute-declaration.md)

[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
