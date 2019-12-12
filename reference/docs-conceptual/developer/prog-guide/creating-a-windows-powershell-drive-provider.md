---
title: 建立 Windows PowerShell 磁片磁碟機提供者 |Microsoft Docs
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
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366827"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>建立 Windows PowerShell 磁碟機提供者

本主題說明如何建立 Windows PowerShell 磁片磁碟機提供者，以提供透過 Windows PowerShell 磁片磁碟機存取資料存放區的方式。 這種類型的提供者也稱為 Windows PowerShell 磁片磁碟機提供者。 提供者所使用的 Windows PowerShell 磁片磁碟機提供連接到資料存放區的方法。

這裡所述的 Windows PowerShell 磁片磁碟機提供者可讓您存取 Microsoft Access 資料庫。 對於此提供者，Windows PowerShell 磁片磁碟機代表資料庫（可以將任意數目的磁片磁碟機新增至磁片磁碟機提供者）、磁片磁碟機的最上層容器代表資料庫中的資料表，而容器的專案則代表中的資料列資料表。

## <a name="defining-the-windows-powershell-provider-class"></a>定義 Windows PowerShell 提供者類別

您的磁片磁碟機提供者必須定義一個衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的 .net 類別。 以下是此磁片磁碟機提供者的類別定義：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

請注意，在此範例中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性會指定提供者的使用者易記名稱，以及提供者在命令處理期間公開給 windows powershell 執行時間的 windows powershell 特定功能。 提供者功能的可能值是由[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉所定義。 此磁片磁碟機提供者不支援任何這些功能。

## <a name="defining-base-functionality"></a>定義基本功能

如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基類，此類別定義了初始化和取消初始化提供者所需的方法。 若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。 不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。

## <a name="creating-drive-state-information"></a>建立磁片磁碟機狀態資訊

所有 Windows PowerShell 提供者都會被視為無狀態，這表示您的磁片磁碟機提供者需要在呼叫提供者時，建立 Windows PowerShell 執行時間所需的任何狀態資訊。

對於此磁片磁碟機提供者，狀態資訊會包含與資料庫的連接，並保留為磁片磁碟機資訊的一部分。 以下程式碼顯示如何將這項資訊儲存在描述磁片磁碟機的[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件中：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>建立磁片磁碟機

若要允許 Windows PowerShell 執行時間建立磁片磁碟機，磁片磁碟機提供者必須執行[DriveCmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。 下列程式碼顯示此磁片磁碟機提供者的[DriveCmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法的執行：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

您的此方法的覆寫應執行下列動作：

- 確認[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)的成員存在，而且可以建立與資料存放區之間的連接。」

- 建立磁片磁碟機並填入連接成員，以支援 `New-PSDrive` Cmdlet。

- 驗證所提議磁片磁碟機的[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件。

- 修改[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件，以描述具有任何必要效能或可靠性資訊的磁片磁碟機，或為使用磁片磁碟機的呼叫端提供額外的資料。

- 使用[Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法來處理失敗，然後傳回 `null`。

  這個方法會傳回傳遞給方法的磁片磁碟機資訊，或它的提供者特定版本。

## <a name="attaching-dynamic-parameters-to-newdrive"></a>將動態參數附加至 NewDrive

您的磁片磁碟機提供者所支援的 `New-PSDrive` Cmdlet 可能需要額外的參數。 若要將這些動態參數附加至 Cmdlet，提供者會執行[DriveCmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。 這個方法會傳回物件，其中具有屬性和欄位，而且其具有類似于 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。

此磁片磁碟機提供者不會覆寫此方法。 不過，下列程式碼會顯示此方法的預設執行：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>移除磁片磁碟機

若要關閉資料庫連接，磁片磁碟機提供者必須執行[DriveCmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。 這個方法會在清除任何提供者特定的資訊之後，關閉與磁片磁碟機的連接。

下列程式碼顯示此磁片磁碟機提供者的[DriveCmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法的執行：

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

如果可以移除磁片磁碟機，方法應該會透過 `drive` 參數傳回傳遞給方法的資訊。 如果無法移除磁片磁碟機，方法應該撰寫例外狀況，然後傳回 `null`。 如果您的提供者不會覆寫這個方法，這個方法的預設執行只會傳回傳遞做為輸入的磁片磁碟機資訊。

## <a name="initializing-default-drives"></a>初始化預設磁片磁碟機

您的磁片磁碟機提供者會執行[DriveCmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法來掛接磁片磁碟機。 例如，如果電腦已加入網域，Active Directory 提供者可能會掛接預設命名內容的磁片磁碟機。

這個方法會傳回有關已初始化磁片磁碟機或空集合的磁片磁碟機資訊集合。 此方法的呼叫是在 Windows PowerShell 運行[時間呼叫 Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者之後進行。

此磁片磁碟機提供者不會覆寫[DriveCmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。 不過，下列程式碼會顯示預設的實值，其會傳回空的磁片磁碟機集合：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>執行 InitializeDefaultDrives 的相關事項

所有磁片磁碟機提供者都應該掛接根磁片磁碟機，以協助使用者進行發現。 根磁片磁碟機可能會列出作為其他已掛接磁片磁碟機之根目錄的位置。 例如，Active Directory 提供者可能會建立一個磁片磁碟機，其中列出在根分散式系統內容（DSE）的 `namingContext` 屬性中找到的命名內容。 這可協助使用者探索其他磁片磁碟機的掛接點。

## <a name="code-sample"></a>範例程式碼

如需完整的範例程式碼，請參閱[AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md)。

## <a name="testing-the-windows-powershell-drive-provider"></a>測試 Windows PowerShell 磁片磁碟機提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的任何 Cmdlet。 讓我們來測試範例磁片磁碟機提供者。

1. 執行 `Get-PSProvider` Cmdlet 來抓取提供者清單，以確保 AccessDB 磁片磁碟機提供者存在：

   **PS > `Get-PSProvider`**

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

2. 藉由存取作業系統的系統**管理工具**的 [**資料來源**] 部分，確保資料庫有資料庫伺服器名稱（DSN）。 在 [**使用者 DSN** ] 資料表中，按兩下 [ **MS Access 資料庫**] 並新增磁片磁碟機路徑 C:\ps\northwind.mdb。

3. 使用範例磁片磁碟機提供者建立新的磁片磁碟機：

   **PS > psdrive-name mydb-root c:\ps\northwind.mdb-psprovider AccessDb**

   會出現下列輸出：

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. 驗證連接。 因為連接是定義為磁片磁碟機的成員，所以您可以使用 PDDrive Cmdlet 來進行檢查。

   > [!NOTE]
   > 使用者還無法以磁片磁碟機的形式與提供者互動，因為提供者需要該互動的容器功能。 如需詳細資訊，請參閱[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

   **PS > （psdrive mydb）。連接**

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

5. 移除磁片磁碟機並結束命令介面：

   **PS > 移除-psdrive mydb**

   **PS > 結束**

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)
