---
title: "Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: edd76ae9-4125-45a8-bf42-47a85b9d9a32
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati
In questa procedura dettagliata verrà sviluppata una soluzione end-to-end per la modellazione predittiva usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Questa procedura dettagliata è basata su un set di dati pubblico, il set di dati dei taxi di New York City. Verrà usata una combinazione di codice R, dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e funzioni SQL personalizzate per la creazione di un modello di classificazione che indica la probabilità che l'autista riceva una mancia per una determinata corsa. Verrà inoltre distribuito il modello R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e verranno usati i dati del server per generare punteggi basati sul modello.  
  
Questo esempio può essere facilmente esteso a tutti i tipi di problemi della vita reale, ad esempio alla previsione delle risposte dei clienti alle campagne di vendita o alla previsione di spesa da parte dei visitatori di eventi. Poiché il modello può essere richiamato da una stored procedure, è possibile incorporarlo facilmente in un'applicazione.  
  
**Destinatari**  
  
Questa procedura dettagliata è destinata agli sviluppatori di R. È anche necessaria una certa familiarità con le operazioni di database di base, ad esempio la creazione di database, la creazione di tabelle, l'importazione di dati in tabelle e l'esecuzione di query sulle tabelle usando [!INCLUDE[tsql](../../includes/tsql-md.md)].  Verranno forniti gli script di SQL e R da eseguire.  
  
Se non si ha familiarità con R ma si conoscono i database, questa esercitazione offre un'introduzione all'integrazione di R nei flussi di lavoro aziendali con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Non è richiesto alcun codice R. Vengono forniti tutti gli script. Per eseguire i comandi è necessario installare un IDE R.  
  
**Prerequisiti**  
  
Per eseguire l'esercitazione, è necessario avere accesso a un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installato. Per l'ambiente locale, preparare una workstation di analisi scientifica dei dati che può connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quindi installare le librerie R richieste.  
  
Per altre informazioni, vedere [Prerequisiti per le procedure dettagliate per l'analisi scientifica dei dati &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/prerequisites-for-data-science-walkthroughs-sql-server-r-services.md).  
  
## <a name="overview"></a>Panoramica  
Questa procedura dettagliata illustra una tipica soluzione end-to-end per l'analisi avanzata. Le lezioni devono essere completate in sequenza.  
  
||Tempo stimato per il completamento|  
|-|------------------------------|  
|[Lezione 1: Preparare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)<br /><br />Il processo analitico inizia con il recupero dei dati usati per la creazione di un modello. Verrà scaricato un set di dati pubblico che verrà salvato in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|30 minuti|  
|[Lezione 2: Visualizzare ed esplorare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)<br /><br />Un analista dei dati spesso trascorre molto tempo esaminando i dati e preparandoli per la modellazione, creando nuove funzionalità o trasformando i dati in base alle esigenze.  Verrà usato sia SQL che R per esplorare i dati e generare riepiloghi.|20 minuti|  
|[Lezione 3: Creare funzionalità di dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)<br /><br />Verranno create nuove funzionalità di dati usando funzioni personalizzate in R e [!INCLUDE[tsql](../../includes/tsql-md.md)].|10 minuti|  
|[Lezione 4: Creare e salvare il modello &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)<br /><br />Quando i dati sono pronti, l'analista esegue il training e ottimizza il modello, valutandone le prestazioni e provando parametri diversi. In questa procedura dettagliata verrà creato un modello di classificazione e verranno usati i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per generare le stime. Verrà inoltre tracciata l'accuratezza del modello usando R.|15 minuti|  
|[Lezione 5: Distribuire e usare il modello &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)<br /><br />Il modello verrà quindi distribuito in produzione salvandolo in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e verrà richiamato da una stored procedure per la generazione delle stime.|10 minuti|  
  
## <a name="notes"></a>Note  
Poiché lo scopo della procedura dettagliata è presentare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]agli sviluppatori R, la maggior parte delle azioni possibile viene eseguita usando R. Ciò non significa che R sia necessariamente lo strumento più adatto a ogni attività. In molti casi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe offrire prestazioni migliori, in particolare in attività quali l'aggregazione dei dati e la progettazione delle funzionalità. Tali attività possono trarre vantaggio dalle nuove funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ad esempio gli indici columnstore con ottimizzazione per la memoria.  
  
## <a name="next-step"></a>Passaggio successivo  
[Lezione 1: Preparare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
