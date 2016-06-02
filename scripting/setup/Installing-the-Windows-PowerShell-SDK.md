---
title:  安裝 Windows PowerShell SDK
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c3636b45-61aa-4720-85f0-58312c4fc8f9
---

# 安裝 Windows PowerShell SDK
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。</para>
  </introduction>
  <section>
    <title>安裝 Windows PowerShell 3.0 SDK for Windows 8 和 Windows Server 2012</title>
    <content>
      <para>Windows PowerShell 3.0 會自動和 Windows 8 及 Windows Server 2012 一起安裝。 您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。 這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。 當您安裝 Windows SDK for Windows 8 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中：\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0。 如需詳細資訊，請參閱 <externalLink><linkText>Windows 8 SDK 下載網站</linkText><linkUri>http://msdn.microsoft.com/windows/hardware/hh852363.aspx</linkUri></externalLink>。 開發中心也會提供 Windows PowerShell 程式碼範例。 如需詳細資訊，請參閱<externalLink><linkText>開發人員中心網站</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>的桌面程式碼範例頁面。 </para>
      <para>此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。 如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。 (請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。) </para>
    </content>
  </section>
  <section>
    <title>安裝 Windows PowerShell 3.0 SDK for Windows 7 和 Windows Server 2008 R2</title>
    <content>
      <para>Windows 7 和 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。 您也可以在這些系統上安裝 PowerShell 3.0。 (如需詳細資訊，請參閱<link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">安裝 Windows PowerShell</link>。) 如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。</para>
    </content>
  </section>
  <section>
    <title>安裝 Windows PowerShell 2.0 SDK for Windows 7、Vista、XP、Server 2003 和 Server 2008</title>
    <content>
      <para> <token>mshshort</token> 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。 </para>
      <para>若要安裝這個 SDK，請參閱 <externalLink><linkText>Windows PowerShell 2.0 SDK</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>。</para>
    </content>
    <sections>
      <section>
        <title>參考組件</title>
        <content>
          <para>參考組件預設安裝在下列位置︰<codeInline>c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>。</para>
          <alert class="note">
            <para>針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入至 Windows PowerShell 1.0 安裝。 不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。</para>
          </alert>
        </content>
      </section>
      <section>
        <title>範例</title>
        <content>
          <para>程式碼範例預設安裝在下列位置︰<codeInline>C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>。</para>
          <para>下列章節提供各範例用途的簡短說明。</para>
        </content>
        <sections>
          <section>
            <title>Cmdlet 範例</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>示範如何撰寫取得本機電腦所有處理序的簡易 Cmdlet。</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>示範如何將參數加入 Cmdlet。 Cmdlet 會使用一或多個處理序名稱，並傳回相符的處理序。</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>示範如何加入接受管線輸入的參數。</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>示範如何處理非終止錯誤。</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>示範如何顯示指定的處理序清單。</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>示範如何寫入篩選器，只選取特定的物件。 </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>示範如何搜尋指定模式的檔案。</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para>示範如何實作 <parameterReference>PassThru</parameterReference> 參數，以及如何透過呼叫 <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> 和 <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference> 方法來徵求使用者意見。 當使用者想要強制執行 Cmdlet 傳回物件時，可以指定 <parameterReference>PassThru</parameterReference> 參數，</para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>示範如何停止特定的處理序。</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>示範如何宣告參數的別名，以及如何支援萬用字元。</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>示範如何宣告參數集 (Cmdlet 作為輸入的物件)，以及如何指定要使用的預設參數集 。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>遠端範例</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>示範如何建立用來建立遠端連線的遠端 Runspace。</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>示範如何建構遠端 Runspace 集區，以及如何使用這個集區來同時執行多個命令。</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>示範如何查看現有的 .NET 類別，並確定這個類別所選的公用屬性資訊保持序列化/還原序列化。</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>示範如何查看現有的 .NET 類別，並在類別的公用屬性不提供資訊時，確定這個類別的執行個體資訊保持序列化/還原序列化。</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>示範如何查看現有的 .NET 類別，並確定這個類別和衍生類別的執行個體都會還原序列化 (解除凍結) 成實際的 .NET 物件。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>事件範例</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>示範如何藉由衍生自 ObjectEventRegistrationBase 建立事件註冊 Cmdlet。</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>示範如何接收在遠端電腦上產生的 <token>mshshort</token> 事件通知。 它會使用透過 <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference> 類別公開的 PSEventReceived 事件。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>主控應用程式範例</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para>示範如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 類別同步執行 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> Cmdlet。 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> Cmdlet 會傳回在本機電腦上執行之每個處理序的 <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> 物件。</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para>示範如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 類別同步執行 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> 和 <externalLink><linkText>Sort-Object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> Cmdlet。 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> Cmdlet 會傳回在本機電腦上執行之每個處理序的 <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> 物件，而 Sort-Object 會根據其 <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference> 屬性排序物件。 這些命令的結果會使用 <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference> 控制項顯示。</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para>示範如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 類別同步執行指令碼，以及如何處理非終止錯誤。 指令碼會接收處理序名稱的清單，然後擷取這些處理序。 指令碼結果，包括執行指令碼時產生的所有非終止錯誤，都會顯示在主控台視窗。</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para>示範如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 類別來執行命令，以及如何在執行命令時捕捉擲回的終止錯誤。 執行了兩個命令，而最後一個命令傳遞了無效的參數引數。 最後不傳回任何物件，也不擲回終止錯誤。</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>示範如何將嵌入式管理單元加入 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 物件中，以便在 Runspace 開啟時有嵌入式管理單元的 Cmdlet 可用。 嵌入式管理單元使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 物件，提供同步執行的 Get-Proc Cmdlet (由 <legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">GetProcessSample01 範例</legacyLink> 定義)。</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>示範如何將模組加入 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 物件中，以便在 Runspace 開啟時載入模組。 模組使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 物件提供同步執行的 Get-Proc Cmdlet (由 <legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">GetProcessSample02 範例</legacyLink> 定義)。</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>示範如何建立 Runspace，然後透過 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 物件使用該 Runspace 同步執行兩個 Cmdlet。</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para>示範如何將命令和引數加入 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 物件的管線中，以及如何以同步方式執行命令。</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para>示範如何將指令碼加入 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 物件的管線中，以及如何以非同步方式執行指令碼。 使用事件來處理指令碼的輸出。</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>示範如何建立預設的初始工作階段狀態、如何將 Cmdlet 加入 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>、如何建立使用初始工作階段狀態的 Runspace，以及如何使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> 物件執行命令。</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para>示範如何使用 <codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> 類別建立 Proxy 命令，呼叫現有的 Cmdlet，但限制可用的參數集合。 Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。 這表示使用者只能透過 Proxy 命令存取 Cmdlet 的功能。</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para>示範如何使用 <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> 物件建立受限 Runspace。</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>示範如何使用 Runspace 集區同時執行多個命令。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>主機範例</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>示範如何實作使用自訂主機的主機應用程式。 在這個範例中，建立了使用自訂主機的 Runspace，然後使用 <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> API 執行呼叫 “exit” 的指令碼。 主機應用程式接著會查看指令碼的輸出並列印結果。</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>示範如何撰寫使用 <token>mshshort</token> 執行階段和自訂主機實作的主機應用程式。 主機應用程式會將主機的文化特性設為德文，執行 <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> Cmdlet 並顯示結果，和使用 pwrsh.exe 所看到一樣，然後以德文列印目前的日期和時間。</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>示範如何建置互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>示範如何建置互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。 這個主機應用程式也支援顯示允許使用者指定多個選項的提示。</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>示範如何建置互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。 這個主機應用程式也支援使用 <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> 和 <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink> Cmdlet 呼叫遠端電腦。</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>示範如何建置互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。 此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>提供者範例</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para>示範如何宣告直接衍生自 <codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference> 類別的提供者類別。 這個項目包含在此處只為求完整性。</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para>示範如何覆寫 <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> 和 <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> 方法，以支援呼叫 New-PSDrive 和 Remove-PSDrive Cmdlet。 這個範例中的提供者類別衍生自 <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference> 類別。</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para>示範如何覆寫 <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> 和 <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> 方法，以支援呼叫 Get-Item 和 Set-Item Cmdlet。 這個範例中的提供者類別衍生自 <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference> 類別。</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>示範如何覆寫容器方法，以支援呼叫 Copy-Item、Get-ChildItem、New-Item 和 Remove-Item Cmdlet。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 這個範例中的提供者類別衍生自 <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference> 類別。</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>示範如何覆寫容器方法，以支援呼叫 Move-Item 和 Join-Path Cmdlet。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 這個範例中的提供者類別衍生自 <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> 類別。</para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>示範如何覆寫內容方法，以支援呼叫 Clear-Content、Get-Content 和 Set-Content Cmdlet。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 這個範例中的提供者類別衍生自 <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> 類別，它會實作 <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference> 介面。</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>



<!--HONumber=May16_HO4-->


