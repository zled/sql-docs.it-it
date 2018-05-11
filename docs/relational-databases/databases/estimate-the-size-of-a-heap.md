---
title: Stimare le dimensioni di un heap | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- estimating heap size
- size [SQL Server], heap
- space [SQL Server], indexes
- heaps
ms.assetid: 81fd5ec9-ce0f-4c2c-8ba0-6c483cea6c75
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f07c117f34944526381e7695b59ac4d2ed2d4cf1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="estimate-the-size-of-a-heap"></a>Stima delle dimensioni di un heap
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  I seguenti passaggi sono utilizzabili per valutare la quantità di spazio necessaria per l'archiviazione dei dati in un heap:  
  
1.  Specificare il numero di righe che verranno incluse nella tabella:  
  
     ***Num_Rows***  = numero di righe della tabella  
  
2.  Specificare il numero di colonne di lunghezza fissa e e variabile e calcolare lo spazio necessario per la loro archiviazione:  
  
     Calcolare lo spazio occupato da ognuno di questi gruppi di colonne all'interno della riga di dati. Le dimensioni di una colonna dipendono dal tipo di dati e dalla lunghezza specificata.  
  
     ***Num_Cols***  = numero totale di colonne (a lunghezza fissa e a lunghezza variabile)  
  
     ***Fixed_Data_Size***  = dimensioni totali in byte di tutte le colonne a lunghezza fissa  
  
     ***Num_Variable_Cols***  = numero di colonne a lunghezza variabile  
  
     ***Max_Var_Size***  = dimensioni massime totali in byte di tutte le colonne a lunghezza variabile  
  
3.  Parte della riga, nota come mappa di bit null, è riservata alla gestione del supporto dei valori Null in una colonna. Calcolarne le dimensioni:  
  
     ***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)  
  
     Solo l'integrale di questa espressione dovrebbe essere utilizzato. Eliminare le parti restanti.  
  
4.  Calcolare le dimensioni dei dati di lunghezza variabile:  
  
     Se la tabella include colonne di lunghezza variabile, determinare la quantità di spazio utilizzata per l'archiviazione delle colonne nella riga:  
  
     ***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***  
  
     I byte aggiunti a ***Max_Var_Size*** servono a tenere traccia di ogni colonna a lunghezza variabile. Questa formula si basa sul presupposto che tutte le colonne a lunghezza variabile siano piene al 100%. Se si prevede una percentuale inferiore di utilizzo dello spazio di archiviazione delle colonne a lunghezza variabile, è possibile modificare il valore di ***Max_Var_Size*** in base a tale percentuale per ottenere una stima più accurata delle dimensioni complessive della tabella.  
  
    > [!NOTE]  
    >  È possibile combinare colonne **varchar**, **nvarchar**, **varbinary**o **sql_variant** che causano il superamento del limite di 8.060 byte previsto per la larghezza totale definita della tabella. La lunghezza di ogni colonna deve essere compresa nel limite di 8.000 byte per una colonna **varchar**, **nvarchar,****varbinary**o **sql_variant** . Le larghezze combinate di tali colonne possono tuttavia superare il limite di 8.060 byte in una tabella.  
  
     Se non sono disponibili colonne di lunghezza variabile, impostare ***Variable_Data_Size*** su 0.  
  
5.  Calcolare le dimensioni totali della riga:  
  
     ***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4  
  
     Il valore 4 nel formula è l'overhead dell'intestazione di riga della riga di dati.  
  
6.  Calcolare il numero di righe per pagina (8096 byte liberi per pagina):  
  
     ***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)  
  
     Poiché le righe non si estendono su più pagine, il numero di righe per pagina deve essere arrotondato alla riga completa più vicina. Il valore 2 nella formula è per la voce di riga nella matrice di slot della pagina.  
  
7.  Calcolare il numero di pagine necessario per archiviare tutte le righe:  
  
     ***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***  
  
     Il numero di pagine stimato deve essere arrotondato alla pagina intera più vicina.  
  
8.  Infine, calcolare la quantità di spazio necessaria per archiviare i dati nell'heap (8192 byte totali per pagina):  
  
     Dimensioni dell'heap (byte) = 8192 x ***Num_Pages***  
  
 Il calcolo non prende in considerazione i fattori seguenti:  
  
-   Partizionamento  
  
     L'overhead dello spazio derivante dal partizionamento è minimo, ma difficile da calcolare. Non è fondamentale includerlo.  
  
-   Pagine di allocazione  
  
     Esiste almeno una pagina IAM utilizzata per tenere traccia delle pagine allocate su un heap, ma l'overhead dello spazio è minimo e non è presente alcun algoritmo per calcolare in modo deterministico l'esatto numero di pagine IAM che verranno utilizzate.  
  
-   Valori LOB  
  
     L'algoritmo per determinare con esattezza la quantità di spazio usata per archiviare i tipi di dati LOB **varchar(max)**, **varbinary(max)**, **nvarchar(max)**, **text**, **ntextxml**e **image** è complesso. È sufficiente aggiungere soltanto le dimensioni medie dei valori LOB previsti e aggiungerle alle dimensioni totali dell'heap.  
  
-   Compressione  
  
     Non è possibile pre-calcolare la dimensione di un heap compresso.  
  
-   Colonne di tipo sparse  
  
     Per informazioni sui requisiti di spazio delle colonne di tipo sparse, vedere [Utilizzo di colonne di tipo sparse](../../relational-databases/tables/use-sparse-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Heap &#40;tabelle senza indici cluster&#41;](../../relational-databases/indexes/heaps-tables-without-clustered-indexes.md)   
 [Descrizione di indici cluster e non cluster.](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)   
 [Creare indici cluster](../../relational-databases/indexes/create-clustered-indexes.md)   
 [Creare indici non cluster](../../relational-databases/indexes/create-nonclustered-indexes.md)   
 [Stima delle dimensioni di una tabella](../../relational-databases/databases/estimate-the-size-of-a-table.md)   
 [Stima delle dimensioni di un indice cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Stima delle dimensioni di un indice non cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)   
 [Stima delle dimensioni di un database](../../relational-databases/databases/estimate-the-size-of-a-database.md)  
  
  
