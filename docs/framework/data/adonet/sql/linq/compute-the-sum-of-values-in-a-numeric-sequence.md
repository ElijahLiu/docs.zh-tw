---
title: "計算數值序列中值的總和 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 計算數值序列中值的總和
使用 <xref:System.Linq.Enumerable.Sum%2A> 運算子，可以計算序列中的數值總和。  
  
 請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的 `Sum` 運算子有下列特性：  
  
-   標準查詢運算子的彙總 \(Aggregate\) 運算子 `Sum` 會將空序列或只包含 null 的序列評估為零。  在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，SQL 的語意 \(Semantics\) 則不變。  因此，`Sum` 會將空序列或只包含 null 的序列評估為 null，而不是零。  
  
-   SQL 對中繼結果的限制會套用至 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總。  32 位元整數量值的總和不會用 64 位元的結果來計算，因此進行 `Sum` 的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 轉譯時可能會發生溢位。  即使標準查詢運算子的實作未使對應的記憶體中序列發生溢位，這個可能性還是存在。  
  
## 範例  
 下列範例會找出 `Order` 資料表中所有訂單的總運費。  
  
 如果您對 Northwind 範例資料庫執行這個查詢，則輸出為：`64942.6900`。  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## 範例  
 下列範例會找出所有產品的訂購單位總數。  
  
 如果您對 Northwind 範例資料庫執行這個查詢，則輸出為：`780`。  
  
 請注意，因為 `Sum` 沒有適用於 short 型別的多載，所以必須轉換 \(Cast\) `short` 型別 \(例如，`UnitsOnOrder`\)。  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## 請參閱  
 [彙總查詢](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)   
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)