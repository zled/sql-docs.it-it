---
title: Elaborazione di query intelligenti nei database Microsoft SQL | Microsoft Docs
description: Funzionalità di elaborazione di query intelligenti e miglioramento delle prestazioni delle query in SQL Server e nel database SQL di Azure.
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7786fd048f1698c90f379450b31e0bac3457706e
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455767"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Elaborazione di query intelligenti nei database SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

La famiglia di funzionalità di **elaborazione di query intelligenti** include funzionalità ad ampio spettro che migliorano le prestazioni di carichi di lavoro esistenti con il minimo sforzo dal punto di vista dell'implementazione.   Sono inclusi miglioramenti dei costrutti preesistenti e anche l'introduzione di metodi e funzionalità adattivi.  

## <a name="adaptive-query-processing"></a>Elaborazione di query adattive
La famiglia di funzionalità di elaborazione di query intelligenti include la famiglia di funzionalità di elaborazione di query adattive introdotta in SQL Server 2017 e nel database SQL di Azure. In generale, aggiungeva nuove funzionalità di elaborazione delle query che adattano le strategie di ottimizzazione alle condizioni di runtime del carico di lavoro dell'applicazione:
- **Join adattivi in modalità batch**. Questa funzionalità consente al piano di passare in modo dinamico a una strategia di join più efficace durante l'esecuzione di un singolo piano memorizzato nella cache.
- **Feedback delle concessioni di memoria in modalità batch**. Questa funzionalità ricalcola la memoria effettiva necessaria per una query e poi aggiorna il valore di concessione per il piano memorizzato nella cache, riducendo il numero eccessivo di concessioni che limita la concorrenza e correggendo il numero insufficiente di concessioni che causa costose distribuzioni su disco.
- **Esecuzione interleaved per funzioni con valori di tabella a più istruzioni**. Con l'esecuzione interleaved si usa il conteggio effettivo delle righe per adottare decisioni più mirate relativamente a un piano di query downstream. 

Per altre informazioni sull'elaborazione di query adattive, fare riferimento a [Elaborazione di query adattive nei database SQL](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="see-also"></a>Vedere anche
[Centro prestazioni per il motore di database di SQL Server e il database SQL di Azure](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md)    
[Guida di riferimento a operatori Showplan logici e fisici](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Join](../../relational-databases/performance/joins.md)    
[Demonstrating Adaptive Query Processing](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md) (Dimostrazione dell'elaborazione di query adattive)        
