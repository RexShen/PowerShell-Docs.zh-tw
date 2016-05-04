---
title: 針對多個物件重複工作 (ForEach-Object)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
---
# 針對多個物件重複工作 (ForEach-Object)
**ForEach-Object** Cmdlet 針對目前的管線物件使用指令碼區塊和 $_ 描述元，讓您能夠在管線中的每個物件上執行命令。 這可以用來執行一些複雜的工作。

一個可能適用的情況是操控資料，使其更加實用。 例如，您可以使用 WMI 中的 Win32_LogicalDisk 類別，傳回每個本機磁碟的可用空間資訊。 傳回的資料是以位元組為單位，不過這會很難閱讀︰

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

我們可以將 FreeSpace 值轉換成 MB，方法是將每個值除以 1024 兩次；第一次相除之後，資料會以 KB 為單位，第二次相除之後，資料會以 MB 為單位。 您可以輸入下列命令，在 ForEach-Object 指令碼區塊中執行這項操作︰

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

不過，輸出現在會是沒有相關聯標籤的資料。 因為這類 WMI 屬性是唯讀的，所以您無法直接轉換 FreeSpace。 如果您輸入︰

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

您會收到錯誤訊息：

```
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

您可以使用一些進階技術來重新組織資料，但更簡單的方法是使用 **Select-Object** 建立新的物件。



<!--HONumber=Apr16_HO1-->


