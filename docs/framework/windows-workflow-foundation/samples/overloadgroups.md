---
title: "OverloadGroups | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# OverloadGroups
這個範例是由 \(`CreateLocation`\) 活動所組成，這個活動有兩個有趣的特性：  
  
1.  它有一些必要的引數及一些選擇性的引數。  
  
2.  它可讓使用者選擇提供兩組不同引數的其中一組。  
  
 這些行為是使用下列兩個功能所完成：  
  
-   `[isRequired]` 會驗證特定活動的屬性已指派，如果未指派則會擲回例外狀況。  
  
-   `[OverloadGroup]` 會將一組引數放在一起，好讓活動的使用者可以選擇使用某一組或另一組。使用者不能在相同執行個體中使用不同多載群組內的引數。  
  
 在設定不同的工作流程之後，請呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，它會傳回 <xref:System.Activities.Validation.ConstraintViolation> 的 <xref:System.Activities.Validation.ValidationResults> 集合。請將 <xref:System.Activities.Validation.ConstraintViolation> 物件列印到主控台。  
  
### 若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 **OverloadGroups.sln** 範例方案。  
  
2.  建置及執行此方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`  
  
## 請參閱