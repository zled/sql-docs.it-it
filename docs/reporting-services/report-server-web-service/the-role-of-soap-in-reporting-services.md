---
title: Il ruolo di SOAP in Reporting Services | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 0d6c14934417d4ece40596c17a7335e09ec1ad78
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="the-role-of-soap-in-reporting-services"></a>Ruolo di SOAP in Reporting Services
  Il servizio Web ReportServer utilizza la messaggistica SOAP (Simple Object Access Protocol) per inviare comandi basati su testo in una rete. Questi comandi sono in formato di testo XML e vengono inviati nel World Wide Web utilizzando HTTP. Grazie all'utilizzo di SOAP come protocollo di comunicazione, il servizio Web ReportServer consente alle applicazioni e ai componenti di scambiare dati con il server di report utilizzando un'infrastruttura aperta molto diffusa. Lo standard SOAP è definito nel sito www.w3.org/TR/SOAP (informazioni in lingua inglese).  
  
 Qualsiasi applicazione client può essere utilizzata come client SOAP a condizione che supporti SOAP e che sia in grado di inviare richieste SOAP. Gestione report è un client SOAP. Questo client fornisce un'interfaccia per il database del server di report in cui vengono archiviati tutti i report e il contenuto correlato ai report. Gli utenti finali possono utilizzare l'applicazione per esplorare e gestire report e cartelle nello spazio dei nomi del server di report. Gestione report è basato sull'infrastruttura del servizio Web ReportServer.  
  
 Un server di report funge da server SOAP, un servizio che supporta SOAP in grado di accettare le richieste dai client SOAP e di creare risposte appropriate. Il server gestisce le richieste e restituisce al client risposte codificate.  
  
 I messaggi SOAP in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] possono avere formati diversi, a seconda del tipo di richiesta effettuata dal client. Nell'esempio seguente viene rappresentata una semplice richiesta client SOAP per la rimozione di un elemento dal database del server di report.  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="http://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 SOAP richiede che i messaggi di essere inserita in un **busta** elemento, con la maggior parte del messaggio all'interno di un **corpo** elemento. In questo esempio il corpo contiene una chiamata al metodo <xref:ReportService2010.ReportingService2010.DeleteItem%2A> che accetta un parametro stringa che rappresenta il percorso dell'elemento da eliminare. È possibile creare un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classe proxy client che incapsula tutte le operazioni SOAP nei metodi. Nell'esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] metodo rappresenta l'esempio SOAP riportato in precedenza.  
  
```  
public void DeleteItem(string item);  
```  
  
 La risposta dal server può essere simile alla seguente:  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="http://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Il metodo <xref:ReportService2010.ReportingService2010.DeleteItem%2A> non restituisce alcun valore, pertanto viene restituita una risposta vuota.  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso all'API SOAP](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [Gestione report &#40; Modalità nativa SSRS &#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Server di Report di Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [Servizio Web ReportServer](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
