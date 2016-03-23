# 用 C`#` 撰寫 DSC 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

一般而言，Windows PowerShell 預期狀態設定 (DSC) 自訂資源是在 PowerShell 指令碼中實作。 但您也可以用 C# 撰寫 Cmdlet 來實作 DSC 自訂資源的功能。 如需以 C# 撰寫 Cmdlet 的簡介，請參閱[撰寫 Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx)。

除了用 C# 將資源當做 Cmdlet 實作，建立 MOF 結構描述、建立資料夾結構、匯入和使用自訂之 DSC 資源的程序，一如[撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md) 中所述。

## 撰寫 Cmdlet 式的資源
本例中，我們會實作簡單的資源，管理文字檔案及其內容。

### 撰寫 MOF 結構描述

以下是 MOF 資源定義。

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### 設定 Visual Studio 專案
#### 設定 Cmdlet 專案

1. 開啟 Visual Studio。
1. 建立 C# 專案並提供名稱。
1. 從可用的專案範本中選取 **[類別庫]**。
1. 按一下 **[確定]**。
1. 在專案中加入 System.Automation.Management.dll 的組件參考。
1. 變更組件名稱使符合資源名稱。 如此，組件應命名為 **MSFT_XDemoFile**。

### 撰寫 Cmdlet 程式碼

下列 C# 程式碼會實作 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** Cmdlet。

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### 部署資源

已編譯的 DLL 檔案應該儲存在類似於指令碼式資源的檔案結構中。 以下是這項資源的資料夾結構。

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### 另請參閱
#### 概念
[撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md)
#### 其他資源
[撰寫 Windows PowerShell Cmdlet](https://msdn.microsoft.com/en-us/library/dd878294.aspx)<!--HONumber=Feb16_HO4-->
