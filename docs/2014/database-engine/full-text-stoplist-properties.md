---
title: Le proprietà di parole non significative Full-Text | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1b052e1987c120bb621da34c6f56d915333baf83
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055554"
---
# <a name="full-text-stoplist-properties"></a>Proprietà elenco di parole non significative full-text
  Utilizzare questa finestra di dialogo per aggiungere o eliminare singole parole non significative, eliminare tutte le parole non significative per una lingua specifica oppure cancellare l'elenco di parole non significative corrente. Una parola non significativa è una parola di uso comune inclusa in un elenco di parole non significative. Le parole contenute in un elenco di questo tipo vengono omesse dall'indicizzazione full-text nelle tabelle che utilizzano l'elenco stesso. Per altre informazioni, vedere [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md).  
  
 **Per utilizzare SQL Server Management Studio per modificare le proprietà di parole non significative**  
  
-   [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Opzioni  
 **Azione**  
 Consente di specificare l'azione che si desidera eseguire.  
  
 **Aggiungi parola non significativa**  
 Consente di aggiungere una parola di uso comune all'elenco di parole non significative.  
  
 **Elimina parola non significativa**  
 Consente di eliminare una parola non significativa dall'elenco.  
  
 **Eliminare tutte le parole non significative**  
 Consente di eliminare tutte le parole non significative per una lingua specifica.  
  
 **Cancella elenco di parole non significative**  
 Consente di cancellare l'elenco di parole non significative eliminando tutte le parole non significative per tutte le lingue.  
  
 **Parola non significativa**  
 Se è stato selezionato **Aggiungi parola non significativa** oppure **Elimina parola non significativa**, immettere la parola non significativa nel **parola non significativa** campo. Una nuova parola non significativa deve essere univoca, ovvero non ancora inclusa nell'elenco di parole non significative per la lingua selezionata.  
  
 **Lingua full-text**  
 Se è stato selezionato **Aggiungi parola non significativa**, **Elimina parola non significativa**, o **eliminare tutte le parole non significative**, selezionare la lingua della parola non significativa o le parole non significative nella casella di riepilogo. Nella casella sono elencate tutte le lingue full-text supportate dall'istanza del server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)   
 [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md)   
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
