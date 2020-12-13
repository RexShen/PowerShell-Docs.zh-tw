---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 磁碟機提供者
description: 建立 Windows PowerShell 磁碟機提供者
ms.openlocfilehash: 639518fce27d941b7529b091364c5905c91a5c0c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663041"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>建立 Windows PowerShell 磁碟機提供者

本主題說明如何建立 Windows PowerShell 磁片磁碟機提供者，以提供透過 Windows PowerShell 磁片磁碟機存取資料存放區的方式。 這種類型的提供者也稱為 Windows PowerShell 磁片磁碟機提供者。 提供者使用的 Windows PowerShell 磁片磁碟機提供連接到資料存放區的方法。

此處所述的 Windows PowerShell 磁片磁碟機提供者提供 Microsoft Access 資料庫的存取權。
對於此提供者，Windows PowerShell 磁片磁碟機代表資料庫 (可以將任意數目的磁片磁碟機新增至磁片磁碟機提供者) 、磁片磁碟機的最上層容器代表資料庫中的資料表，而容器的專案則代表資料表中的資料列。

## <a name="defining-the-windows-powershell-provider-class"></a>定義 Windows PowerShell 提供者類別

您的磁片磁碟機提供者必須定義衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的 .net 類別。 以下是此磁片磁碟機提供者的類別定義：

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

請注意，在此範例中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性會指定提供者的使用者易記名稱，以及提供者在命令處理期間公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。
提供者功能的可能值是由 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉所定義。 此磁片磁碟機提供者不支援任何這些功能。

## <a name="defining-base-functionality"></a>定義基底功能

如 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)所述， [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 基類，該基類會定義初始化和取消初始化提供者所需的方法。 若要執行新增會話特定初始化資訊，以及釋出提供者所使用之資源的功能，請參閱 [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。
不過，大部分的提供者 (包括此處所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。

## <a name="creating-drive-state-information"></a>正在建立磁片磁碟機狀態資訊

所有 Windows PowerShell 提供者均視為無狀態，這表示您的磁片磁碟機提供者必須在呼叫您的提供者時，建立 Windows PowerShell 執行時間所需的任何狀態資訊。

在此磁片磁碟機提供者中，狀態資訊會包含保留為磁片磁碟機資訊一部分的資料庫連接。 以下程式碼顯示如何將這項資訊儲存在描述磁片磁碟機的 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 物件中：

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a>建立磁片磁碟機

若要允許 Windows PowerShell 執行時間建立磁片磁碟機，磁片磁碟機提供者必須執行 [DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 方法。 下列程式碼顯示此磁片磁碟機提供者的 [DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 方法的執行方式：

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

您對此方法的覆寫應該執行下列作業：

- 確認 [System.Management.Automation.PSDriveinfo。根 *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) 成員存在，而且可以建立與資料存放區的連接。
- 建立磁片磁碟機，並填入連接成員，以支援 `New-PSDrive` Cmdlet。
- 驗證所建議磁片磁碟機的 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 物件。
- 使用任何必要的效能或可靠性資訊修改描述磁片磁碟機的 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 物件，或為使用該磁片磁碟機的呼叫端提供額外的資料。
- 使用 [Cmdletprovider WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 方法來處理失敗，然後再傳回 `null` 。

  這個方法會傳回傳遞給方法的磁片磁碟機資訊或它的提供者特定版本。

## <a name="attaching-dynamic-parameters-to-newdrive"></a>將動態參數附加至 >newdrive

`New-PSDrive`您的磁片磁碟機提供者所支援的 Cmdlet 可能需要額外的參數。 為了將這些動態參數附加至 Cmdlet，提供者會實 [DriveCmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 方法。 這個方法會傳回物件，該物件具有剖析屬性（attribute）與 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件類似的屬性和欄位。

此磁片磁碟機提供者不會覆寫這個方法。 但是，下列程式碼會顯示此方法的預設執行：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>移除磁片磁碟機

若要關閉資料庫連接，磁片磁碟機提供者必須執行 [DriveCmdletprovider. >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法。 清除任何提供者特定的資訊之後，這個方法會關閉磁片磁碟機的連接。

下列程式碼顯示此磁片磁碟機提供者的 [DriveCmdletprovider. >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法的執行方式：

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

如果可以移除磁片磁碟機，方法應該會透過參數傳回傳遞給方法的資訊 `drive` 。 如果無法移除磁片磁碟機，方法應寫入例外狀況，然後傳回 `null` 。 如果您的提供者不會覆寫這個方法，這個方法的預設執行只會傳回傳遞做為輸入的磁片磁碟機資訊。

## <a name="initializing-default-drives"></a>正在初始化預設磁片磁碟機

您的磁片磁碟機提供者會執行 [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 方法來掛接磁片磁碟機。 例如，如果電腦已加入網域，Active Directory 提供者可能會掛接預設命名內容的磁片磁碟機。

這個方法會傳回有關已初始化磁片磁碟機的磁片磁碟機資訊集合，或空集合。 在 Windows PowerShell 執行時間呼叫 [Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 方法來初始化提供者之後，就會呼叫這個方法。

此磁片磁碟機提供者不會覆寫 [System.Management.Automation.Provider.Drivecmdletprovider.Ini的 tializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 方法。 但是，下列程式碼會顯示預設的實作為，它會傳回空的磁片磁碟機集合：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>執行 InitializeDefaultDrives 的注意事項

所有磁片磁碟機提供者都應該掛接根磁片磁碟機，以協助使用者進行可探索性。 根磁片磁碟機可能會列出作為其他載入的磁片磁碟機根目錄的位置。 例如，Active Directory 提供者可能會建立一個磁片磁碟機，以列出在根分散式系統內容的屬性中找到的命名內容 `namingContext` (DSE) 。 這可協助使用者探索其他磁片磁碟機的掛接點。

## <a name="code-sample"></a>程式碼範例

如需完整的範例程式碼，請參閱 [AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md)。

## <a name="testing-the-windows-powershell-drive-provider"></a>測試 Windows PowerShell 磁片磁碟機提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的任何 Cmdlet。 讓我們測試範例磁片磁碟機提供者。

1. 執行 `Get-PSProvider` Cmdlet 以取得提供者清單，以確定 AccessDB 磁片磁碟機提供者存在：

   **PS> `Get-PSProvider`**

   下列輸出會出現：

   ```Output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. 存取作業系統的系統 **管理工具** 的 [**資料來源**] 部分，以確定資料庫的資料庫伺服器名稱 (DSN) 存在。 在 [ **使用者 DSN** ] 資料表中，按兩下 [ **MS Access 資料庫** ]，然後新增磁片磁碟機路徑 `C:\ps\northwind.mdb` 。

3. 使用範例磁片磁碟機提供者建立新的磁片磁碟機：

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   下列輸出會出現：

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. 驗證連接。 因為連接是定義為磁片磁碟機的成員，所以您可以使用 Get-PDDrive Cmdlet 來檢查它。

   > [!NOTE]
   > 使用者還無法與提供者互動作為磁片磁碟機，因為提供者需要該互動的容器功能。 如需詳細資訊，請參閱 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。

   **PS> (new-psdrive mydb) 連接**

   下列輸出會出現：

   ```Output
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

5. 移除磁片磁碟機並結束 shell：

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)

[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)
