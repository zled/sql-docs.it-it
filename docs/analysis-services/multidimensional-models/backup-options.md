---
title: "Opzioni di backup | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backup di database [Analysis Services]"
  - "database [Analysis Services], backup"
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Opzioni di backup
  È possibile eseguire il backup dei database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in molti modi e in tutti i casi è necessario disporre delle autorizzazioni di amministratore del server e del database. È possibile visualizzare la finestra di dialogo **Backup** di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], selezionare le opzioni di configurazione appropriate e quindi eseguire il backup dalla finestra di dialogo. In alternativa, è possibile creare uno script utilizzando le impostazioni già specificate nel file. Sarà quindi possibile salvare lo script ed eseguirlo quando necessario.  
  
## Backup e sincronizzazione  
 Se il database si trova in un'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile usare la caratteristica di sincronizzazione per eseguire il backup del database nell'istanza locale. In questo modo, è possibile spostare le build di sviluppo di un database nell'ambiente di produzione. Per spostare la build di sviluppo nell'ambiente di produzione, è inoltre possibile utilizzare le procedure tradizionali di backup e ripristino basate su file, ma la sincronizzazione offre funzionalità aggiuntive. Il computer di sviluppo e quello di produzione potrebbero, ad esempio, avere impostazioni di sicurezza diverse. Tramite la sincronizzazione è possibile mantenere tali impostazioni e sincronizzare tutti gli oggetti a esclusione dei ruoli. La sincronizzazione, inoltre, comporta in genere un aggiornamento incrementale degli oggetti che sono diversi nei computer di origine e in quelli di destinazione. Questo tipo di backup incrementale non è disponibile quando si utilizza la caratteristica di backup e ripristino. Per altre informazioni, vedere [Sincronizzare database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  L'account del servizio Analysis Services deve disporre delle autorizzazioni per scrivere nel percorso di backup specificato per ogni file. L'utente deve inoltre avere uno dei ruoli seguenti: ruolo di amministratore per l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) per il database di cui eseguire il backup.  
  
## Vedere anche  
 [Finestra di dialogo Backup database &#40;Analysis Services - Dati multidimensionali&#41;](../Topic/Backup%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Backup e ripristino di database di Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Elemento Backup &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  