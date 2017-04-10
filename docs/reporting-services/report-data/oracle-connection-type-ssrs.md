---
title: "Tipo di connessione Oracle (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "01/11/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 8
---
# Tipo di connessione Oracle (SSRS)
  Per utilizzare dati di un database Oracle nel report, è necessario disporre di un set di dati basato su un'origine dati del report di tipo Oracle. Questo tipo di origine dati predefinita è basata sul provider gestito .NET Framework per Oracle e richiede un componente software client Oracle.  
  
 Usare le informazioni presenti in questo argomento per compilare un'origine dati. Per istruzioni dettagliate, vedere [Aggiungere e verificare una connessione dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Stringa di connessione  
 Contattare l'amministratore del database per ottenere le informazioni di connessione e le credenziali da utilizzare per connettersi all'origine dati. Nella stringa di connessione di esempio seguente viene specificato un database Oracle nel server "Oracle9" che utilizza Unicode. Il nome del server deve corrispondere a quello definito nel file di configurazione Tnsnames.ora come nome dell'istanza del server Oracle.  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 Per altre informazioni ed esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md).  
  
##  <a name="Credentials"></a> Credenziali  
 Le credenziali sono necessarie per eseguire query, nonché per visualizzare l'anteprima del report in locale e dal server di report.  
  
 Dopo aver pubblicato il report, potrebbe essere necessario modificare le credenziali per l'origine dati affinché quando il report viene eseguito nel server di report, le autorizzazioni per il recupero dei dati risultino valide.  
  
 Per altre informazioni, vedere [Connessioni dati, origini dati e stringhe di connessione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) e [Specifica di credenziali in Generatore report](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Query"></a> Query  
 Per creare un set di dati, è possibile selezionare una stored procedure in un elenco a discesa oppure creare una query SQL. Per compilare una query, è necessario utilizzare la finestra Progettazione query basata su testo. Per altre informazioni, vedere [Interfaccia utente di Progettazione query basata su testo &#40;Generatore report &#41;](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 È possibile specificare le stored procedure che restituiscono solo un set di risultati. Le query basate su cursori non sono supportate.  
  
##  <a name="Parameters"></a> Parametri  
 Se la query include variabili di query, i parametri di report corrispondenti verranno generati automaticamente. I parametri denominati sono supportati da questa estensione. Per Oracle versione 9 o successive, i parametri multivalore sono supportati.  
  
 I parametri di report vengono creati con valori di proprietà predefiniti che all'occorrenza possono essere modificati. Ad esempio, i dati di ogni parametro di report sono di tipo **Text**. Dopo aver creato i parametri di report, potrebbe essere necessario modificare i valori predefiniti. Per altre informazioni, vedere [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="Remarks"></a> Osservazioni  
 Prima di poter connettere un'origine dati Oracle, l'amministratore di sistema deve installare la versione del provider di dati .NET per Oracle che supporta il recupero di dati dal database Oracle. Il provider di dati deve essere installato nello stesso computer di Generatore report e anche nel server di report.  
  
 Per ulteriori informazioni, vedere quanto segue:  
  
-   [Utilizzo del provider di dati .NET Framework per Oracle](http://go.microsoft.com/fwlink/?LinkId=112314) nel sito msdn.microsoft.com  
  
-   [Come utilizzare Reporting Services per configurare e accedere a un'origine dati Oracle](http://support.microsoft.com/kb/834305)  
  
-   [Come aggiungere autorizzazioni per l'entità di sicurezza SERVIZIO DI RETE](http://support.microsoft.com/kb/870668)  
  
###### Estensioni per i dati alternative  
 È inoltre possibile recuperare dati da un database Oracle tramite un tipo di origine dati OLE DB. Per altre informazioni, vedere [Tipo di connessione OLE DB &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  
  
###### Modelli di report  
 È possibile creare anche modelli basati su un database Oracle.  
  
###### Informazioni sulla piattaforma e sulla versione  
 Per altre informazioni sul supporto della piattaforma e della versione, vedere [Origini dei dati supportate da Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentazione online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
##  <a name="HowTo"></a> Procedure  
 In questa sezione sono contenute le istruzioni dettagliate per l'utilizzo di connessioni dati, origini dati e set di dati.  
  
 [Aggiungere e verificare una connessione dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Aggiungere un filtro a un set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
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
 Vengono fornite informazioni sulla raccolta di campi di set di dati generata dalla query.  
  
 [Origini dei dati supportate da Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online](http://go.microsoft.com/fwlink/?linkid=121312) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Vengono fornite informazioni dettagliate sul supporto delle piattaforme e delle versioni per ogni estensione per i dati.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.png "Icona freccia usata con il collegamento Torna all'inizio") [Torna all'inizio](#BackToTop)  
  
## Vedere anche  
 [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  