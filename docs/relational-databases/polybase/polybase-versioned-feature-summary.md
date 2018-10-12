---
title: Funzionalità e limitazioni di PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 766d1ec31dda38993a4d5a66a70d56a132c4667c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848279"
---
# <a name="polybase-features-and-limitations"></a>Funzionalità e limitazioni di PolyBase

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

## <a name="known-limitations"></a>Limitazioni note

PolyBase include le limitazioni seguenti:

- Le dimensioni massime consentite per la riga, inclusa la lunghezza totale delle colonne di lunghezza variabile, non possono superare 32 KB in SQL Server o 1 MB in Azure SQL Data Warehouse.

- PolyBase non supporta il tipo di dati Hive 0.12+ (ovvero Char(), VarChar())

- In caso di esportazione di dati in un file in formato ORC da SQL Server o Azure SQL Data Warehouse le colonne contenenti molto testo possono essere limitate a un massimo di 50 colonne a causa degli errori Java di memoria insufficiente. Per risolvere questo problema, esportare solo un subset delle colonne.

- Impossibile leggere o scrivere i dati crittografati inattivi in Hadoop. Sono incluse le aree crittografate HDFS o la crittografia trasparente.

- PolyBase non può connettersi a un'istanza di Hortonworks se KNOX è abilitata.

- Se si usano tabelle Hive con transactional=true, PolyBase non può accedere ai dati nella directory della tabella Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase non viene installato quando si aggiunge un nodo a un cluster di failover di SQL Server 2016](https://support.microsoft.com/en-us/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end

- Da definire: Larghezza riga
- Da definire: Mapping dei tipi
- Da definire: Autenticazione
- Da definire: Regole di confronto 
- Da definire: Distribuzione  

## <a name="security-and-authentication"></a>Sicurezza e autenticazione 

## <a name="see-also"></a>Vedere anche  

[Guida a PolyBase](../../relational-databases/polybase/polybase-guide.md)  
