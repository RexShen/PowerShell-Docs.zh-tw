---
ms.date: 09/13/2016
ms.topic: reference
title: 如何宣告 Cmdlet 參數
description: 如何宣告 Cmdlet 參數
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667091"
---
# <a name="how-to-declare-cmdlet-parameters"></a>如何宣告 Cmdlet 參數

這些範例示範如何宣告指名的、位置、必要、選擇性和切換參數。 這些範例也會示範如何定義參數別名。

## <a name="how-to-declare-a-named-parameter"></a>如何宣告具名引數

- 定義公用屬性，如下列程式碼所示。 當您加入參數屬性時，請省略 `Position` 屬性中的關鍵字。

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-positional-parameter"></a>如何宣告位置參數

- 定義公用屬性，如下列程式碼所示。 當您加入參數屬性時，請將 `Position` 關鍵字設定為引數位置。 值為0表示第一個位置。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-mandatory-parameter"></a>如何宣告強制參數

- 定義公用屬性，如下列程式碼所示。 當您加入參數屬性時，請將 `Mandatory` 關鍵字設定為 `true` 。

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-an-optional-parameter"></a>如何宣告選擇性參數

- 定義公用屬性，如下列程式碼所示。 當您加入參數屬性時，請省略 `Mandatory` 關鍵字。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>如何宣告切換參數

- 將公用屬性定義為 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，然後宣告參數屬性。

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

如需參數屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-parameter-with-aliases"></a>如何使用別名宣告參數

- 定義公用屬性，如下列程式碼所示。 新增可列出參數別名的別名屬性。 在此範例中，會針對相同參數定義三個別名。 第一個別名提供快捷方式。 第二個和第三個別名提供可在不同案例中使用的名稱。

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需別名屬性的詳細資訊，請參閱 [別名屬性聲明](./alias-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[參數屬性宣告](./parameter-attribute-declaration.md)

[別名屬性宣告](./alias-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
