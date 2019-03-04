---
title: Cmdlet 的動態參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853804"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet 動態參數

Cmdlet 可以定義參數，例如，當另一個參數的引數為特定值的特殊情況下，使用者可以使用。 這些參數會加入在執行階段，並稱為*動態參數*因為只在需要時才新增。 比方說，您可以設計一個特定的切換參數指定時，才會將數個參數加入 cmdlet。

> [!NOTE]
> 提供者和 Windows PowerShell 函式也可以定義的動態參數。

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet 中的動態參數

Windows PowerShell 會使用動態參數，在數個提供者 cmdlet。 例如，`Get-Item`並`Get-ChildItem`cmdlet 新增`CodeSigningCert`參數在執行階段時`Path`指令程式參數指定的憑證提供者路徑。 如果`Path`指令程式參數指定的路徑為不同的提供者，`CodeSigningCert`參數不是可用。

下列範例會顯示如何`CodeSigningCert`參數會加入在執行階段時`Get-Item`執行 cmdlet。

在第一個範例中，Windows PowerShell 執行階段已新增參數，且此 cmdlet 成功。

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

在第二個範例中，指定檔案系統磁碟機，而且會傳回錯誤。 錯誤訊息表示`CodeSigningCert`找不到參數。

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>動態參數的支援

若要支援的動態參數，cmdlet 程式碼必須包含下列項目。

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)這個介面會提供擷取動態參數的方法。

範例：

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)這個方法會擷取包含的動態參數定義的物件。

範例：

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

動態參數類別此類別會定義要加入的參數。 這個類別必須包含每個參數以及此指令程式所需的任何選擇性別名和驗證屬性的參數屬性。

範例：

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

支援動態參數的 cmdlet 的完整範例，請參閱 <<c0> [ 宣告的動態參數如何](./how-to-declare-dynamic-parameters.md)。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
