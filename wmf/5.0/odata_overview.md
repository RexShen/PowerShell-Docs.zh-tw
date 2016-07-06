# 根據 OData 端點產生 PowerShell Cmdlet
根據 OData 端點產生 Windows PowerShell Cmdlet
--------------------------------------------------------------

**Export-ODataEndpointProxy** 是 Cmdlet，它會根據指定的 OData 端點所公開的功能產生一組 Windows PowerShell Cmdlet。

下例示範如何使用這個新的 Cmdlet：

\# Export-ODataEndpointProxy 基本使用案例

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

這項功能仍有部分主要使用案例仍在開發中，包括但不限於：
-   關聯
-   傳遞資料流

根據具有 ODataUtils 的 OData 端點產生 Windows PowerShell Cmdlet
------------------------------------------------------------------------------
ODataUtils 模組可以從支援 OData 的 REST 端點產生 Windows PowerShell Cmdlet。 下列的累加增強功能位在 Microsoft.PowerShell.ODataUtils Windows PowerShell 模組中。
-   從伺服器端端點到用戶端的通道其他資訊。
-   用戶端的分頁支援
-   使用 -Select 參數進行伺服器端篩選
-   Web 要求標頭的支援

Export-ODataEndPointProxy Cmdlet 產生的 Proxy Cmdlet 提供伺服器端 OData 端點資訊資料流 (新的 Windows PowerShell 5.0 功能) 的其他資訊 (用戶端 Proxy 產生期間所使用的 $metadata 中未提及)。 下例為取得這項資訊的方法。
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

您可以使用用戶端的分頁支援，從批次的伺服器端取得記錄。 當您必須透過網路從伺服器取得大量資料時，這非常有用。
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

產生的 Proxy Cmdlet 支援 –Select 參數，這可用為篩選條件，只接收用戶端需要的記錄屬性。 因為篩選發生在伺服器端，所以這會減少透過網路傳送的資料量。
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Export-ODataEndpointProxy Cmdlet 和它產生的 Proxy Cmdlet，現在支援標頭參數 (提供值當做雜湊表)，可用來傳輸伺服器端 OData 端點所預期的任何其他資訊。 在下列範例中，您可以透過期待驗證訂閱金鑰的服務標頭傳輸訂閱金鑰。
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```


<!--HONumber=Jun16_HO4-->


