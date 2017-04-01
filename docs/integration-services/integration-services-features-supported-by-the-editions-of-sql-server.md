---
title: "Funzionalit&#224; di Integration Services supportate dalle edizioni di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: 15
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Funzionalit&#224; di Integration Services supportate dalle edizioni di SQL Server
 Questo argomento illustra i dettagli delle funzionalità di SQL Server Integration Services (SSIS) supportate dalle diverse edizioni di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Per le funzionalità supportate dalle edizioni Evaluation e Developer, vedere SQL Server Enterprise Edition. 
  
Per le note sulla versione più recenti e informazioni sulle novità, vedere quanto segue:
-   [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Novità di Integration Services in SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [What's New in Integration Services in SQL Server vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md) (Novità di Integration Services in SQL Server vNext)
    
**Try SQL Server 2016!** (Provare SQL Server 2016)    

SQL Server Evaluation Edition è disponibile per un periodo di valutazione di 180 giorni.  
    
> [![Download da Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Scaricare SQL Server 2016 da Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Macchina virtuale di Azure small](../analysis-services/media/azure-virtual-machine-small.png) **[Spin up a Virtual Machine with SQL Server 2016 already installed](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** (Accedere a una macchina virtuale con SQL Server 2016 già installato)    

##  <a name="a-nameisanew-integration-services-features-in-sql-server-vnext"></a><a name="IS"></a>Nuove funzionalità di Integration Services in SQL Server vNext
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Scalabilità orizzontale|Sì||||||Sì|
|Supporto per Microsoft Dynamics AX e Microsoft Dynamics CRM nei componenti OData <sup>1</sup>|Sì|Sì|||||Sì|

<sup>1</sup> Questa funzionalità è supportata anche in SQL Server 2016 con Service Pack 1.

##  <a name="a-nameisa-integration-services"></a><a name="IS"></a> Integration Services  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Connettori origine dati incorporati|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Attività e connettori di origine dati di Azure|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Importazione/Esportazione guidata SQL Server|Sì|Sì|Sì|Sì|Sì|Sì|Sì|  
|Connettori e attività Hadoop/HDFS|Sì|Sì|Sì||||Sì|  
|Progettazione SSIS e SSIS Runtime|Sì|Sì|||||Sì|  
|Attività e trasformazioni predefinite|Sì|Sì|||||Sì|  
|Strumenti di profiling dei dati di base|Sì|Sì|||||Sì|  
|Servizio Change Data Capture per Oracle di Attunity|Sì||||||Sì|  
|Progettazione Change Data Capture per Oracle di Attunity|Sì||||||Sì| 

##  <a name="a-nameisaaa-integration-services---advanced-adapters"></a><a name="ISAA"></a> Integration Services - Adattatori avanzati  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Destinazione Oracle a prestazioni elevate|Sì||||||Sì|  
|Destinazione Teradata a prestazioni elevate|Sì||||||Sì|  
|Origine e destinazione SAP BW|Sì||||||Sì|  
|Adattatore di destinazione per il training del modello di data mining|Sì||||||Sì|  
|Adattatore di destinazione dell'elaborazione dimensione|Sì||||||Sì|  
|Adattatore di destinazione dell'elaborazione partizione|Sì||||||Sì|  
|Componenti Change Data Capture di Attunity|Sì||||||Sì|  
|Connettore per ODBC (Open Database Connectivity) di Attunity|Sì||||||Sì|  
  
##  <a name="a-nameisata-integration-services---advanced-transforms"></a><a name="ISAT"></a> Integration Services - Trasformazioni avanzate  
  
|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Ricerche persistenti (prestazioni elevate)|Sì||||||Sì|  
|Trasformazione di query di data mining|Sì||||||Sì|  
|Trasformazioni di Ricerca fuzzy e Raggruppamento fuzzy|Sì||||||Sì|  
|Trasformazioni di estrazioni e ricerca termini|Sì||||||Sì|  
  