---
ms.date: 09/13/2016
ms.topic: reference
title: 確認訊息
description: 確認訊息
ms.openlocfilehash: 76302b2f8d8ca6dcdfe1b3c36f71aad23a53f7cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355182"
---
# <a name="confirmation-messages"></a>確認訊息

以下是不同的確認訊息，這些訊息會根據所呼叫的 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的變異數而顯示出來，如下所示。

> [!IMPORTANT]
> 如需顯示如何要求確認的範例程式碼，請參閱 [如何要求確認](./how-to-request-confirmations.md)。

## <a name="specifying-the-resource"></a>指定資源

您可以藉由呼叫 [Shouldprocess% 2a 來指定即將變更的資源，而不需要變更資源。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法。 在此情況下，您會使用方法的參數來提供資源 `target` ，而作業會由 Windows PowerShell 加入。 在下列訊息中，文字 "MyResource" 是處理的資源，而作業則是發出呼叫的命令名稱。

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果使用者選取 [ **是]** 或 [ **全部]** 至確認要求 (如下列範例) 所示，則會呼叫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，這會導致第二個確認訊息顯示。

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>指定作業和資源

您可以藉由呼叫 Shouldprocess% 2A 來指定即將變更的資源，以及該命令即將執行的 [作業？（System。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法。 在此情況下，您可以使用參數 `target` ，並使用參數來提供資源 `target` 。 在下列訊息中，文字 "MyResource" 是所採取的資源，而 "MyAction" 是要執行的作業。

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

如果使用者選取 [ **是]** 或 [ **全部]** 至先前的訊息，則會呼叫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，這會導致第二個確認訊息顯示。

```Output
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
