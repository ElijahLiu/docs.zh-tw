---
title: "&lt;memoryCache&gt; 項目 (快取設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<memoryCache> 項目"
  - "快取 [.NET Framework], 組態"
  - "memoryCache 項目"
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;memoryCache&gt; 項目 (快取設定)
定義用來設定根據 <xref:System.Runtime.Caching.MemoryCache> 類別之快取的項目。<xref:System.Runtime.Caching.Configuration.MemoryCacheElement> 類別定義可用來設定快取的 [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) 項目。 多個 <xref:System.Runtime.Caching.MemoryCache> 類別執行個體可以用於單一應用程式。 組態檔中的每個 `memoryCache` 項目都可以包含具名 <xref:System.Runtime.Caching.MemoryCache> 執行個體的設定。  
  
 \<configuration\>  
\<system.runtime.caching\>  
\<memoryCache\>  
  
## 語法  
  
```  
<memoryCache   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
< memoryCache />  
```  
  
## 類型  
 <xref:System.Runtime.Caching.MemoryCache> 類別。  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`CacheMemoryLimitMegabytes`|<xref:System.Runtime.Caching.MemoryCache> 物件執行個體可以成長的最大記憶體大小 \(MB\)。 預設值為 0，表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 類別的自動調整啟發學習法。|  
|`Name`|快取組態的名稱。|  
|`PhysicalMemoryLimitPercentage`|快取可使用的實體記憶體百分比。 預設值為 0，表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 類別的自動調整啟發學習法。|  
|`PollingInterval`|表示時間間隔的值，在此時間之後，快取實作會比較目前的記憶體負載與針對快取執行個體所設定的絕對和百分比型記憶體限制。 此值是以 "HH:MM:SS" 格式輸入。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含 `namedCache` 執行個體的組態設定集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.runtime.caching\>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|包含可讓您實作 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 內建應用程式中輸出快取的類型。|  
  
## 備註  
 <xref:System.Runtime.Caching.MemoryCache> 類別是抽象 <xref:System.Runtime.Caching.ObjectCache> 類別的具體實作。<xref:System.Runtime.Caching.MemoryCache> 類別執行個體可以與應用程式組態檔中的組態資訊一起提供。[memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) 組態區段包含 `namedCaches` 組態集合。  
  
 初始化記憶體型快取物件時，會先嘗試尋找 `namedCaches` 項目，而此項目符合傳遞給記憶體快取建構函式之參數中的名稱。 如果找不到 `namedCaches` 項目，則會從組態檔中擷取輪詢和記憶體管理資訊。  
  
 初始化程序接著會判斷是否已覆寫任何組態項目，方法是在建構函式中使用組態資訊的選擇性名稱\/值組集合。 如果您在名稱\/值組集合中傳遞下列任何一個值，則這些值會覆寫從組態檔取得的資訊︰  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## 範例  
 下列範例示範如何透過將 `name` 屬性設定為 "default"，以將 <xref:System.Runtime.Caching.MemoryCache> 物件的名稱設定為預設快取物件名稱。  
  
 `cacheMemoryLimitMegabytes` 屬性和 `physicalMemoryPercentage` 屬性都設定為零。 將這些屬性設定為零表示預設會使用 <xref:System.Runtime.Caching.MemoryCache> 自動調整啟發學習法。 快取實作應該會每隔兩分鐘即比較目前的記憶體負載與絕對和百分比型記憶體限制。  
  
```  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Runtime.Caching.MemoryCache>   
 [\<system.runtime.caching\> 項目 \(快取設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)   
 [\<namedCaches\> 項目 \(快取設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)