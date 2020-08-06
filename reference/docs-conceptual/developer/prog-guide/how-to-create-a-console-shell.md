---
title: 如何建立主控台 Shell |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.openlocfilehash: 5d8231363ab804bfd7113ef69f0bdede445149a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771612"
---
# <a name="how-to-create-a-console-shell"></a>如何建立主控台殼層

Windows PowerShell 提供一個 Shell 工具（也稱為「建立套件」），可用來建立不可延伸的主控台 Shell。 使用這項新工具所建立的 shell 之後，將無法透過 Windows PowerShell 嵌入式管理單元延伸。

## <a name="syntax"></a>語法

以下是用來從檔案內執行 Make Shell 的語法。

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

以下是 Shell 參數的簡短描述。

> [!CAUTION]
> Make 命令介面不支援元件的 UNC 路徑。

|參數|描述|
|---------------|-----------------|
|-out n.exe|必要。 要產生的 shell 名稱。 此路徑會指定為此參數的一部分。<br /><br /> 如果未指定，則 Make-shell 會將 ".exe" 附加至此值。 **注意：** 請勿使用與所參考 .dll 檔案相同的名稱來建立輸出檔。 如果您嘗試這麼做，則 Shell 工具會建立具有相同名稱的 .cs 檔案，這將會覆寫具有 Cmdlet 原始程式碼的 .cs 檔案。|
|-namespace ns|必要。 要用於衍生的[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration)類別的命名空間，而此類套件會產生和編譯。|
|-lib libdirectory1 [，libdirectory2,..]|針對 .NET 元件搜尋的目錄，包括 Windows PowerShell 元件、由參數所指定的元件 `reference` 、由另一個元件間接參考的元件，以及 .net 系統元件。|
|-reference ca1.dll [，ca2.dll,...]|要包含在 shell 中的元件清單（以逗號分隔）。 這些元件包括所有 Cmdlet 和提供者元件，以及應載入的資源元件。 如果未指定此參數，則會產生 shell，其中只包含 Windows PowerShell 所提供的核心 Cmdlet 和提供者。<br /><br /> 元件可以使用其完整路徑來指定，否則會使用參數所指定的路徑進行搜尋 `lib` 。|
|-formatdata fd1.format.ps1xml [，fd2.format.ps1xml,...]|要包含在 shell 中的格式資料清單（以逗號分隔）。 如果未指定此參數，則會產生 shell，其中只包含 Windows PowerShell 所提供的格式資料。|
|-typedata td1.type.ps1xml [，td2.type.ps1xml,...]|要包含在 shell 中的類型資料清單（以逗號分隔）。 如果未指定此參數，則會產生 shell，其中只包含 Windows PowerShell 所提供的類型資料。|
|-source c1.cs [，c2.cs,...]|Shell 開發人員所提供的檔案名，其中包含建立命令介面所需的任何原始程式碼。<br /><br /> 原始程式碼檔案可以包含下列任何原始程式碼：<br /><br /> -覆寫預設授權管理員的授權管理員執行。  (也可以提供編譯成元件。 ) <br />-元件資訊屬性宣告：例如 System.reflection.assemblycompanyattribute>、System.reflection.assemblycopyrightattribute>、AssemblyFileVersionAttribute、System.reflection.assemblyinformationalversionattribute>、System.reflection.assemblyproductattribute> 和 System.reflection.assemblytrademarkattribute>。|
|-authorizationmanager authorizationManagerType|包含授權管理員執行的類型。 這可以在原始程式碼中定義，或編譯成元件 (由 `reference` 參數) 指定。 如果未指定此參數，則會使用預設的安全性管理員。 這個值應該是完整的類型名稱，包括命名空間。|
|-win32icon i .ico|Shell 之 .exe 檔案的圖示。 如果未指定，則 shell 會有 c # 編譯器包含 (（如果有任何) ）的圖示。|
|-initscript p.ps1|Shell 的啟動設定檔。 檔案包含「原樣」;不會透過 Make-Shell 來完成有效性檢查。|
|-builtinscript s1.ps1 [，s2.ps1,...]|Shell 的內建腳本清單。 這些腳本會在路徑中的腳本之前探索，而且在建立 shell 之後，就無法變更其內容。<br /><br /> 檔案會以「原樣」包含;不會透過 Make-Shell 來完成有效性檢查。|
|-資源 resourcefile.txt|包含 shell 之說明和橫幅資源的 .txt 檔案。 第一個資源的名稱是 ShellHelp，其中包含使用參數叫用 shell 時所顯示的文字 `help` 。 第二個資源的名稱是 ShellBanner，它包含在互動模式下啟動 shell 時所顯示的文字和著作權資訊。<br /><br /> 如果未提供此參數，或這些資源不存在，則會使用一般說明和橫幅。|
|-cscflags cscFlags|應該傳遞至 c # 編譯器 ( # A0) 的旗標。 這些會透過未變更的傳遞。 如果此參數包含空格，則應以雙引號括住。|
|-?<br /><br /> -help|顯示著作權訊息和 Make Shell 命令列選項。|
|-verbose|會在建立 shell 時顯示詳細資訊。|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
