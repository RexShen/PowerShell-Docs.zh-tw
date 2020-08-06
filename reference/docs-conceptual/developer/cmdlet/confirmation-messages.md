---
title: 確認訊息 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8f8192f6ed96b1eeb22e3b28ce1366eee8e7c16a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782186"
---
# <a name="confirmation-messages"></a>確認訊息

以下是不同的確認訊息，可以根據所呼叫的[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的變體來顯示這些資訊，以供您看到。

> [!IMPORTANT]
> 如需說明如何要求確認的範例程式碼，請參閱[如何要求確認](./how-to-request-confirmations.md)。

## <a name="specifying-the-resource"></a>指定資源

您可以藉由呼叫[Shouldprocess% 2a 來指定即將變更的資源，然後使用。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在此情況下，您會使用方法的參數來提供資源 `target` ，而此作業是由 Windows PowerShell 新增。 在下列訊息中，"MyResource" 文字是要處理的資源，而作業則是進行呼叫的命令名稱。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果使用者在確認要求中選取 **[是]** 或 **[全部皆是]** (如下列範例) 所示，則會呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，這會導致第二個確認訊息顯示。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>指定作業和資源

您可以藉由呼叫[Shouldprocess% 2a？來指定即將變更的資源，以及命令即將執行的作業，以進行操作。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。 在這種情況下，您可以使用參數和作業來提供資源， `target` 方法是使用 `target` 參數。 在下列訊息中，文字 "MyResource" 是所處理的資源，而 "MyAction" 是要執行的作業。

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果使用者對先前的訊息選取 **[是]** 或 **[全部皆是]** ，就會呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，這會導致第二個確認訊息顯示。

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
