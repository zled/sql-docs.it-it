---
title: "Dati per i report per dispositivi mobili di Reporting Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
caps.latest.revision: 15
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 15
---
# Dati per i report per dispositivi mobili di Reporting Services
Il modello di dati [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] è semplice. I dati vengono importati in [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] come raccolta di set di dati. Non sono necessarie relazioni formali tra i set di dati. È possibile eseguire ricerche da un set di dati a un altro fino a quando i valori chiave corrispondono. Le aggregazioni data/ora vengono gestite dal runtime del report per dispositivi mobili e corrisponderanno tra diversi set di dati, anche se la granularità dei dati data/ora differisce tra i set di dati.   
  
È possibile importare dati da due tipi di origini:   
  
* **File di Excel locali**: selezionare un documento di Excel e selezionare uno o più fogli di lavoro da importare. Dopo l'importazione, i dati vengono archiviati all'interno della definizione del report per dispositivi mobili. Per aggiornare i dati dal file di Excel originale, usare il comando **Aggiorna dati** nell'angolo superiore destro della scheda **Dati** di [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]. Per altre informazioni, vedere [Prepare Excel data for Reporting Services mobile reports](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md) (Preparare i dati di Excel per i report per dispositivi mobili di Reporting Services).  
  
* **Set di dati di [!INCLUDE[PRODUCT_NAME](../../includes/server-product-name.md)] condivisi**: esplorare l'elenco di set di dati pubblicati nel server e selezionare quelli da aggiungere al report per dispositivi mobili. I report per dispositivi mobili basati sui dati del server restano sempre connessi ai set di dati del server originale e riflettono lo stato più recente dei dati nel server. Vedere un [elenco delle origini dati supportate](https://msdn.microsoft.com/library/ms159219.aspx).   
  
  Per altre informazioni, vedere [Get data from shared datasets in Reporting Services mobile reports](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md) (Ottenere dati da set di dati condivisi nei report per dispositivi mobili di Reporting Services).  
  
Dopo aver importato i dati in [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)], il resto dell'esperienza di progettazione e creazione di report per dispositivi mobili è identico, indipendentemente dalla provenienza dei dati.   
  
## Connettere elementi del report per dispositivi mobili ai dati ##  
  
Ogni elemento [!INCLUDE[PRODUCT_NAME](../../includes/short-product-name.md)] contiene una o più impostazioni di dati. Ad esempio, l'elemento Misuratore radiale contiene due impostazioni di dati, cioè il valore principale e il valore di confronto, ciascuna delle quali punta esattamente a un singolo campo (colonna) in un set di dati specifico.   
  
Il runtime del report per dispositivi mobili fornisce valori aggregati per il misuratore, in base alle selezioni dell'utente. Si noti che il valore di confronto dell'istanza dello stesso misuratore radiale può essere associato a un campo di un set di dati differente.   
  
### Vedere anche  
-  [Preparare i dati per i report per dispositivi mobili di Reporting Services](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Creare e pubblicare report per dispositivi mobili con SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [Get data from shared datasets in Reporting Services mobile reports (Ottenere dati da set di dati condivisi nei report per dispositivi mobili di Reporting Services)](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [Retain date formatting for Analysis Services data in mobile reports (Mantenere la formattazione della data per i dati di Analysis Services nei report per dispositivi mobili)](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  
