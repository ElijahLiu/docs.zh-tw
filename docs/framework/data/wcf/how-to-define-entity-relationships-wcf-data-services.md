---
title: "HOW TO：定義實體關聯性 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 變更資料"
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：定義實體關聯性 (WCF Data Services)
當您在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中加入新的實體時，並不會自動定義新實體與相關實體之間的任何關聯性。  您可以建立和變更實體執行個體之間的關聯性，而且可以讓用戶端程式庫在資料服務中反映這些變更。  如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 下列範例會建立一個新的物件執行個體，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> 方法，在內容中建立項目與相關訂單的連結。  呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP POST 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## 範例  
 下列範例示範如何使用 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> 方法將 `Order_Details` 物件加入至相關的 `Orders` 物件 \(包含特定 `Products` 物件的參考\)。  <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> 和 <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> 方法可定義關聯性。  此範例中也會明確設定 `Order_Details` 物件的導覽屬性。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorder)]  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [HOW TO：加入、修改和刪除實體](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)