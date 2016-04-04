# 開始使用 PowerShell 預期狀態設定 #

本指南說明如何開始建立 PowerShell 預期狀態設定文件，並套用至電腦。 本指南假設您大致熟悉 PowerShell Cmdlet、模組和函式。 


## 建立設定 ##

[**設定**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)是描述環境的文件。 環境包含「**節點**」，通常是虛擬或實體機器。 

設定可以有各種形式。 建立新設定的最簡單作法是建立 .ps1 (PowerShell 指令碼) 檔案。 若要這樣做，請開啟您選擇的編輯器。 因為 PowerShell ISE 原本就了解 DSC，所以是不錯的選擇。 將下列項目儲存為 PS1：

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## 設定的組件 ##
**設定**是 PowerShell 4.0 中已加入的關鍵字， 表示一種特殊的預期狀態設定所使用的 PowerShell 函式。 在這個範例中，此函式稱為 myFirstConfiguration。 

下一行是匯入陳述式，類似於匯入模組， 將在稍後討論。

「節點」定義這個設定將產生作用的目標電腦名稱。 雖然這項設定在本機進行編輯，設定仍可連接到遠端節點，並加以設定。 

節點可以是電腦名稱或 IP 位址。 在單一設定文件中可以有多個節點。 使用[設定資料](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)時，您也可以將相同設定套用到多個節點。 在此情況下，節點會是 "localhost"，表示本機電腦。 

下一個項目是[**資源**](https://msdn.microsoft.com/en-us/powershell/dsc/resources)。 資源是設定的建置組塊。 每個資源都是模組，其中定義單一電腦層面的實作邏輯。 您也可以在 PowerShell 中執行 **Get-DscResource** 檢視電腦上的每個資源。 資源必須存在於本機電腦上，並先匯入，然後才可用於 **Import-DscResource** 的設定，其位於這項設定的第二行。 

**制定設定**

如果上述指令碼是儲存並執行，將不會產生任何輸出。 這是因為設定不只是函式，而且上述指令碼已定義了函式，但尚未執行。 函式經定義之後，就必須叫用：
```powershell
myFirstConfiguration
```

在執行設定函數時，設定函數會驗證設定是否有效， 不應有語法錯誤，資源應該定義所有必要的參數，而且應該在執行之前匯入所有資源。

一旦執行設定之後，它會對設定中每個節點建立一個設定名稱包含 **.MOF 檔案**的資料夾。 .MOF 檔案是由 PowerShell DSC 使用，用來透過網路進行通訊、以標準為基礎的管理格式。

制定設定：
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
這會建立 PowerShell 工作，向外連到設定中的節點，並設定節點。 若要查看工作的輸出，請使用 -Wait。 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```



<!--HONumber=Mar16_HO1-->


