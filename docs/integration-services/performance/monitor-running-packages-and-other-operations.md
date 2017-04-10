---
title: "Esecuzione di pacchetti e altre operazioni di monitoraggio | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Esecuzione di pacchetti e altre operazioni di monitoraggio
  È possibile monitorare esecuzioni di pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], convalide di progetto e altre operazioni di usando uno o più strumenti tra quelli indicati di seguito. Alcuni strumenti, tra cui le scelte dei dati, sono disponibili solo per i progetti distribuiti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Log  
  
     Per altre informazioni, vedere [registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
-   Report  
  
     Per altre informazioni, vedere [report per il server Integration Services](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
-   Viste  
  
     Per altre informazioni, vedere [viste &#40;Catalogo di Integration Services&#41;](../../integration-services/system-views/views-integration-services-catalog.md).  
  
-   Contatori delle prestazioni  
  
     Per altre informazioni, vedere [i contatori delle prestazioni](../../integration-services/performance/performance-counters.md).  
  
-   Scelte dei dati  
  
## Tipi di operazione  
 Nel catalogo **SSISDB** vengono monitorati numerosi tipi diversi di operazioni nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. A ogni operazione possono essere associati più messaggi. Ogni messaggio può essere classificato in uno dei molti tipi diversi. Ad esempio, un messaggio può essere informativo, di avviso o di errore. Per l'elenco completo dei tipi di messaggi, vedere la documentazione relativa alla vista Transact-SQL [catalog.operation_messages &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md). Per l'elenco completo dei tipi di operazioni, vedere [catalog.operations &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md).  
  
 Nove diversi tipi di stato consentono di indicare lo stato di un'operazione. Per l'elenco completo dei tipi di stato, vedere la vista [catalog.operations &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md).  
  
## Contenuto correlato  
 Intervento nel blog relativo alla [panoramica dell'API T-SQL SSIS](http://go.microsoft.com/fwlink/?LinkId=249051) su blogs.msdn.com.  
  
  