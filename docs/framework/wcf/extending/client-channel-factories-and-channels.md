---
title: "用戶端：通道處理站與通道 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 用戶端：通道處理站與通道
這個主題會討論通道處理站和通道的建立方面。  
  
## 通道處理站與通道  
 通道處理站會負責建立通道。  而通道處理站所建立的通道會用於傳送訊息。  這些通道會負責從上層取得訊息、執行必須的處理動作，然後將訊息傳送至下層。  下圖會說明這個程序。  
  
 ![用戶端工廠和通道](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc\_WCFChannelsigure2HIghLevelFactgoriesc")  
通道處理站會建立通道。  
  
 關閉時，通道處理站會負責關閉所建立但尚未關閉的任何通道。  請注意，此處的模型為非對稱，這是因為關閉通道接聽項時，只會停止接受新通道，但會讓現有的通道保持為開啟，這樣才可以繼續接收訊息。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會提供此處理序的基底類別協助程式   \(如需本主題討論的通道協助程式類別圖表，請參閱[通道模型概觀](../../../../docs/framework/wcf/extending/channel-model-overview.md)\)。  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> 類別會實作 <xref:System.ServiceModel.ICommunicationObject> 並強制執行[開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)步驟 2 中所述的狀態電腦。  
  
-   ``  <xref:System.ServiceModel.Channels.ChannelManagerBase> 類別會實作 <xref:System.ServiceModel.Channels.CommunicationObject>，並為 <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=fullName> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=fullName> 提供統一的基底類別。  <xref:System.ServiceModel.Channels.ChannelManagerBase> 類別可以和 <xref:System.ServiceModel.Channels.ChannelBase> 一起運作，而後者是實作 <xref:System.ServiceModel.Channels.IChannel> 的基底類別。  
  
-   ``  <xref:System.ServiceModel.Channels.ChannelFactoryBase> 類別會實作 <xref:System.ServiceModel.Channels.ChannelManagerBase> 和 <xref:System.ServiceModel.Channels.IChannelFactory>，並且將 `CreateChannel` 多載合併為單一 `OnCreateChannel` 抽象方法。  
  
-   ``  <xref:System.ServiceModel.Channels.ChannelListenerBase> 類別會實作 <xref:System.ServiceModel.Channels.IChannelListener>。  它會負責基礎的狀態管理。  
  
 下列討論將以[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md) 範例為基礎。  
  
### 建立通道處理站y  
 `UdpChannelFactory` 是衍生自 <xref:System.ServiceModel.Channels.ChannelFactoryBase>。  範例會覆寫 <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A>，以提供訊息編碼器之訊息版本的存取權。  當狀態電腦進行轉換時，該範例也會覆寫 <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> 以終止 <xref:System.ServiceModel.Channels.BufferManager> 的執行個體。  
  
#### UDP 輸出通道  
 `UdpOutputChannel` 會實作 <xref:System.ServiceModel.Channels.IOutputChannel>。  建構函式會驗證引數，並根據傳進的 <xref:System.ServiceModel.EndpointAddress> 建構目的地 <xref:System.Net.EndPoint> 物件。  
  
 覆寫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> 後會建立用於將訊息傳送至此 <xref:System.Net.EndPoint> 的通訊端 \(Socket\)。  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 可以依正常程序或非正常程序關閉通道。  如果依正常程序關閉通道，將會關閉通訊端，並且會呼叫基底類別 `OnClose` 方法。  如果因此發生例外狀況，則基礎結構會呼叫 `Abort`，確保已清除通道。  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
  
```  
  
 實作 `Send()` 和 `BeginSend()`\/`EndSend()`。  這分成兩個主要區段。  首先，將訊息序列化為位元組陣列：  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
  
```  
  
 然後在 Wire 上傳送產生的資料：  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## 請參閱  
 [開發通道](../../../../docs/framework/wcf/extending/developing-channels.md)