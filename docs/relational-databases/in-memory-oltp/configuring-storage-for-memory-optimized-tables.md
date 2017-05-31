---
title: Configurazione dell&quot;archiviazione per le tabelle con ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0250c8370960dc17adf13c020c51bfc603b111c8
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="configuring-storage-for-memory-optimized-tables"></a>Configurazione dell'archiviazione per le tabelle con ottimizzazione per la memoria
  È necessario configurare la capacità di archiviazione e le operazioni di input/output al secondo (IOPS).  
  
## <a name="storage-capacity"></a>Capacità di archiviazione  
 Usare le informazioni in [Stimare i requisiti di memoria delle tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) per stimare le dimensioni in memoria delle tabelle con ottimizzazione per la memoria durevoli del database. Poiché gli indici non vengono mantenuti per le tabelle con ottimizzazione per la memoria, non includere le dimensioni degli indici. Una volta determinata la dimensione, è necessario fornire uno spazio libero su disco quattro volte superiore alla dimensione delle tabelle in memoria durevoli.  
  
## <a name="storage-iops"></a>IOPS di archiviazione  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] consente di aumentare notevolmente la velocità effettiva del carico di lavoro. Pertanto, è importante verificare che le operazioni di IO non rappresentino un collo di bottiglia.  
  
-   Quando si esegue la migrazione delle tabelle basate su disco nelle tabelle con ottimizzazione per la memoria, verificare che il log delle transazioni sia in un supporto di archiviazione che supporti l'attività aumentata del log delle transazioni. Ad esempio, se il supporto di archiviazione supporta le operazioni del log delle transazioni a 100 MB/sec e le tabelle con ottimizzazione per la memoria restituiscono prestazioni cinque volte superiori, anche il supporto di archiviazione del log delle transazioni deve essere in grado di supportare un incremento di cinque volte delle prestazioni, per impedire all'attività del log delle transazioni di diventare un collo di bottiglia.  
  
-   Le tabelle con ottimizzazione per la memoria sono persistenti nei file distribuiti in uno o più contenitori. In genere è necessario eseguire il mapping di ogni contenitore al relativo spindle, che consente di aumentare la capacità di archiviazione e migliorare gli IOPS. È necessario assicurarsi che le operazioni di IOPS sequenziali del supporto di archiviazione possono supportare un aumento pari a 3 volte la velocità effettiva del log delle transazioni.  
  
     Ad esempio, se le tabelle con ottimizzazione per la memoria generano 500 MB/sec di attività nel log delle transazioni, l'archiviazione per le tabelle con ottimizzazione per la memoria deve supportare IOPS da 1,5 GB/sec. La necessità di supportare un aumento pari a 3 volte la velocità effettiva del log delle transazioni deriva dall'analisi che le coppie di file di dati e differenziali vengono prima scritti con dati iniziali e quindi devono essere letti e riscritti come parte di un'operazione di merge.  
  
     Un altro fattore per stimare gli IOPS per l'archiviazione è il tempo di recupero per le tabelle con ottimizzazione per la memoria. I dati delle tabelle durevoli devono essere letti in memoria prima che un database viene reso disponibile alle applicazioni. In genere, il caricamento dei dati nelle tabelle con ottimizzazione per la memoria può essere eseguito alla velocità delle operazioni di IOPS. Pertanto se l'archiviazione totale per le tabelle con ottimizzazione per la memoria durevoli è di 60 GB e si desidera essere in grado di caricare i dati in 1 minuto, le operazioni di IOPS per l'archiviazione devono essere impostati su 1 GB/sec.  
  
-   Se il numero di spindle è pari, a differenza di SQL Server 2014 i file del checkpoint vengono distribuiti in modo uniforme tra tutti gli spindle.  
  
## <a name="encryption"></a>Crittografia  
 In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] lo spazio di archiviazione per le tabelle con ottimizzazione per la memoria viene crittografato come parte dell'abilitazione di Transparent Data Encryption nel database. Per altre informazioni, vedere [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption-tde.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
