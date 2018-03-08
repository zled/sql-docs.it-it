---
title: Visualizzare un piano di esecuzione effettivo | Microsoft Docs
ms.custom: 
ms.date: 08/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
caps.latest.revision: "24"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d34a82e9ceb357fde6059e3259cb2be64a3e50d7
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="display-an-actual-execution-plan"></a>Visualizzazione di un piano di esecuzione effettivo
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Questo argomento descrive come generare piani di esecuzione grafici effettivi usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. I piani di esecuzione effettivi vengono generati dopo l'esecuzione di query [!INCLUDE[tsql](../../includes/tsql-md.md)] o batch. Un piano di esecuzione effettivo include quindi informazioni di runtime, ad esempio le metriche relative all'utilizzo effettivo delle risorse e gli avvisi sul runtime, se disponibili. Il piano di esecuzione generato visualizza il piano di esecuzione query effettivo usato da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] per eseguire le query.  
  
 Per utilizzare questa funzionalità, gli utenti devono disporre delle autorizzazioni appropriate per eseguire le query [!INCLUDE[tsql](../../includes/tsql-md.md)] per le quali viene generato un piano di esecuzione grafico e dell'autorizzazione SHOWPLAN per tutti i database a cui fa riferimento la query.  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a>Per includere un piano di esecuzione per una query durante l'esecuzione  
  
1.  Scegliere [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query del motore di database **nella barra degli strumenti**. Per aprire una query esistente e visualizzare il piano di esecuzione stimato, è anche possibile fare clic sul pulsante **Apri file** della barra degli strumenti e trovare la query. 
  
2.  Immettere la query per quale si desidera visualizzare il piano di esecuzione effettivo.  
  
3.  Scegliere **Includi piano di esecuzione effettivo** dal menu **Query** oppure fare clic sul pulsante della barra degli strumenti **Includi piano di esecuzione effettivo**  
  
4.  Fare clic sul pulsante della barra degli strumenti **Esegui** per eseguire la query. Il piano usato da Query Optimizer viene visualizzato nella scheda **Piano di esecuzione** del riquadro dei risultati. Posizionando il puntatore del mouse sugli operatori logici e fisici è possibile visualizzare una descrizione comando contenente la descrizione e le proprietà degli operatori.  
  
     In alternativa, è possibile visualizzare le proprietà dell'operatore nella finestra Proprietà. Se la finestra Proprietà non è visibile, fare clic con il pulsante destro del mouse su un operatore e scegliere **Proprietà**. Selezionare un operatore e visualizzare le relative proprietà.  
  
5.  È possibile modificare la visualizzazione del piano di esecuzione facendo clic con il pulsante destro del mouse sul piano di esecuzione e scegliendo **Zoom avanti**, **Zoom indietro**, **Personalizza zoom**oppure **Adatta alla finestra**. Le opzioni**Zoom avanti** e **Zoom indietro** consentono rispettivamente di ingrandire e rimpicciolire il piano di esecuzione, mentre **Personalizza zoom** consente di definire un fattore di zoom personalizzato, ad esempio 80 percento. **Adatta alla finestra** consente di ingrandire il piano di esecuzione per adattarlo al riquadro Risultati. In alternativa, usare una combinazione di tasto CTRL e rotellina del mouse per attivare lo **zoom dinamico**.  
  
 
 > [!NOTE] 
 > In alternativa, usare [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md) per restituire le informazioni del piano di esecuzione per ogni istruzione dopo l'esecuzione. Se usata in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], la scheda *Risultati* includerà un collegamento per l'apertura del piano di esecuzione in formato grafico.   
