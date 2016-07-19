---
title: "分離設定和環境資料"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: ebd74549e2671a332ef6abf131ab984a4d0865a6
ms.openlocfilehash: 8a3ae5fdf5d70de999ca6b992efb14533408c305

---

# 分離設定和環境資料

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

在 Windows PowerShell 預期狀態設定 (DSC) 中，設定資料和設定邏輯是可以分離的。 另一個查看方式是將結構化設定 (例如，設定可能需要安裝 IIS) 和環境設定視為分開的 (也就是說，無論情況是測試環境或生產環境，節點名稱可能不同，但它們套用的設定都是一樣的)。 這有下列優點：

* 設定資料可重複使用於不同的資源、節點和設定。
* 如果設定邏輯不含硬式編碼資料，會增加重複使用性。 這類似很好的函式指令碼處理指導方針。
* 如有某些資料需要變更，您只要在一個位置變更資料，省時並減少錯誤。

## 基本概念和範例

DSC 使用 **ConfigurationData** 參數指定設定的環境部分，它是雜湊表 (或使用包含雜湊表的 .psd1 檔案)。 這個雜湊表至少要有一個具有結構化值的索引鍵 **AllNodes**。 例如：

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

請注意，AllNodes 索引鍵的值是陣列。 這個陣列的每個元素也是雜湊表，需要 NodeName 作為索引鍵：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

AllNodes 中的每個雜湊表項目都會對應到設定節點的設定資料。 除了必要的 NodeName 索引鍵，雜湊表中也可以加入其他索引鍵，例如：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

DSC 提供三個特殊變數，在設定指令碼中使用：

* **$AllNodes**：指是所有的節點。 您可以使用篩選搭配 **.Where()** 和 **.ForEach()**，不使用硬式編碼節點名稱為動作選取特定的節點，您可以撰寫類似下面的內容，在上例中選取 VM-1 和 VM-3：

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**：只要篩選過節點集，您就可以使用 $Node 參考特定的項目。 例如：

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

若要將屬性套用至所有節點，您可以設定 NodeName = “*”。 例如，您可以如下為每個節點提供 LogPath 屬性：

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**：您可以在設定內使用這個變數，存取當做參數傳遞的設定資料雜湊表。 例如：

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3"
            Role     = "WebServer"
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

完整範例請參閱 [xWebAdministration 模組](https://powershellgallery.com/packages/xWebAdministration)。




<!--HONumber=Jun16_HO4-->


