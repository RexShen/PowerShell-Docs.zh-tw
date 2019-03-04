---
title: 如何建立主控台 Shell |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853494"
---
# <a name="how-to-create-a-console-shell"></a>如何建立主控台殼層

Windows PowerShell 提供讓殼層的工具，也稱為 「 請-套件 」，用來建立不是可延伸的主控台介面。 使用這項新工具建立的殼層無法稍後再擴充，透過 Windows PowerShell 嵌入式管理單元。

## <a name="syntax"></a>語法

以下是用來執行從讓殼層內讓檔案的語法。

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>參數

以下是讓殼層參數的簡短描述。

> [!CAUTION]
> 請 Shell 不支援 UNC 路徑，組件。

|參數|描述|
|---------------|-----------------|
|-out n.exe|必要。 產生介面名稱。 指定的路徑，此參數的一部分。<br /><br /> 讓殼層將會附加".exe"，此值，如果未指定。 **注意：** 具有相同名稱與參考的.dll 檔建立的輸出檔。 如果您嘗試這麼做，請殼層工具會建立.cs 檔案具有相同名稱，將會覆寫的.cs 檔案中包含您指令程式的原始程式碼。|
|命名空間 ns|必要。 要用於 衍生的命名空間[System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration)讓套件產生和編譯的類別。|
|-lib libdirectory1[,libdirectory2,..]|.NET 組件，包括 Windows PowerShell 組件，這是所指定的組件中搜尋的目錄`reference`參數、 組件的間接參考的另一個組件和.NET system 組件。|
|-reference ca1.dll[,ca2.dll,...]|要包含在殼層中的組件以逗號分隔清單。 這些組件包含所有 cmdlet 和提供者組件，以及應該載入的資源組件。 如果未指定此參數，然後在殼層會產生包含只有核心 cmdlet 與 Windows PowerShell 所提供的提供者。<br /><br /> 您可以使用其完整路徑指定的組件，否則搜尋使用指定的路徑`lib`參數。|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|要包含在殼層中的格式化資料的逗號分隔清單。 如果未指定此參數，然後在殼層會產生包含只有 Windows PowerShell 所提供的格式資料。|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|在殼層中包含的資料類型以逗號分隔清單。 如果未指定此參數，然後在殼層會產生包含只有 Windows PowerShell 所提供的型別資料。|
|-source c1.cs [,c2.cs,...]|提供 shell 開發人員，包含所有建置命令介面所需的原始程式碼的檔案名稱。<br /><br /> 原始程式碼檔可以包含任何下列原始程式碼：<br /><br /> -覆寫預設授權管理員的授權管理員實作。 （這可能也會提供編譯的組件。）<br />組件參考的屬性宣告： 例如 AssemblyCompanyAttribute、 AssemblyCopyrightAttribute、 AssemblyFileVersionAttribute、 AssemblyInformationalVersionAttribute、 AssemblyProductAttribute，及AssemblyTrademarkAttribute。|
|-authorizationmanager authorizationManagerType|包含授權管理員實作的型別。 這可以是定義在原始程式碼中，或編譯的組件 (藉由指定`reference`參數)。 如果未指定此參數，則會使用預設安全性管理員。 值應該是完整類型名稱，包括命名空間。|
|-win32icon i.ico|.Exe 檔案，shell 圖示。 如果未指定，殼層將會有 c# 編譯器包含 （如果有的話） 圖示。|
|-initscript p.ps1|殼層啟動設定檔。 檔案會包含"作為-是";沒有驗證檢查，即可讓殼層。|
|-builtinscript s1.ps1[,s2.ps1,...]|殼層的內建指令碼的清單。 這些指令碼會探索之前，路徑中的指令碼，並建置殼層後，就無法變更其內容。<br /><br /> 檔案會包含在 「 為-是";沒有驗證檢查，即可讓殼層。|
|-資源 resourcefile.txt|在.txt 檔案，其中包含說明及橫幅 shell 的資源。 第一個資源名為 ShellHelp，並包含與叫用殼層時所顯示的文字`help`參數。 第二個資源為 ShellBanner，，其中包含文字和在互動模式中啟動殼層時顯示的著作權資訊。<br /><br /> 如果未提供這個參數，或這些資源不存在，則一般的說明和橫幅會使用。|
|-cscflags cscFlags|旗標，應傳遞至C#編譯器 (csc.exe)。 這些都會通過不變。 如果此參數包含空格，則它應該用雙引號括住。|
|-?<br /><br /> -help|顯示著作權訊息和讓殼層命令列選項。|
|-verbose|建立殼層時，顯示詳細資訊。|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)