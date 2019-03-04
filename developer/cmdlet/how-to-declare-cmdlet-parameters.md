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
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861394"
---
# <a name="how-to-declare-cmdlet-parameters"></a>如何宣告 Cmdlet 參數

這些範例示範如何宣告具名、 位置、 必要、 選擇性的以及切換參數。 這些範例也顯示如何定義參數的別名。

## <a name="how-to-declare-a-named-parameter"></a>如何宣告具名的參數

- 定義的公用屬性，如下列程式碼所示。 當您新增的參數屬性時，略過`Position`關鍵字的屬性。

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-positional-parameter"></a>如何宣告位置參數

- 定義的公用屬性，如下列程式碼所示。 當您新增的參數屬性時，設定`Position`關鍵字引數位置。 值為 0 表示第一個位置。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-mandatory-parameter"></a>如何宣告的必要參數

- 定義的公用屬性，如下列程式碼所示。 當您新增的參數屬性時，設定`Mandatory`關鍵字來`true`。

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-an-optional-parameter"></a>如何宣告選擇性參數

- 定義的公用屬性，如下列程式碼所示。 當您新增的參數屬性時，略過`Mandatory`關鍵字。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>如何宣告參數的參數

- 定義的公用屬性，為型別[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)，然後將宣告參數屬性。

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

如需參數屬性的詳細資訊，請參閱[參數的屬性宣告](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-parameter-with-aliases"></a>如何宣告具有別名的參數

- 定義的公用屬性，如下列程式碼所示。 新增別名屬性，其中列出參數的別名。 在此範例中，針對相同的參數定義三個別名。 第一個別名提供捷徑。 第二個和第三個別名會提供您可以針對不同的案例中使用的名稱。

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

如需別名屬性的詳細資訊，請參閱[別名屬性宣告](./alias-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[參數屬性宣告](./parameter-attribute-declaration.md)

[別名屬性宣告](./alias-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
