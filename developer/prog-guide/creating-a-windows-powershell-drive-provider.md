---
title: 建立 Windows PowerShell 磁碟機提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055643"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>建立 Windows PowerShell 磁碟機提供者

本主題描述如何建立可用來存取資料存放區，透過 Windows PowerShell 磁碟機的 Windows PowerShell 磁碟機提供者。 這種類型的提供者也稱為 Windows PowerShell 磁碟機提供者。 提供者所使用的 Windows PowerShell 磁碟機提供方法來連線到資料存放區。

此處所述的 Windows PowerShell 磁碟機提供者會提供 Microsoft Access 資料庫的存取權。 此提供者，Windows PowerShell 磁碟機代表資料庫 （您可將任意數目的磁碟機新增至磁碟機提供者），磁碟機的最上層容器代表在資料庫中，資料表和容器的項目代表的資料列資料表中。

以下是本主題中的區段清單。 如果您不熟悉如何撰寫 Windows PowerShell 磁碟機提供者，閱讀這些章節中出現的順序。 不過，如果您已熟悉撰寫磁碟機提供者，請直接前往您所需要的資訊。

- [定義 Windows PowerShell 提供者類別](#Defining-the-Windows-PowerShell-Provider-Class)

- [定義基底的功能](#Defining-Base-Functionality)

- [建立磁碟機狀態資訊](#Creating-Drive-State-Information)

- [建立磁碟機](#Creating-a-Drive)

- [將動態參數附加至 NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [移除磁碟機](#Removing-a-Drive)

- [初始化的預設磁碟機](#Initializing-Default-Drives)

- [程式碼範例](#Code-Sample)

- [測試 Windows PowerShell 磁碟機提供者](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>定義 Windows PowerShell 提供者類別

您的磁碟機提供者必須定義衍生自.NET 類別[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。 以下是此磁碟機提供者的類別定義：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

請注意，在此範例中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性指定的提供者和 Windows PowerShell 的特定功能的使用者易記名稱，提供者命令處理期間，Windows PowerShell 執行階段會公開。 所定義的提供者功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 此磁碟機提供者不支援任何這些功能。

## <a name="defining-base-functionality"></a>定義基底的功能

中所述[設計您 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別衍生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別，定義所需的初始化和未初始化的提供者的方法。 若要實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者 （包括此處所述的提供者） 可以使用這項功能所提供的 Windows PowerShell 的預設實作。

## <a name="creating-drive-state-information"></a>建立磁碟機狀態資訊

所有 Windows PowerShell 提供者會被都視為無狀態，這表示您的磁碟機提供者，必須建立呼叫您的提供者時，會將 Windows PowerShell 執行階段所需的任何狀態資訊。

此磁碟機提供者、 狀態資訊會包含做為一部分的磁碟機資訊會保留資料庫的連接。 以下是示範如何將這項資訊儲存在程式碼[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)描述磁碟機的物件：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>建立磁碟機

若要讓 Windows PowerShell 執行階段建立的磁碟機，磁碟機提供者必須實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。 下列程式碼示範實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)此磁碟機提供者的方法：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

這個方法的覆寫應該執行下列作業：

- 確認[System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)成員存在，而且可以建立連接到資料存放區。

- 建立磁碟機，並填入連接成員支援`New-PSDrive`cmdlet。

- 驗證[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)建議的磁碟機的物件。

- 修改[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件，描述與任何必要的效能或可靠性的詳細資訊，磁碟機，或呼叫端使用的磁碟機提供額外的資料。

- 處理使用的失敗[System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，然後傳回`null`。

  這個方法傳回的磁碟機資訊傳遞至方法或它的提供者特定版本。

## <a name="attaching-dynamic-parameters-to-newdrive"></a>將動態參數附加至 NewDrive

`New-PSDrive`您磁碟機提供者所支援的 cmdlet 可能會需要額外的參數。 若要將這些動態參數附加至 cmdlet，提供者會實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。 這個方法會傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。

此磁碟機提供者不會覆寫這個方法。 不過，下列程式碼會顯示這個方法的預設實作：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>移除磁碟機

若要關閉資料庫連接，磁碟機提供者必須實作[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。 這個方法會關閉磁碟機的連線之後清除任何提供者專屬資訊。

下列程式碼示範實作[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)此磁碟機提供者的方法：

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

如果可以移除磁碟機，這個方法應傳回的資訊傳遞給方法，透過`drive`參數。 如果無法移除磁碟機，方法應該撰寫例外狀況，並傳回`null`。 如果您的提供者不會覆寫這個方法，則這個方法的預設實作只會傳回做為輸入傳遞的磁碟機資訊。

## <a name="initializing-default-drives"></a>初始化的預設磁碟機

您的磁碟機提供者會實作[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法來掛接磁碟機。 例如，Active Directory 提供者可能會掛接磁碟機，預設命名內容，如果電腦已加入網域。

這個方法會傳回初始化的磁碟機的磁碟機資訊的集合則為空集合。 呼叫此方法會在 Windows PowerShell 執行階段會呼叫後[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者。

此磁碟機提供者不會覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。 不過，下列程式碼會顯示預設的實作，它會傳回空的磁碟機的集合：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>有關實作 InitializeDefaultDrives 的注意事項

所有的磁碟機提供者應該裝載的根磁碟機，以協助使用者使用可搜尋性。 根磁碟機可能會列出，做為其他已掛接的磁碟機的根位置。 例如，Active Directory 提供者可能會建立列出命名內容中找到的磁碟機`namingContext`根目錄分散式系統環境 (DSE) 上的屬性。 這可協助使用者探索的其他磁碟機的掛接點。

## <a name="code-sample"></a>程式碼範例

完整的範例程式碼，請參閱[AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md)。

## <a name="testing-the-windows-powershell-drive-provider"></a>測試 Windows PowerShell 磁碟機提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以在命令列，包括任何衍生所提供的指令程式上執行支援的 cmdlet 來進行測試。 我們來測試範例磁碟機提供者。

1. 執行`Get-PSProvider`cmdlet 來擷取確保 AccessDB 磁碟機提供者的提供者清單：

   **PS> `Get-PSProvider`**

   會出現下列輸出：

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. 請確認資料庫伺服器名稱 (DSN) 資料庫中存在的存取**資料來源**一部分**系統管理工具**作業系統。 在 **使用者 DSN**資料表中，按兩下**MS Access 資料庫**，然後將磁碟機路徑 C:\ps\northwind.mdb。

3. 建立新的磁碟機，使用範例磁碟機提供者：

   **PS > 新 psdrive-名稱 mydb-根 c:\ps\northwind.mdb psprovider AccessDb**

   會出現下列輸出：

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. 驗證連線。 因為連接定義為磁碟機的成員，您可以檢查使用 Get PDDrive cmdlet。

   > [!NOTE]
   > 因為提供者為該互動需要容器的功能，使用者無法還會與做為磁碟機中，提供者互動。 如需詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

   **PS > (get psdrive mydb).connection**

   會出現下列輸出：

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. 移除磁碟機，並結束 shell:

   **PS > 移除 psdrive mydb**

   **PS > 結束**

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)