---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 C# 撰寫 DSC 資源
ms.openlocfilehash: a19559c225dd91eceed397df91dd584a577cd7d4
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417689"
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="2c515-103">用 C\# 撰寫 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="2c515-103">Authoring a DSC resource in C\#</span></span>

> <span data-ttu-id="2c515-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2c515-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2c515-105">一般而言，Windows PowerShell 預期狀態設定 (DSC) 自訂資源是在 PowerShell 指令碼中實作。</span><span class="sxs-lookup"><span data-stu-id="2c515-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="2c515-106">但您也可以用 C# 撰寫 Cmdlet 來實作 DSC 自訂資源的功能。</span><span class="sxs-lookup"><span data-stu-id="2c515-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="2c515-107">如需以 C# 撰寫 Cmdlet 的簡介，請參閱[撰寫 Windows PowerShell Cmdlet](/powershell/scripting/developer/windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="2c515-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](/powershell/scripting/developer/windows-powershell).</span></span>

<span data-ttu-id="2c515-108">除了用 C# 將資源當做 Cmdlet 實作，建立 MOF 結構描述、建立資料夾結構、匯入和使用自訂之 DSC 資源的程序，一如[撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="2c515-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="2c515-109">撰寫 Cmdlet 式的資源</span><span class="sxs-lookup"><span data-stu-id="2c515-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="2c515-110">本例中，我們會實作簡單的資源，管理文字檔案及其內容。</span><span class="sxs-lookup"><span data-stu-id="2c515-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="2c515-111">撰寫 MOF 結構描述</span><span class="sxs-lookup"><span data-stu-id="2c515-111">Writing the MOF schema</span></span>

<span data-ttu-id="2c515-112">以下是 MOF 資源定義。</span><span class="sxs-lookup"><span data-stu-id="2c515-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="2c515-113">設定 Visual Studio 專案</span><span class="sxs-lookup"><span data-stu-id="2c515-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="2c515-114">設定 Cmdlet 專案</span><span class="sxs-lookup"><span data-stu-id="2c515-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="2c515-115">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2c515-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="2c515-116">建立 C# 專案並提供名稱。</span><span class="sxs-lookup"><span data-stu-id="2c515-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="2c515-117">從可用的專案範本中選取 **[類別庫]** 。</span><span class="sxs-lookup"><span data-stu-id="2c515-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="2c515-118">按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="2c515-118">Click **Ok**.</span></span>
1. <span data-ttu-id="2c515-119">在專案中加入 System.Automation.Management.dll 的組件參考。</span><span class="sxs-lookup"><span data-stu-id="2c515-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="2c515-120">變更組件名稱使符合資源名稱。</span><span class="sxs-lookup"><span data-stu-id="2c515-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="2c515-121">如此，組件應命名為 **MSFT_XDemoFile**。</span><span class="sxs-lookup"><span data-stu-id="2c515-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="2c515-122">撰寫 Cmdlet 程式碼</span><span class="sxs-lookup"><span data-stu-id="2c515-122">Writing the cmdlet code</span></span>

<span data-ttu-id="2c515-123">下列 C# 程式碼會實作 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2c515-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
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
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="2c515-124">部署資源</span><span class="sxs-lookup"><span data-stu-id="2c515-124">Deploying the resource</span></span>

<span data-ttu-id="2c515-125">已編譯的 DLL 檔案應該儲存在類似於指令碼式資源的檔案結構中。</span><span class="sxs-lookup"><span data-stu-id="2c515-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="2c515-126">以下是這項資源的資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="2c515-126">The following is the folder structure for this resource.</span></span>

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a><span data-ttu-id="2c515-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c515-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="2c515-128">概念</span><span class="sxs-lookup"><span data-stu-id="2c515-128">Concepts</span></span>
[<span data-ttu-id="2c515-129">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="2c515-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="2c515-130">其他資源</span><span class="sxs-lookup"><span data-stu-id="2c515-130">Other Resources</span></span>
[<span data-ttu-id="2c515-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c515-131">Writing a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/windows-powershell)
