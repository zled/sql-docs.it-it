---
title: "Riepilogo delle funzionalità con controllo delle versioni di PolyBase | Microsoft Docs"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: polybase
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff2d8cb28ff4d1ae4960d183ce73524ecf24d7d3
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="polybase-versioned-feature-summary"></a>PolyBase Versioned Feature Summary (Riepilogo delle funzionalità con controllo delle versioni di PolyBase)
[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]
Riepilogo delle funzionalità di PolyBase disponibili per i prodotti e servizi di SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Riepilogo delle funzionalità per le versioni dei prodotti  
 Questa tabella riepiloga le funzionalità principali per PolyBase e i prodotti in cui sono disponibili.  
  
||||||
|-|-|-|-|-|   
|**Funzionalità**|**SQL Server 2016**|**Database SQL di Azure**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Eseguire query sui dati di Hadoop con [!INCLUDE[tsql](../../includes/tsql-md.md)]|sì|no|no|sì|
|Importare dati da Hadoop|sì|no|no|sì|
|Esportare dati in Hadoop  |sì|no|no| sì|
|Eseguire query, importare da ed esportare in HDInsights |no|no|no|no
|Eseguire il push down dei calcoli delle query in Hadoop|sì|no|no|sì|  
|Importare dati dall'archivio BLOB di Azure|sì|no|sì|sì| 
|Esportare dati nell'archivio BLOB di Azure|sì|no|sì|sì|  
|Importare dati da Azure Data Lake Store|no|no|sì|no|    
|Esportare dati da Azure Data Lake Store|no|no|sì|no|
|Eseguire query PolyBase da strumenti di Business Intelligence di Microsoft|sì|no|sì|sì|   


## <a name="pushdown-computation-supported-t-sql-operators"></a>Operatori T-SQL supportati per il calcolo della distribuzione dinamica
In SQL Server e APS, non tutti gli operatori T-SQL possono essere distribuiti sul cluster hadoop. Nella tabella seguente sono elencati tutti gli operatori supportati e un subset degli operatori non supportati. 

||||
|-|-|-| 
|**Tipo di operatore**|**Distribuibile su hadoop**|**Distribuibile nell'archiviazione BLOB**|
|Proiezioni di colonna|sì|no|
|Predicati|sì|no|
|Aggregazioni|parziale|no|
|Crea un join tra le tabelle esterne|no|no|
|Crea un join tra le tabelle esterne e locali|no|no|
|Ordina|no|no|

Aggregazione parziale significa che deve verificarsi un'aggregazione finale una volta che i dati raggiungono SQL Server, ma che si verifica una parte dell'aggregazione in Hadoop. Si tratta di un metodo comune di calcolo delle aggregazioni nei sistemi con la funzionalità di elaborazione parallela massiva.  
## <a name="see-also"></a>Vedere anche  
 [Guida a PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  
