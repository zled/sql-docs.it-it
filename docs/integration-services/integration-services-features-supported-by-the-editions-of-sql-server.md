---
title: "Funzionalità supportate dalle edizioni di SQL Server Integration Services | Documenti Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 365fb52c9808e0402323d52c85371c35555d833e
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Funzionalità di servizi di integrazione supportate dalle edizioni di SQL Server
 Questo argomento illustra i dettagli delle funzionalità di SQL Server Integration Services (SSIS) supportate dalle diverse edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Per le funzionalità supportate dalle edizioni Evaluation e Developer, vedere le funzionalità elencate per Enterprise Edition nelle tabelle seguenti.
  
Per le note sulla versione più recente e informazioni sulle novità, vedere gli articoli seguenti:
-   [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Novità di Integration Services in SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Novità di Integration Services in SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**Try SQL Server 2016!**    

SQL Server Evaluation Edition è disponibile per un periodo di valutazione di 180 giorni.  
    
> [![Download da Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Scaricare SQL Server 2016 da Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a>Nuove funzionalità di Integration Services in SQL Server 2017
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Scalabilità orizzontale Master|Sì|||||
|Scalabilità di lavoro|Sì|Sì <sup>1</sup>|TBD|TBD|TBD|
|Supporto per Microsoft Dynamics AX e Microsoft Dynamics CRM nei componenti di OData <sup>2</sup>|Sì|Sì||||

<sup>1</sup> se si eseguono i pacchetti che richiedono funzionalità Enterprise solo in orizzontale, la scala i lavoratori, è inoltre necessario eseguire nelle istanze di SQL Server Enterprise Edition.

<sup>2</sup> questa funzionalità è supportata anche in SQL Server 2016 con Service Pack 1.

## <a name="IEWiz"></a>SQL Server importazione / esportazione guidata

|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Importazione/Esportazione guidata SQL Server|Sì|Sì|Sì|Sì|Sì|  

## <a name="IS"></a> Integration Services  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Connettori origine dati incorporati|Sì|Sì|||| 
|Attività e trasformazioni predefinite|Sì|Sì||||  
|Origine ODBC e destinazione di Attunity|Sì|Sì|||| 
|Attività e connettori di origine dati di Azure|Sì|Sì||||  
|Attività e i connettori di Hadoop/HDFS|Sì|Sì||||  
|Strumenti di profiling dei dati di base|Sì|Sì|||| 

## <a name="ISAA"></a>Integration Services - avanzate origini e destinazioni  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Destinazione Oracle a prestazioni elevate di Attunity|Sì|||||  
|Destinazione Teradata a prestazioni elevate di Attunity|Sì|||||  
|Origine e destinazione SAP BW|Sì|||||  
|Destinazione training modello di data mining|Sì|||||  
|Destinazione elaborazione dimensione|Sì|||||  
|Destinazione elaborazione partizione|Sì|||||  
  
## <a name="ISAT"></a>Integration Services - avanzate attività e trasformazioni  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Ricerche di persistenti (prestazioni elevate)|Sì|||||  
|Componenti Change Data Capture di Attunity <sup>1</sup>|Sì|||||  
|Trasformazione di query di data mining|Sì|||||  
|Trasformazioni di ricerca fuzzy e raggruppamento fuzzy|Sì|||||  
|Estrazione termini e le trasformazioni ricerca termini|Sì|||||  

<sup>1</sup> i componenti di Change Data Capture di Attunity richiedono Enterprise edition. Il servizio Change Data Capture e Change Data Capture Designer, tuttavia, non richiedono Enterprise edition. È possibile utilizzare la finestra di progettazione e il servizio in un computer in cui SSIS non è installato.
