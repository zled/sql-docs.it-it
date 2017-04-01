---
title: "Risoluzione dei conflitti interattiva | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "risoluzione interattiva di conflitti [replica di SQL Server]"
  - "sistema di risoluzione interattivo [replica di SQL Server]"
  - "articoli [replica di SQL Server], risoluzione dei conflitti"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Risoluzione dei conflitti interattiva
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la replica offre un sistema di risoluzione interattivo che consente di risolvere manualmente i conflitti durante la sincronizzazione su richiesta in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Gestione sincronizzazione Microsoft Windows. Attivato in fase di esecuzione, il sistema di risoluzione interattivo è un'interfaccia grafica che visualizza i dati relativi a ogni riga in conflitto e offre opzioni per la visualizzazione e la modifica dei dati in conflitto, nonché per la risoluzione distinta dei singoli conflitti.  
  
 Il sistema di risoluzione interattivo presenta alcune analogie con il Visualizzatore conflitti. Nel Visualizzatore conflitti vengono tuttavia visualizzati i risultati dei conflitti già risolti dopo la sincronizzazione di tipo merge, mentre il sistema di risoluzione interattivo visualizza ogni conflitto prima della risoluzione e consente di determinarne l'esito durante la sincronizzazione di tipo merge. È necessario che sia disponibile un utente per il monitoraggio del sistema di risoluzione interattivo in caso di conflitto.  
  
> [!NOTE]  
>  La risoluzione interattiva richiede Gestione sincronizzazione Microsoft Windows. Se una sincronizzazione viene eseguita all'esterno di Gestione sincronizzazione Microsoft Windows (come sincronizzazione pianificata o sincronizzazione su richiesta in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o Monitoraggio replica), i conflitti vengono risolti automaticamente senza richiedere l'intervento dell'utente, in base al sistema di risoluzione specificato per l'articolo. I conflitti a livello di record logici non vengono visualizzati nel sistema di risoluzione interattivo. Per visualizzare informazioni relative a questi conflitti, utilizzare le stored procedure di replica. Per ulteriori informazioni, vedere [visualizzare informazioni sul conflitto per le pubblicazioni di tipo Merge & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/view conflict information for merge publications.md).  
  
## Sistemi di risoluzione dei conflitti di articolo e sistema di risoluzione interattivo  
 I sistemi di risoluzione dei conflitti, ovvero il sistema di risoluzione dei conflitti predefinito, un gestore della logica di business o un sistema personalizzato, vengono assegnati ad articoli specifici durante la creazione di una pubblicazione. Tali sistemi utilizzano un set di regole predefinite per determinare il set di dati che è necessario utilizzare quando si immettono dati di riga in conflitto. Il sistema di risoluzione interattivo non è un sistema di risoluzione dei conflitti distinto con regole per stabilire la modifica che prevale nei conflitti, ma uno strumento da utilizzare in combinazione con i sistemi di risoluzione dei conflitti predefiniti e personalizzati. Il sistema di risoluzione dei conflitti di articolo determina la riga confermata e la riga non confermata e il sistema di risoluzione interattivo consente all'utente di accettare, rifiutare o modificare i risultati.  
  
 Per utilizzare il sistema di risoluzione interattivo, è necessario che la risoluzione interattiva sia attivata per ogni articolo e sottoscrizione che la richiede. Dopo essere stato abilitato per uno o più articoli e sottoscrizioni, il sistema di risoluzione interattivo viene utilizzato quando viene rilevato un conflitto durante la sincronizzazione di tipo merge.  
  
 Per utilizzare il sistema di risoluzione interattivo, vedere [specificare risoluzione interattiva dei conflitti per articoli di Merge](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md) e [sincronizzare una sottoscrizione tramite Gestione sincronizzazione Microsoft Windows & #40; Gestione sincronizzazione Microsoft Windows & #41;](../../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md).  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  