---
title: "Editor origine ODBC (pagina Colonne) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.odbcsource.columns.f1"
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Editor origine ODBC (pagina Colonne)
  Usare la pagina **Colonne** della finestra di dialogo **Editor origine ODBC** per eseguire il mapping tra una colonna di output e ogni colonna esterna (di origine).  
  
 Per ulteriori informazioni sull'origine ODBC, vedere [ODBC Source](../../integration-services/data-flow/odbc-source.md).  
  
## Elenco attività  
 **Per aprire ODBC Source Editor (pagina Colonne)**  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] che contiene l'origine ODBC.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine ODBC.  
  
3.  In **ODBC Source Editor**, fare clic su **Colonne**.  
  
## Opzioni  
  
### Colonne esterne disponibili  
 Elenco delle colonne esterne disponibili nell'origine dei dati. Non è possibile utilizzare questa tabella per l'aggiunta o l'eliminazione di colonne. Selezionare le colonne da utilizzare dall'origine. Le colonne scelte vengono aggiunte all'elenco **Colonna esterna** nell'ordine in cui vengono selezionate.  
  
 Selezionare la casella di controllo **Seleziona tutto** per selezionare tutte le colonne.  
  
### Colonna esterna  
 Una vista delle colonne esterne (di origine) nell'ordine in cui vengono presentate durante la configurazione di componenti che utilizzano i dati dell'origine ODBC.  
  
### Colonna di output  
 Consente di immettere un nome univoco per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna esterna (di origine) selezionata. È comunque possibile scegliere qualsiasi nome descrittivo univoco. Il nome immesso viene visualizzato in Progettazione SSIS.  
  
## Vedere anche  
 [Editor origine ODBC &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [Editor origine ODBC &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  