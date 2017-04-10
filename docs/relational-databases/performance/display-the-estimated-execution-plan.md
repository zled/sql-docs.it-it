---
title: "Visualizzazione del piano di esecuzione stimato | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "zoom [SQL Server]"
  - "piano di esecuzione stimato [SQL Server]"
  - "visualizzazione dei piani di esecuzione"
  - "visualizzazione dei piani di esecuzione"
  - "piani di esecuzione [SQL Server], visualizzazione"
  - "personalizzazione della visualizzazione del piano di esecuzione [SQL Server]"
  - "modifica della visualizzazione del piano di esecuzione"
  - "zoom personalizzato [SQL Server]"
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# Visualizzazione del piano di esecuzione stimato
  In questo argomento viene descritta la procedura per generare rappresentazioni grafiche di piani di esecuzione stimati mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Quando si generano piani di esecuzione stimati, le query o i batch [!INCLUDE[tsql](../../includes/tsql-md.md)] non vengono eseguiti. Nel piano di esecuzione generato vengono invece visualizzate le query che verrebbero utilizzate con maggiore probabilità da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in caso di effettiva esecuzione.  
  
 Per utilizzare questa funzionalità, è necessario che gli utenti dispongano delle autorizzazioni appropriate relative all'esecuzione delle query [!INCLUDE[tsql](../../includes/tsql-md.md)] per le quali verrà generato un piano di esecuzione grafico, nonché dell'autorizzazione SHOWPLAN per tutti i database a cui fa riferimento la query.  
  
### Per visualizzare il piano di esecuzione stimato di una query  
  
1.  Scegliere **Query del Motore di database** nella barra degli strumenti. Per aprire una query esistente e visualizzare il piano di esecuzione stimato, è inoltre possibile fare clic sul pulsante **Apri file** della barra degli strumenti e individuare la query.  
  
2.  Immettere la query di cui si desidera visualizzare il piano di esecuzione stimato.  
  
3.  Scegliere **Visualizza piano di esecuzione stimato** dal menu **Query** oppure fare clic sul pulsante **Visualizza piano di esecuzione stimato** della barra degli strumenti. Il piano di esecuzione stimato verrà visualizzato nel riquadro Risultati della scheda **Piano di esecuzione**. Per visualizzare informazioni aggiuntive, posizionare il mouse sulle icone degli operatori logici e fisici e visualizzare la descrizione e le proprietà dell'operatore nella descrizione comando. In alternativa, è possibile visualizzare le proprietà dell'operatore nella finestra Proprietà. Se tale finestra non è visibile, fare clic con il pulsante destro del mouse su un operatore e scegliere **Proprietà**. Selezionare un operatore e visualizzare le relative proprietà.  
  
4.  Per modificare la visualizzazione del piano di esecuzione, fare clic con il pulsante destro del mouse sul piano di esecuzione e scegliere **Zoom avanti**, **Zoom indietro**, **Personalizza zoom** o **Adatta alla finestra**. **Zoom avanti** e **Zoom indietro** consentono rispettivamente di ingrandire o ridurre il piano di esecuzione in base a valori di percentuale predefiniti. **Personalizza zoom** consente di definire un ingrandimento personalizzato per la visualizzazione, ad esempio 80 percento. **Adatta alla finestra** consente di ingrandire il piano di esecuzione per adattarlo al riquadro Risultati.  
  
  