---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxFile 資源
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954825"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="e3cb8-103">DSC for Linux nxFile 資源</span><span class="sxs-lookup"><span data-stu-id="e3cb8-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="e3cb8-104">PowerShell 預期狀態設定 (DSC) 的 **nxFile** 資源會提供在 Linux 節點上管理檔案和目錄的機制。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3cb8-105">語法</span><span class="sxs-lookup"><span data-stu-id="e3cb8-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="e3cb8-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e3cb8-106">Properties</span></span>

|<span data-ttu-id="e3cb8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e3cb8-107">Property</span></span> |<span data-ttu-id="e3cb8-108">描述</span><span class="sxs-lookup"><span data-stu-id="e3cb8-108">Description</span></span> |
|---|---|
|<span data-ttu-id="e3cb8-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="e3cb8-109">DestinationPath</span></span> |<span data-ttu-id="e3cb8-110">指定您要確認檔案或目錄狀態的位置。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="e3cb8-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="e3cb8-111">SourcePath</span></span> |<span data-ttu-id="e3cb8-112">指定要從中複製檔案或資料夾資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="e3cb8-113">此路徑可以是本機路徑，或 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="e3cb8-114">當 `http/https/ftp`Type**屬性的值是**file**時，才支援遠端** URL。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="e3cb8-115">類型</span><span class="sxs-lookup"><span data-stu-id="e3cb8-115">Type</span></span> |<span data-ttu-id="e3cb8-116">指定要設定的資源是目錄或檔案。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="e3cb8-117">將此屬性設定為 **directory**，表示該資源為目錄。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="e3cb8-118">將其設定為 **file**，表示該資源為檔案。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="e3cb8-119">預設值為 **file**。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-119">The default value is **file**.</span></span> |
|<span data-ttu-id="e3cb8-120">內容</span><span class="sxs-lookup"><span data-stu-id="e3cb8-120">Contents</span></span> |<span data-ttu-id="e3cb8-121">指定檔案的內容，例如特定字串。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="e3cb8-122">總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="e3cb8-122">Checksum</span></span> |<span data-ttu-id="e3cb8-123">定義判斷兩個檔案是否相同時所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="e3cb8-124">如不指定 **Checksum**，只會使用檔案或目錄名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="e3cb8-125">值為：**ctime**、**mtime** 或 **md5**。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="e3cb8-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="e3cb8-126">Recurse</span></span> |<span data-ttu-id="e3cb8-127">表示是否包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="e3cb8-128">將此屬性設定為 `$true`，表示您想要包含子目錄。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="e3cb8-129">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-129">The default is `$false`.</span></span> <span data-ttu-id="e3cb8-130">只有當 **Type** 屬性設定為 **directory** 時，這個屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="e3cb8-131">Force</span><span class="sxs-lookup"><span data-stu-id="e3cb8-131">Force</span></span> |<span data-ttu-id="e3cb8-132">某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="e3cb8-133">使用 **Force** 屬性會覆寫此類錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="e3cb8-134">預設值是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="e3cb8-135">連結</span><span class="sxs-lookup"><span data-stu-id="e3cb8-135">Links</span></span> |<span data-ttu-id="e3cb8-136">指定符號連結的預期行為。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="e3cb8-137">將此屬性設定為 **follow** 以遵循符號連結，並在連結目標上執行。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="e3cb8-138">例如，複製檔案而非連結。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="e3cb8-139">將此屬性設定為 **manage** 以在連結上執行。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="e3cb8-140">例如，複製連結本身。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-140">For example, copy the link itself.</span></span> <span data-ttu-id="e3cb8-141">將此屬性設定為 **ignore** 以忽略符號連結。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="e3cb8-142">群組</span><span class="sxs-lookup"><span data-stu-id="e3cb8-142">Group</span></span> |<span data-ttu-id="e3cb8-143">要擁有檔案或目錄權限的 **Group** 名稱。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="e3cb8-144">[模式]</span><span class="sxs-lookup"><span data-stu-id="e3cb8-144">Mode</span></span> |<span data-ttu-id="e3cb8-145">以八進位或符號標記法指定資源的預期權限。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="e3cb8-146">例如，**777** 或 **rwxrwxrwx**。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="e3cb8-147">如果使用符號標記法，就不會提供表示目錄或檔案的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="e3cb8-148">擁有者</span><span class="sxs-lookup"><span data-stu-id="e3cb8-148">Owner</span></span> |<span data-ttu-id="e3cb8-149">要擁有檔案或目錄的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e3cb8-150">通用屬性</span><span class="sxs-lookup"><span data-stu-id="e3cb8-150">Common properties</span></span>

|<span data-ttu-id="e3cb8-151">屬性</span><span class="sxs-lookup"><span data-stu-id="e3cb8-151">Property</span></span> |<span data-ttu-id="e3cb8-152">描述</span><span class="sxs-lookup"><span data-stu-id="e3cb8-152">Description</span></span> |
|---|---|
|<span data-ttu-id="e3cb8-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e3cb8-153">DependsOn</span></span> |<span data-ttu-id="e3cb8-154">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e3cb8-155">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e3cb8-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="e3cb8-156">Ensure</span></span> |<span data-ttu-id="e3cb8-157">決定是否要檢查檔案存在。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="e3cb8-158">將此屬性設定為 **Present** 以確保檔案存在。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="e3cb8-159">將其設定為 **Absent** 以確保此檔案不存在。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="e3cb8-160">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="e3cb8-161">其他資訊</span><span class="sxs-lookup"><span data-stu-id="e3cb8-161">Additional Information</span></span>

<span data-ttu-id="e3cb8-162">Linux 和 Windows 預設在文字檔案中使用不同分行符號字元，而在 Linux 電腦上以 **nxFile** 設定某些檔案時，可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="e3cb8-163">有多種方式來管理 Linux 檔案的內容，同時避免非預期的分行符號字元所造成的問題：</span><span class="sxs-lookup"><span data-stu-id="e3cb8-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="e3cb8-164">從遠端來源 (HTTP、HTTPS 或 FTP) 複製檔案</span><span class="sxs-lookup"><span data-stu-id="e3cb8-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="e3cb8-165">在 Linux 上以想要的內容建立檔案，並暫存於您所要設定節點可存取的網頁或 FTP 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="e3cb8-166">以該檔案的 Web 或 FTP URL 定義 **nxFile** 資源的 **SourcePath** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
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

1. <span data-ttu-id="e3cb8-167">在設定 [$OFS](https://technet.microsoft.com/library/hh849787.aspx) 屬性後，透過 **Get-Content** 讀取 PowerShell 指令碼中的檔案內容以使用 Linux 分行字元。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
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

1. <span data-ttu-id="e3cb8-168">使用 PowerShell 函式，以 Linux 分行符號字元取代 Windows 分行符號。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
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

## <a name="example"></a><span data-ttu-id="e3cb8-169">範例</span><span class="sxs-lookup"><span data-stu-id="e3cb8-169">Example</span></span>

<span data-ttu-id="e3cb8-170">下列範例可確保目錄 `/opt/mydir` 存在，且具有指定內容的檔案存在於此目錄中。</span><span class="sxs-lookup"><span data-stu-id="e3cb8-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
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
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```