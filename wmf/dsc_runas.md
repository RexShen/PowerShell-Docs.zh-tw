# DSC 資源的自動 RunAs 支援
DSC RunAs 認證的支援
--------------------------------

2015 年 4 月 WMF 5.0 Preview 包含在指定認證下執行**任何** DSC 資源的支援，方法是使用屬性 PsDscRunAsCredential。 它可啟用讓某些動作可以執行的狀況，像是在特定使用者內容中安裝 MSI 封裝、存取使用者的登錄 Hive、存取使用者特定的本機目錄、存取網路共用等。

下列項目顯示在 DSC 中使用 PsDscRunAsCredential 屬性變更使用者命令提示字元背景色彩的範例。

設定 ChangeCmdBackGroundColor

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## 已知問題

在此版本中，下列為已知的 DSC RunAs 認證功能問題︰

-   WindowsProcess 資源不支援 RunAs 認證。

<!--HONumber=Mar16_HO2-->
