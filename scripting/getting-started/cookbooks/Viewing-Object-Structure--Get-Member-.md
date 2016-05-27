---
title:  檢視物件結構 Get Member 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  a1819ed2-2ef3-453a-b2b0-f3589c550481
---

# 檢視物件結構 (Get-Member)
因為物件在 Windows PowerShell 中播放這類重要角色，所以有數個設計成使用任意物件類型的原生命令。 最重要的是 **Get-Member** 命令。

分析命令所傳回物件的最簡單技巧是將該命令的輸出傳送到 **Get-Member** Cmdlet。 **Get-Member** Cmdlet 顯示物件類型的正式名稱以及其成員的完整清單。 所傳回元素的數目有時可能非常龐大。 例如，Process 物件可以有 100 位以上的成員。

若要查看 Process 物件的所有成員，並將輸出分頁，以檢視其所有內容，請輸入︰

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

此命令的輸出看起來如下︰

```
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

我們可以篩選想要查看的元素，以讓這份長資訊清單更為有用。 **Get-Member** 命令可讓您只列出為屬性的成員。 有數種形式的屬性。 如果我們將 **Get-MemberMemberType** 參數設為值 **Properties**，這個 Cmdlet 會顯示任何類型的屬性。 產生的清單仍然很長，但更容易管理︰

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE] MemberType 的允許值是 AliasProperty、CodeProperty、Property、NoteProperty、ScriptProperty、Properties、PropertySet、Method、CodeMethod、ScriptMethod、Methods、ParameterizedProperty、MemberSet 和 All。

處理序有 60 個以上的屬性。 Windows PowerShell 通常僅顯示任何已知物件之少數屬性的原因，在於顯示其所有項目將會產生無法管理的資訊量。

> [!NOTE]
> Windows PowerShell 使用名稱結尾為 .format.ps1xml 的 XML 檔案中所儲存的資訊，來決定如何顯示物件類型。 Process 物件 (即 .NET System.Diagnostics.Process 物件) 的格式資料儲存在 PowerShellCore.format.ps1xml 中。

如果您需要查看 Windows PowerShell 預設所顯示屬性以外的屬性，則需要自行格式化輸出資料。 使用格式 Cmdlet 來完成這個動作。



<!--HONumber=May16_HO2-->


