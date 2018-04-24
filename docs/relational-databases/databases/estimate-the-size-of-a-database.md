---
title: Stimare le dimensioni di un database | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 180e6a5d6c74a8a2859c6f30566f113d3c14f771
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="estimate-the-size-of-a-database"></a>Stima delle dimensioni di un database
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Durante la progettazione di un database potrebbe essere necessario stimare le dimensioni che il database può raggiungere quando viene riempito di dati. La stima delle dimensioni del database può consentire di determinare la configurazione hardware necessaria per raggiungere gli obiettivi seguenti:  
  
-   Ottenere il livello di prestazioni necessario per eseguire correttamente le applicazioni.  
  
-   Assegnare la quantità di spazio su disco appropriata per l'archiviazione dei dati e degli indici.  
  
 La stima delle dimensioni del database consente inoltre di determinare se è necessario ottimizzare la struttura del database. Ad esempio, si potrebbe determinare che le dimensioni del database stimate sono troppo grandi per implementarlo nell'organizzazione e che è necessaria una maggiore normalizzazione. Al contrario, le dimensioni potrebbero essere inferiori a quanto previsto e ciò consentirebbe di denormalizzare il database per ottimizzare le prestazioni delle query.  
  
 Per stimare le dimensioni del database, è possibile stimare le dimensioni di ogni singola tabella e quindi sommare i valori ottenuti. Le dimensioni di una tabella dipendono dalla presenza o meno di indici e dal tipo di indici.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Stima delle dimensioni di una tabella](../../relational-databases/databases/estimate-the-size-of-a-table.md)|Definisce i passaggi e i calcoli necessari per stimare la quantità di spazio necessaria per archiviare i dati in una tabella e gli indici associati.|  
|[Stima delle dimensioni di un heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md)|Definisce i passaggi e i calcoli necessari per stimare la quantità di spazio necessaria per archiviare i dati in un heap, ovvero in una tabella per cui non è disponibile un indice cluster.|  
|[Stima delle dimensioni di un indice cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)|Definisce i passaggi e i calcoli necessari per stimare la quantità di spazio necessaria per archiviare i dati in un indice cluster.|  
|[Stima delle dimensioni di un indice non cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)|Definisce i passaggi e i calcoli necessari per stimare la quantità di spazio necessaria per archiviare i dati in un indice non cluster.|  
  
  
