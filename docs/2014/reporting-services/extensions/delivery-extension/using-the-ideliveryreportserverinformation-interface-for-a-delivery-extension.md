---
title: Using the IDeliveryReportServerInformation Interface for a Delivery Extension (Uso dell'interfaccia IDeliveryReportServerInformation per un'estensione per il recapito) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e0a03b385bc6cbc4f4d1c5794829a52bcf3d7cf7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153952"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Utilizzo dell'interfaccia IDeliveryReportServerInformation per un'estensione per il recapito
  L'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> espone diverse proprietà che è possibile utilizzare per recuperare informazioni su un server di report. È possibile utilizzare queste informazioni per recapitare notifiche e report. Quando si implementa la classe di estensioni per il recapito, si implementa la proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>, come richiesto dall'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> restituisce un oggetto che implementa l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. Da questo oggetto è possibile ottenere un elenco di estensioni per il rendering attualmente supportate dal server di report.  
  
 Quanto segue `for` ciclo può essere usato per archiviare un elenco di estensioni per il rendering attualmente disponibili nel server di report in un **ArrayList** oggetto.  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 Per altre informazioni sull'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>, [vedere Uso dell'interfaccia IDeliveryReportServerInformation per un'estensione per il recapito](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Implementazione di un'estensione per il recapito](implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  
