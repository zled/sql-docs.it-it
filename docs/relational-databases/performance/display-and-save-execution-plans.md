---
title: Visualizzare e salvare piani di esecuzione | Microsoft Docs
ms.custom: 
ms.date: 08/21/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 014b531a94b555b8d12f049da1bd9eb749b4b0db
ms.openlocfilehash: 3eb1056b561e2fea455c29c2d5f72736564c1ffd
ms.contentlocale: it-it
ms.lasthandoff: 08/22/2017

---
# <a name="display-and-save-execution-plans"></a>Visualizzare e salvare piani di esecuzione
  In questa sezione viene illustrata la procedura di visualizzazione e di salvataggio dei piani di esecuzione in un file in formato XML utilizzando Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Nei piani di esecuzione sono visualizzate graficamente le modalità di recupero dei dati selezionate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Query Optimizer. I piani di esecuzione rappresentano il costo di esecuzione di istruzioni e query specifiche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite icone anziché tramite la rappresentazione di tabella generata dall'istruzione [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) o [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Questo approccio grafico è particolarmente utile per la comprensione delle caratteristiche relative alle prestazioni di una query.  

 Benché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Query Optimizer produca solo un piano di esecuzione, sono disponibili i concetti di piano di esecuzione **stimato** e piano di esecuzione **effettivo**.
 -  Un [piano di esecuzione stimato](../../relational-databases/performance/display-the-estimated-execution-plan.md) restituisce il piano di esecuzione prodotto da Query Optimizer in fase di compilazione. La produzione del piano di esecuzione stimato non comporta l'esecuzione effettiva della query o del batch e quindi non include alcuna informazione di runtime, ad esempio le metriche relative all'utilizzo effettivo delle risorse o avvisi sul runtime. 
 -  Un [piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md) restituisce il piano di esecuzione prodotto da Query Optimizer e successivo al completamento dell'esecuzione di query o batch. Il piano include informazioni di runtime sulle metriche relative all'utilizzo effettivo delle risorse e avvisi sul runtime.  

 Per altre informazioni, vedere [Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Visualizzazione del piano di esecuzione stimato](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Visualizzazione di un piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
-   [Salvataggio di un piano di esecuzione in formato XML](../../relational-databases/performance/save-an-execution-plan-in-xml-format.md)  
  
  

