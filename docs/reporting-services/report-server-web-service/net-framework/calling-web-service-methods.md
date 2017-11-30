---
title: Chiamata di metodi del servizio Web | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
caps.latest.revision: "38"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eae7dc1f7e673f332f5c85db89b9a247f0a36d35
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="calling-web-service-methods"></a>Chiamata ai metodi del servizio Web
  Quando si usa una classe proxy [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] per chiamare le operazioni del servizio Web, si usano i metodi di tale classe. Questi metodi funzionano come qualsiasi altro metodo di una classe nella libreria di classi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Tutti i metodi del servizio Web dispongono di accesso pubblico e richiedono di fornire il numero appropriato di argomenti e tipi di argomento. Dopo aver creato un'istanza della classe proxy nel progetto, è possibile chiamare i metodi per eseguire operazioni relative ai report tramite il server di report. Il codice C# seguente illustra l'uso del metodo <xref:ReportService2010.ReportingService2010.ListChildren%2A> della classe proxy <xref:ReportService2010.ReportingService2010>. Il codice viene utilizzato per effettuare una chiamata ricorsiva al servizio Web che restituisce una matrice di oggetti <xref:ReportService2010.CatalogItem> contenente un elenco di tutti gli elementi nel database del server di report:  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Guida di riferimento tecnico &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
