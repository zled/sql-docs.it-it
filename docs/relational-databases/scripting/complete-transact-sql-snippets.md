---
title: Completare frammenti di Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8e1793b4d6987dbb40d1370855f51394d325d0a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="complete-transact-sql-snippets"></a>Completare frammenti di Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Dopo aver inserito un frammento di codice [!INCLUDE[tsql](../../includes/tsql-md.md)] in uno script, è necessario modificare il contenuto del frammento per compilare un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] completa.  
  
## <a name="completing-snippets"></a>Completamento di frammenti  
 Quando si aggiunge un frammento [!INCLUDE[tsql](../../includes/tsql-md.md)] allo script, l'istruzione del frammento inserito include uno o più punti di sostituzione, evidenziati. Se si posiziona il puntatore del mouse su un punto di sostituzione, viene visualizzata una descrizione comando con una descrizione dell'elemento di sintassi che è possibile specificare. L'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] riconosce il frammento come separato dallo script circostante fino a quando non si chiude il file di origine. I punti di sostituzione rimangono attivi fino a quando non si chiude il file di origine.  
  
 È inoltre possibile aggiungere altri elementi di sintassi al codice del modello inserito da un frammento. Il modello di frammento Crea tabella, ad esempio, genera due definizioni di colonna. È necessario aggiungere altre definizioni di colonna per creare una tabella con più di due colonne.  
  
#### <a name="completing-the-snippet-statement"></a>Completamento dell'istruzione del frammento  
  
1.  Utilizzare il tasto TAB per spostarsi da un punto di sostituzione al successivo. Utilizzare MAIUSC+TAB per spostarsi al punto di sostituzione precedente.  
  
2.  Premere CTRL+BARRA SPAZIATRICE per richiamare IntelliSense.  
  
3.  Selezionare un elemento nell'elenco o digitare una sostituzione desiderata.  
  
## <a name="see-also"></a>Vedere anche  
 [Inserimento di frammenti di Transact-SQL](../../relational-databases/scripting/insert-transact-sql-snippets.md)   
 [Inserimento di frammenti Transact-SQL racchiusi](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  
