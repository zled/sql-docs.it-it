---
title: "Definizione di durabilità per gli oggetti con ottimizzazione per la memoria | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d4f8bab5cfa0cc83737bb5736dfe4dcac84b8c13
ms.lasthandoff: 04/11/2017

---
# <a name="defining-durability-for-memory-optimized-objects"></a>Definizione di durabilità per gli oggetti con ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Per le tabelle con ottimizzazione per la memoria sono disponibili due opzioni di durabilità:  
  
 SCHEMA_AND_DATA (impostazione predefinita)  
 Questa opzione offre durabilità dello schema e dei dati. Il livello di durabilità dei dati dipende dall'eventuale scelta di eseguire il commit di una transazione come completamente durevole o con durabilità posticipata. Le transazioni completamente durevoli offrono la stessa garanzia di durabilità dei dati e dello schema, in modo analogo a una tabella basata su disco. La durabilità posticipata migliora le prestazioni ma può causare la perdita di dati in caso di un arresto anomalo del server o di failover. Per altre informazioni sulla durabilità ritardata, vedere [Controllo della durabilità delle transazioni](../../relational-databases/logs/control-transaction-durability.md).  
  
 SCHEMA_ONLY  
 Questa opzione assicura la durabilità dello schema della tabella. Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene riavviato oppure viene eseguita una riconfigurazione in un database SQL di Azure, lo schema della tabella persiste, ma i dati nella tabella vengono persi. Si tratta di un comportamento diverso da una tabella in tempdb, in cui sia la tabella che i dati vengono persi al riavvio. Uno scenario tipico per creare una tabella non durevole consiste nell'archiviare dati temporanei, ad esempio una tabella di gestione temporanea per un processo ETL. Una durabilità SCHEMA_ONLY evita la registrazione delle transazioni e i checkpoint, con una possibile riduzione significativa delle operazioni di I/O.  
  
 Quando si usano le tabelle SCHEMA_AND_DATA predefinite, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre le stesse garanzie di durabilità delle tabelle basate su disco:  
  
 Durabilità delle transazioni  
 Quando si esegue il commit di una transazione completamente durevole che ha apportato modifiche (DML o DDL) a una tabella con ottimizzazione per la memoria, le modifiche apportate a una tabella durevole con ottimizzazione per la memoria vengono rese permanenti.  
  
 Quando si esegue il commit di una transazione durevole posticipata a una tabella con ottimizzazione per la memoria, la transazione diventa durevole solo dopo che il log delle transazioni in memoria viene salvato su disco. Per altre informazioni sulla durabilità ritardata, vedere [Controllo della durabilità delle transazioni](../../relational-databases/logs/control-transaction-durability.md).  
  
 Durabilità al riavvio  
 Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene riavviato dopo un arresto anomalo o pianificato, viene ricreata un'istanza delle tabelle durevoli con ottimizzazione per la memoria per ripristinarne lo stato precedente all'arresto anomalo o pianificato.  
  
 Durabilità in caso di errori dei supporti  
 Se in un disco guasto o danneggiato sono presenti una o più copie persistenti di oggetti durevoli con ottimizzazione per la memoria, la funzionalità di backup e ripristino di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di ripristinare le tabelle con ottimizzazione per la memoria sul nuovo supporto.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
