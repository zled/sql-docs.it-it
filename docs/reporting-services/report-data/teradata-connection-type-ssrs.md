---
title: "Tipo di connessione Teradata (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Tipo di connessione Teradata (SSRS)
  Per includere dati da un database relazionale di Teradata nel report, è necessario disporre di un set di dati basato su un'origine dati del report di tipo Teradata. Questo tipo di origine dati predefinito è basato sull'estensione per l'elaborazione dati del provider gestito .NET per Teradata.  
  
 Usare le informazioni presenti in questo argomento per compilare un'origine dati. Per istruzioni dettagliate, vedere [Aggiungere e verificare una connessione dati &40#;Generatore report e SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Stringa di connessione  
 Contattare l'amministratore del database per ottenere le informazioni di connessione e le credenziali da utilizzare per connettersi all'origine dati. Nell'esempio di stringa di connessione seguente viene specificato un database Teradata sul server identificato da un indirizzo IP:  
  
```  
data source=<IP Address>  
```  
  
 Per altri esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md).  
  
##  <a name="Credentials"></a> Credenziali  
 Le credenziali sono necessarie per eseguire query, nonché per visualizzare l'anteprima del report in locale e dal server di report.  
  
 Dopo aver pubblicato il report, potrebbe essere necessario modificare le credenziali per l'origine dati affinché quando il report viene eseguito nel server di report, le autorizzazioni per il recupero dei dati risultino valide.  
  
 Per altre informazioni, vedere [Connessioni dati, origini dati e stringhe di connessione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) e [Specificare credenziali in Generatore report](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Remarks"></a> Osservazioni  
 Prima che sia possibile connettersi a un'origine dati Teradata, l'amministratore di sistema deve aver installato la versione corretta del provider di dati .NET per Teradata che supporta il recupero di dati dal database di Teradata. Il provider di dati deve essere installato nello stesso computer di Generatore report e anche nel server di report.  
  
 Non tutte le modalità di recapito report sono supportate da questo provider di dati. Il recapito di report tramite sottoscrizioni guidate dai dati non è supportato per questa estensione per l'elaborazione dati. Per altre informazioni, vedere [Usare un'origine dati esterna per i dati del Sottoscrittore &#40;sottoscrizione guidata dai dati&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [Documentazione online](http://go.microsoft.com/fwlink/?linkid=121312) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Models"></a> Modelli di report  
 Per creare un set di dati da un modello di report basato su un'origine dati Teradata, il modello deve essere progettato in Progettazione modelli in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e deve essere pubblicato su un server di report.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Related"></a> Sezioni correlate  
 In queste sezioni della documentazione sono incluse informazioni concettuali approfondite sui dati dei report, nonché le informazioni necessarie sulle procedure per definire, personalizzare e usare parti di un report correlate ai dati.  
  
 [Set di dati del report &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Viene fornita una panoramica sull'accesso ai dati del report.  
  
 [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
 Vengono fornite informazioni sulle connessioni dati e sulle origini dati.  
  
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Vengono fornite informazioni sui set di dati incorporati e condivisi.  
  
 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Vengono fornite informazioni sulla raccolta di campi generata dalla query del set di dati.  
  
 [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online](http://go.microsoft.com/fwlink/?linkid=121312) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Vengono fornite informazioni dettagliate sul supporto delle piattaforme e delle versioni per ogni estensione per i dati.  
  
 [Utilizzo di SQL Server 2008 Reporting Services con il provider di dati .NET Framework per Teradata](http://go.microsoft.com/fwlink/?LinkID=130848)  
 Vengono fornite informazioni dettagliate sull'utilizzo di questa estensione per i dati.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
## Vedere anche  
 [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  