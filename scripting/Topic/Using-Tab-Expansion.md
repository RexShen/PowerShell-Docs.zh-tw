---
title: 使用 Tab 鍵擴充
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
---
# 使用 Tab 鍵擴充
命令列殼層通常會提供方法，透過加速命令輸入以及提供提示，來自動完成長檔案或命令的名稱。 Windows PowerShell 可讓您按 **Tab** 鍵來填入檔案名稱和 Cmdlet 名稱。

> [!NOTE]
> Tab 鍵擴充是透過內部函式 TabExpansion 所控制。 因為可以修改或覆寫這個函式，所以這項討論只是預設 Windows PowerShell 設定行為的指南。

若要自動從可用的選項中填入檔案名稱或路徑，請輸入部分名稱，然後按 **Tab** 鍵。 Windows PowerShell 會自動將名稱擴充到找到的第一個相符項目。 重複按 **Tab** 鍵，會循環顯示所有可用選項。

Cmdlet 名稱的 Tab 鍵擴充略有不同。 若要對 Cmdlet 名稱使用 Tab 鍵擴充，請輸入名稱的完整第一個部分 (動詞) 和後面的連字號。 您可以填入名稱的更多部分來進行局部比對。 例如，如果您輸入 **Get-co**，然後按 **Tab** 鍵，則 Windows PowerShell 會自動將此項目擴充到 **Get-Command** Cmdlet (請注意，它也會將字母的大小寫變更為其標準形式)。 如果您再次按下 **Tab** 鍵，Windows PowerShell 會將此項目取代為僅其他相符 Cmdlet 名稱 (**Get-Content**)。

您可以對同一行重複使用 Tab 鍵擴充。 例如，您可以對 **Get-Content** Cmdlet 的名稱使用 Tab 鍵擴充，方法是輸入：

```
PS> Get-Con<Tab>
```

按 **Tab** 鍵時，命令會擴充到︰

```
PS> Get-Content
```

您接著可以局部指定 Active Setup 記錄檔的路徑，並再次使用 Tab 鍵擴充︰

```
PS> Get-Content c:\windows\acts<Tab>
```

按 **Tab** 鍵時，命令會擴充到︰

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Tab 鍵擴充處理程序的一個限制是一律會將 Tab 鍵解譯為嘗試完成文字。 如果您複製命令範例並將其貼入 Windows PowerShell 主控台，請確定此範例未包含 Tab 鍵；如果包含的話，將無法預測結果，而且幾乎肯定不會是您預期的結果。



<!--HONumber=Apr16_HO1-->


