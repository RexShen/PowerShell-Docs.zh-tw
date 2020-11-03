---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203587"
---
# New-WebServiceProxy

## 概要
建立 Web 服務 proxy 物件，可讓您使用和管理 PowerShell 中的 Web 服務。

## SYNTAX

### NoCredentials (預設值)

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### 認證

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### UseDefaultCredential

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## DESCRIPTION

此 `New-WebServiceProxy` Cmdlet 可讓您在 PowerShell 中使用 Web 服務。 此 Cmdlet 會連線到 Web 服務，並在 PowerShell 中建立 Web 服務 proxy 物件。 您可以使用 Proxy 物件來管理 Web 服務。

Web 服務是以 XML 為基礎的程式，可透過網路（尤其是透過網際網路）交換資料。 Microsoft .NET Framework 提供 Web 服務 Proxy 物件，這些物件會以 .NET Framework 物件代表 Web 服務。

## 範例

### 範例1：建立 Web 服務的 proxy

此範例會在 Windows PowerShell 中建立 .NET Framework 的計算機 Web 服務 proxy。

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### 範例2：建立 Web 服務的 proxy 並指定命名空間和類別

這個範例會使用 `New-WebServiceProxy` Cmdlet 來建立 .NET Framework 的計算機 Web 服務 proxy。

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

此命令會使用 **uri** 參數來指定 Uri 以及 **命名空間** 和 **類別** 參數，以指定物件的命名空間和類別。

### 範例3：顯示 Web 服務 proxy 的方法

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

此範例會使用 `Get-Member` Cmdlet 來顯示變數中 Web 服務 proxy 物件的方法 `$calc` 。 我們會在下列範例中使用這些方法。

請注意，proxy 物件的 **TypeName** （WebServiceProxy）會反映先前範例中所指定的命名空間和類別名稱。

### 範例4：使用 Web 服務 proxy

```powershell
PS> $calc.Multiply(6,7)
42
```

此範例會使用儲存在變數中的 Web 服務 proxy `$calc` 。 此命令會使用 proxy 的 **乘法** 方法。

## PARAMETERS

### -Class

指定 Cmdlet 為 Web 服務建立之 Proxy 類別的名稱。 此參數的值會與 **Namespace** 參數一起使用，以提供類別的完整名稱。 預設值是從統一資源識別項 (URI) 產生。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。 這可做為使用 **UseDefaultCredential** 參數的替代方案。

輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

指定新類別的命名空間。

這個參數的值會和 **class** 參數的值一起使用，以產生類別的完整名稱。 預設值為 **microsoft.powershell.commands.newwebserviceproxy.autogeneratedtypes. microsoft.powershell.commands.addtype.autogeneratedtypes** ，再加上從 URI 產生的類型。

您可以設定 **Namespace** 參數的值，讓您可以存取多個同名的 Web 服務。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uri

指定 Web 服務的 URI。 輸入 URI 或包含服務描述之檔案的路徑和檔案名。

URI 必須傳回 `.asmx` 頁面或傳回服務描述的頁面。 若要傳回使用 ASP.NET 建立之 Web 服務的服務描述，請附加 "？WSDL」至 Web 服務的 URL (例如 `http://www.contoso.com/MyWebService.asmx?WSDL`) 。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredential

指出此 Cmdlet 會使用預設認證。 此 Cmdlet 會將產生之 proxy 物件中的 **UseDefaultCredential** 屬性設定為 True。 這可做為使用 **Credential** 參數的替代方案。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Web 服務 Proxy 物件

此 Cmdlet 會傳回 Web 服務 proxy 物件。 物件的命名空間和類別取決於命令的參數。 預設值是從輸入 URI 產生的。

## 注意

`New-WebServiceProxy` 使用 **系統 .net. WebClient** 類別來載入指定的 Web 服務。

## 相關連結

[New-Service](New-Service.md)
