---
title: 確認訊息 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861414"
---
# <a name="confirmation-messages"></a>確認訊息

以下是不同的確認訊息，可以顯示不同的變化[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)呼叫的方法。

> [!IMPORTANT]
> 示範如何要求確認的範例程式碼，請參閱[如何要求確認](./how-to-request-confirmations.md)。

## <a name="specifying-the-resource"></a>指定資源

您可以指定的資源，藉由呼叫即將變更[System.Management.Automation.Cmdlet.Shouldprocess%2A 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在此情況下，您提供資源使用`target`方法，以及作業的參數已加入 Windows powershell。 在下列的訊息中，「 MyResource 」 的文字是採取行動的資源，而且作業是發出呼叫的命令名稱。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果使用者選取 **[是]** 或**全部**若要確認要求 （如所示在下列範例中），呼叫[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法為止，這會導致要顯示的第二個確認訊息。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>指定的作業和資源

您可以指定是即將變更的資源和作業的命令即將執行的呼叫[System.Management.Automation.Cmdlet.Shouldprocess%2A 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在此情況下，您使用提供的資源時`target`參數和使用作業`target`參數。 在下列訊息: 「 MyResource 」 的文字是採取行動的資源，「 MyAction 」 是要執行的作業。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果使用者選取 **[是]** 或是**全部**至上一個訊息，也就是呼叫[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法進行時，會造成第二個要顯示的確認訊息。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
