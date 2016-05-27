---
title:  選取物件的組件 Select Object 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  72e64b1a-d351-4500-9da3-24d8a71d7a92
---

# 選取物件的組件 (Select-Object)
您可以使用 **Select-Object** Cmdlet 來建立新的自訂 Windows PowerShell 物件，這些物件包含從用來建立它們的物件中選取的屬性。 輸入下列命令，以建立只包括 Win32_LogicalDisk WMI 類別的 Name 和 FreeSpace 屬性的新物件：

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

發出該命令之後會看不到資料類型；但是，如果您在 Select-Object 之後將結果輸送到 Get-Member，則可以分辨您有新類型的物件 (PSCustomObject)：

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Select-Object 有許多用法。 其中一種是複寫之後可以進行修改的資料。 我們現在可以處理上一節所發生的問題。 我們可以更新新建立物件中的 FreeSpace 值，而且輸出將包括描述性標籤︰

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```



<!--HONumber=May16_HO2-->


