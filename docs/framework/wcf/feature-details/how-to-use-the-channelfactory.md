---
title: "HOW TO：使用 ChannelFactory | Microsoft Docs"
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
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# HOW TO：使用 ChannelFactory
會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。  
  
### 建立及使用 ChannelFactory 類別  
  
1.  建置及執行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [設計與實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)、[設定服務](../../../../docs/framework/wcf/configuring-services.md) 和 [裝載服務](../../../../docs/framework/wcf/hosting-services.md)。  
  
2.  使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 產生用戶端的合約 \(介面\)。  
  
3.  在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。  
  
## 範例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]