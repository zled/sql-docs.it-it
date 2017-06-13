---
title: Utilizzo dell&quot;interfaccia IDeliveryReportServerInformation per un&quot;estensione di recapito | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4a3c2ea843dbfe19b797da7b792d10220018a595
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Utilizzo dell'interfaccia IDeliveryReportServerInformation per un'estensione per il recapito
  L'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> espone diverse proprietà che è possibile utilizzare per recuperare informazioni su un server di report. È possibile utilizzare queste informazioni per recapitare notifiche e report. Quando si implementa la classe di estensioni per il recapito, si implementa la proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>, come richiesto dall'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> restituisce un oggetto che implementa l'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. Da questo oggetto è possibile ottenere un elenco di estensioni per il rendering attualmente supportate dal server di report.  
  
 Nell'esempio **per** ciclo può essere utilizzato per archiviare un elenco di estensioni per il rendering attualmente disponibili nel server di report in un **ArrayList** oggetto.  
  
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
  
 Per ulteriori informazioni sul <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interfaccia, vedere [tramite l'interfaccia IDeliveryReportServerInformation per un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Implementazione di un'estensione di recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
