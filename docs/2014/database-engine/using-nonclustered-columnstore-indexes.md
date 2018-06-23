---
title: Utilizzo di indici Columnstore non cluster | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.openlocfilehash: fd711b644c551da7a658eff7ede74007d69a2286
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068091"
---
# <a name="using-nonclustered-columnstore-indexes"></a>Utilizzo di indici columnstore non cluster
  Vengono descritte le attività principali per l'utilizzo di un indice columnstore non cluster in una tabella di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Per una panoramica degli indici columnstore, vedere [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Per informazioni sugli indici columnstore cluster, vedere [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Sommario  
  
-   [Creare un indice Columnstore non cluster](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)  
  
-   [Modificare i dati in un indice Columnstore non cluster](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)  
  
##  <a name="load"></a> Creare un indice Columnstore non cluster  
 Per caricare dati in un indice columnstore non cluster, caricare innanzitutto i dati in una tabella rowstore tradizionale archiviata come heap o cluster di indice e quindi utilizzare [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) per creare un indice ColumnStore.  
  
 ![Il caricamento dei dati in un indice columnstore](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "il caricamento dei dati in un indice columnstore")  
  
##  <a name="change"></a> Modificare i dati in un indice Columnstore non cluster  
 Dopo aver creato un indice columnstore non cluster in una tabella, non è possibile modificare i dati direttamente nella tabella. Se si esegue una query con INSERT, UPDATE, DELETE o MERGE viene restituito un messaggio di errore. Per aggiungere o modificare i dati nella tabella, è possibile effettuare una delle operazioni seguenti:  
  
-   Disabilitare l'indice columnstore. È possibile aggiornare i dati nella tabella. Se si disabilita l'indice columnstore, è possibile ricompilare l'indice columnstore al termine dell'aggiornamento dei dati. Esempio:  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Eliminare l'indice columnstore, aggiornare la tabella e quindi ricreare l'indice columnstore con CREATE COLUMNSTORE INDEX. Esempio:  
  
    ```  
    DROP INDEX mycolumnstoreindex ON mytable  
    -- update mytable --  
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;  
  
    ```  
  
-   Caricare i dati in una tabella di staging che non dispone di un indice columnstore. Compilare un indice columnstore nella tabella di staging. Passare la tabella di staging in una partizione vuota della tabella principale.  
  
-   Passare una partizione della tabella con l'indice columnstore in una tabella di staging vuota. Se è presente un indice columnstore nella tabella di staging, disabilitare l'indice columnstore. Eseguire gli aggiornamenti. Compilare o ricompilare l'indice columnstore. Passare la tabella di staging nuovamente nella partizione (ora vuota) della tabella principale.  
  

  
  
