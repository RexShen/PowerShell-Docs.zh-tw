---
title: Cmdlet 動態參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369877"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet 動態參數

Cmdlet 可以定義使用者在特殊條件下可用的參數，例如當另一個參數的引數為特定值時。 這些參數會在執行時間加入，並稱為動態參數，因為只有在需要時才會新增這些參數。 例如，您可以設計一個 Cmdlet，只在指定了特定的切換參數時，才會新增數個參數。

> [!NOTE]
> 提供者和 PowerShell 函數也可以定義動態參數。

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>PowerShell Cmdlet 中的動態參數

PowerShell 會在其多個提供者 Cmdlet 中使用動態參數。 例如，當**Path**參數指定**憑證**提供者路徑時，`Get-Item` 和 `Get-ChildItem` Cmdlet 會在執行時間新增**CodeSigningCert**參數。 如果**path**參數指定不同提供者的路徑，則無法使用**CodeSigningCert**參數。

下列範例顯示在執行 `Get-Item` 時，如何在執行時間新增**CodeSigningCert**參數。

在此範例中，PowerShell 執行時間已新增參數，且 Cmdlet 成功。

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

在此範例中，指定了**FileSystem**磁片磁碟機，並傳回錯誤。 錯誤訊息指出找不到**CodeSigningCert**參數。

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>支援動態參數

若要支援動態參數，Cmdlet 程式碼中必須包含下列元素。

### <a name="interface"></a>介面

[IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)。
這個介面提供可抓取動態參數的方法。

例如：

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>方法

[IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)。
這個方法會抓取包含動態參數定義的物件。

例如：

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

### <a name="class"></a>類別

定義要加入之動態參數的類別。 此類別必須包含每個參數的**參數**屬性，以及 Cmdlet 所需的任何選擇性**別名**和**驗證**屬性。

例如：

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

如需支援動態參數之 Cmdlet 的完整範例，請參閱[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)。

## <a name="see-also"></a>另請參閱

[IDynamicParameters。](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.web. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
