---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC for Linux nxFile 資源"
ms.openlocfilehash: 14f1ae31a8409b8874d76a91b8b29595e30fbb46
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="a2458-103">DSC for Linux nxFile 資源</span><span class="sxs-lookup"><span data-stu-id="a2458-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="a2458-104">PowerShell 預期狀態設定 (DSC) 的 **nxFile** 資源會提供在 Linux 節點上管理檔案和目錄的機制。</span><span class="sxs-lookup"><span data-stu-id="a2458-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2458-105">語法</span><span class="sxs-lookup"><span data-stu-id="a2458-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="a2458-106">[內容]</span><span class="sxs-lookup"><span data-stu-id="a2458-106">Properties</span></span>

|  <span data-ttu-id="a2458-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a2458-107">Property</span></span> |  <span data-ttu-id="a2458-108">描述</span><span class="sxs-lookup"><span data-stu-id="a2458-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="a2458-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a2458-109">DestinationPath</span></span>| <span data-ttu-id="a2458-110">指定您要確認檔案或目錄狀態的位置。</span><span class="sxs-lookup"><span data-stu-id="a2458-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="a2458-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="a2458-111">SourcePath</span></span>| <span data-ttu-id="a2458-112">指定要從中複製檔案或資料夾資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="a2458-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="a2458-113">此路徑可以是本機路徑，或 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="a2458-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="a2458-114">當 **Type** 屬性的值是檔案，才支援遠端 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="a2458-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>| 
| <span data-ttu-id="a2458-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="a2458-115">Ensure</span></span>| <span data-ttu-id="a2458-116">決定是否要檢查檔案存在。</span><span class="sxs-lookup"><span data-stu-id="a2458-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="a2458-117">將此屬性設定為 "Present" 以確保檔案存在。</span><span class="sxs-lookup"><span data-stu-id="a2458-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="a2458-118">設為 "Absent" 以確保此檔案不存在。</span><span class="sxs-lookup"><span data-stu-id="a2458-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="a2458-119">預設值為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="a2458-119">The default value is "Present".</span></span>| 
| <span data-ttu-id="a2458-120">類型</span><span class="sxs-lookup"><span data-stu-id="a2458-120">Type</span></span>| <span data-ttu-id="a2458-121">指定要設定的資源是目錄或檔案。</span><span class="sxs-lookup"><span data-stu-id="a2458-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="a2458-122">將此屬性設定為 "directory"，表示該資源為目錄。</span><span class="sxs-lookup"><span data-stu-id="a2458-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="a2458-123">將此屬性設定為 "file"，表示該資源為檔案。</span><span class="sxs-lookup"><span data-stu-id="a2458-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="a2458-124">預設值為 "file"。</span><span class="sxs-lookup"><span data-stu-id="a2458-124">The default value is "file"</span></span>| 
| <span data-ttu-id="a2458-125">內容</span><span class="sxs-lookup"><span data-stu-id="a2458-125">Contents</span></span>| <span data-ttu-id="a2458-126">指定檔案的內容，例如特定字串。</span><span class="sxs-lookup"><span data-stu-id="a2458-126">Specifies the contents of a file, such as a particular string.</span></span>| 
| <span data-ttu-id="a2458-127">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="a2458-127">Checksum</span></span>| <span data-ttu-id="a2458-128">定義判斷兩個檔案是否相同時所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="a2458-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="a2458-129">如不指定 **Checksum**，只會使用檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="a2458-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="a2458-130">值為："ctime"、"mtime" 或 "md5"。</span><span class="sxs-lookup"><span data-stu-id="a2458-130">Values are: "ctime", "mtime", or "md5".</span></span>| 
| <span data-ttu-id="a2458-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="a2458-131">Recurse</span></span>| <span data-ttu-id="a2458-132">表示是否包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="a2458-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="a2458-133">將此屬性設定為 **$true**，表示您想要包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="a2458-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="a2458-134">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="a2458-134">The default is **$false**.</span></span> <span data-ttu-id="a2458-135">**注意**：僅當 **Type** 屬性設定為 directory 時，這個屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="a2458-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>| 
| <span data-ttu-id="a2458-136">Force</span><span class="sxs-lookup"><span data-stu-id="a2458-136">Force</span></span>| <span data-ttu-id="a2458-137">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2458-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a2458-138">使用 **Force** 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2458-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="a2458-139">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="a2458-139">The default value is **$false**.</span></span>| 
| <span data-ttu-id="a2458-140">連結</span><span class="sxs-lookup"><span data-stu-id="a2458-140">Links</span></span>| <span data-ttu-id="a2458-141">指定符號連結的預期行為。</span><span class="sxs-lookup"><span data-stu-id="a2458-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="a2458-142">設定此屬性為 "follow"，以遵循符號連結，並在連結目標上執行 (例如，</span><span class="sxs-lookup"><span data-stu-id="a2458-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="a2458-143">複製檔案而非連結)。</span><span class="sxs-lookup"><span data-stu-id="a2458-143">copy the file instead of the link).</span></span> <span data-ttu-id="a2458-144">設定此屬性為 "manage" 以在連結上執行 (例如，</span><span class="sxs-lookup"><span data-stu-id="a2458-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="a2458-145">複製連結本身)。</span><span class="sxs-lookup"><span data-stu-id="a2458-145">copy the link itself).</span></span> <span data-ttu-id="a2458-146">設定此屬性為 "ignore" 以忽略符號連結。</span><span class="sxs-lookup"><span data-stu-id="a2458-146">Set this property to "ignore" to ignore symbolic links.</span></span>| 
| <span data-ttu-id="a2458-147">群組</span><span class="sxs-lookup"><span data-stu-id="a2458-147">Group</span></span>| <span data-ttu-id="a2458-148">要擁有檔案或目錄的 **Group** 名稱。</span><span class="sxs-lookup"><span data-stu-id="a2458-148">The name of the **Group** to own the file or directory.</span></span>| 
| <span data-ttu-id="a2458-149">模式</span><span class="sxs-lookup"><span data-stu-id="a2458-149">Mode</span></span>| <span data-ttu-id="a2458-150">以八進位或符號標記法指定資源的預期權限。</span><span class="sxs-lookup"><span data-stu-id="a2458-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="a2458-151">(例如，777 或 rwxrwxrwx)。</span><span class="sxs-lookup"><span data-stu-id="a2458-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="a2458-152">如果使用符號標記法，就不會提供表示目錄或檔案的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="a2458-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>| 
| <span data-ttu-id="a2458-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a2458-153">DependsOn</span></span> | <span data-ttu-id="a2458-154">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="a2458-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a2458-155">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a2458-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="additional-information"></a><span data-ttu-id="a2458-156">其他資訊</span><span class="sxs-lookup"><span data-stu-id="a2458-156">Additional Information</span></span>


<span data-ttu-id="a2458-157">Linux 和 Windows 預設在文字檔案中使用不同分行符號字元，而在 Linux 電腦上以 __nxFile__ 設定某些檔案時，可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="a2458-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="a2458-158">有多種方式來管理 Linux 檔案的內容，同時避免非預期的分行符號字元所造成的問題：</span><span class="sxs-lookup"><span data-stu-id="a2458-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="a2458-159">步驟 1：從遠端來源 (http、https 或 ftp) 複製檔案：在 Linux 上建立具有所需內容的檔案，並暫存於您將設定之可存取 Web 或 FTP 伺服器的節點。</span><span class="sxs-lookup"><span data-stu-id="a2458-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="a2458-160">以該檔案的 Web 或 FTP URL 定義 __nxFile__ 資源的 __SourcePath__ 屬性。</span><span class="sxs-lookup"><span data-stu-id="a2458-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


<span data-ttu-id="a2458-161">步驟 2：設定 __$OFS__ 屬性後，以 [Get-content](https://technet.microsoft.com/en-us/library/hh849787.aspx) 讀取 PowerShell 指令碼中的檔案內容，以使用 Linux 換行字元。</span><span class="sxs-lookup"><span data-stu-id="a2458-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="a2458-162">步驟 3：使用 PowerShell 函式，以 Linux 換行字元取代 Windows 分行符號。</span><span class="sxs-lookup"><span data-stu-id="a2458-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## <a name="example"></a><span data-ttu-id="a2458-163">範例</span><span class="sxs-lookup"><span data-stu-id="a2458-163">Example</span></span>

<span data-ttu-id="a2458-164">下列範例可確保目錄 `/opt/mydir` 存在，且具有指定內容的檔案存在於此目錄中。</span><span class="sxs-lookup"><span data-stu-id="a2458-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

