---
title: 如何宣告 Cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365677"
---
# <a name="how-to-declare-cmdlet-parameters"></a>如何宣告 Cmdlet 參數

這些範例示範如何宣告指名的、位置、必要、選擇性和切換參數。 這些範例也會示範如何定義參數別名。

## <a name="how-to-declare-a-named-parameter"></a>如何宣告具名引數

- 定義公用屬性，如下列程式碼所示。 當您新增參數屬性時，請省略屬性中的 `Position` 關鍵字。

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

## <a name="how-to-declare-a-positional-parameter"></a>如何宣告位置參數

- 定義公用屬性，如下列程式碼所示。 當您新增參數屬性時，請將 `Position` 關鍵字設定為引數位置。 值為0表示第一個位置。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

## <a name="how-to-declare-a-mandatory-parameter"></a>如何宣告強制參數

- 定義公用屬性，如下列程式碼所示。 當您新增參數屬性時，請將 `Mandatory` 關鍵字設定為 `true`。

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

## <a name="how-to-declare-an-optional-parameter"></a>如何宣告選擇性參數

- 定義公用屬性，如下列程式碼所示。 當您新增參數屬性時，請省略 `Mandatory` 關鍵字。

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

- 將公用屬性定義為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，然後宣告參數屬性。

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

如需參數屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

## <a name="how-to-declare-a-parameter-with-aliases"></a>如何宣告具有別名的參數

- 定義公用屬性，如下列程式碼所示。 新增別名屬性，其中列出參數的別名。 在此範例中，會為相同的參數定義三個別名。 第一個別名提供快捷方式。 第二個和第三個別名提供可用於不同案例的名稱。

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

如需 Alias 屬性的詳細資訊，請參閱[Alias 屬性](./alias-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[SwitchParameter。](/dotnet/api/System.Management.Automation.SwitchParameter)

[參數屬性宣告](./parameter-attribute-declaration.md)

[Alias 屬性宣告](./alias-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
