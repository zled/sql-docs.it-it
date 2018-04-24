---
title: Inserimento e aggiornamento di dati in una tabella (esercitazione) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 407b1c470f691de3c6165cddfe1252afc6e44da9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="lesson-1-3---inserting-and-updating-data-in-a-table"></a>Lezione 1-3 - Inserimento e aggiornamento dei dati in una tabella
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Dopo aver creato la tabella **Products** è possibile inserirvi dati con l'istruzione INSERT. Dopo aver inserito i dati, si procederà alla modifica del contenuto di una riga mediante l'istruzione UPDATE. Per limitare l'operazione di aggiornamento a una sola riga verrà utilizzata la clausola WHERE dell'istruzione UPDATE. Le quattro istruzioni immetteranno i dati seguenti.  
  
|ProductID|ProductName|Price|ProductDescription|  
|-------------|---------------|---------|----------------------|  
|1|Clamp|12.48|Workbench clamp|  
|50|Screwdriver|3.17|Flat head|  
|75|Tire Bar||Tool for changing tires.|  
|3000|3mm Bracket|.52||  
  
La sintassi di base è INSERT, nome tabella, elenco colonne, VALUES, a cui segue quindi un elenco dei valori da inserire. I due trattini davanti a una riga indicano che si tratta di un commento il cui testo verrà ignorato dal compilatore. In questo caso il commento descrive una variazione consentita della sintassi.  
  
### <a name="to-insert-data-into-a-table"></a>Per inserire dati in una tabella  
  
1.  Eseguire l'istruzione seguente per inserire una riga nella tabella `Products` creata nell'attività precedente. Viene utilizzata la sintassi di base.  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  L'istruzione seguente illustra come modificare l'ordine in cui vengono specificati i parametri scambiando la posizione di `ProductID` e `ProductName` in entrambi gli elenchi di campi (tra parentesi) e nell'elenco dei valori.  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  L'istruzione seguente illustra che i nomi delle colonne sono facoltativi a condizione che i valori siano elencati nell'ordine corretto. Questa sintassi comune non è tuttavia consigliata poiché potrebbe rendere il codice di difficile comprensione per gli altri utenti. `NULL` viene specificato per la colonna `Price` perché il prezzo del prodotto corrispondente non è ancora noto.  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  Il nome dello schema è facoltativo a condizione che si acceda per la modifica a una tabella inclusa nello schema predefinito. Poiché la colonna `ProductDescription` supporta valori Null e non viene specificato alcun valore, il nome e il valore della colonna `ProductDescription` verranno eliminati completamente dall'istruzione.  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a>Per aggiornare la tabella Products  
  
1.  Digitare ed eseguire l'istruzione `UPDATE` seguente per modificare il valore `ProductName` del secondo prodotto da `Screwdriver`in `Flat Head Screwdriver`.  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Lettura dei dati di una tabella &#40;Esercitazione&#41;](../t-sql/lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a>Vedere anche  
[INSERT &#40;Transact-SQL&#41;](../t-sql/statements/insert-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../t-sql/queries/update-transact-sql.md)  
  
  
  
