---
title: "HOW TO：在重新裝載的設計工具中顯示驗證錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# HOW TO：在重新裝載的設計工具中顯示驗證錯誤
本主題描述如何擷取及發行 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中的驗證錯誤。這提供確認重新裝載設計工具中工作流程是否有效的程序。  
  
 這個工作分為兩個部分。第一個部分是提供 <xref:System.Activities.Presentation.Validation.IValidationErrorService> 的實作。這個介面有要實作一個重要方法 <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>，這個方法會將包含錯誤資訊的 <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> 物件清單傳遞至偵錯記錄檔。在實作此介面之後，您可以將該實作的執行個體發行至編輯內容，藉此擷取錯誤資訊。  
  
### 實作 IValidationErrorService 介面  
  
1.  以下是將驗證錯誤寫出至偵錯記錄檔的簡單實作程式碼範例。  
  
    ```  
  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### 發行至編輯內容  
  
1.  以下用來發行至編輯內容的程式碼。  
  
    ```  
  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```