---
title: Nuovo oggetto Stoplist Full-Text (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2304b2b9a8711210117ffbb2a84abbf167694e71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221971"
---
# <a name="new-full-text-stoplist-general-page"></a>Nuovo elenco di parole non significative full-text (pagina Generale)
  Utilizzare questa finestra di dialogo per creare un elenco di parole non significative full-text. Un *elenco di parole non significative* è un set di parole di uso comune, denominate *parole non significative*, omesse dall'indicizzazione full-text per tabelle che utilizzano l'elenco di parole non significative. Per altre informazioni, vedere [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md).  
  
 **Usare SQL Server Management Studio per creare un elenco di parole non significative**  
  
-   [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Opzioni  
 **Nome di parole non significative full-text**  
 Consente di immettere il nome dell'elenco di parole non significative full-text.  
  
 **Proprietario**  
 Consente di specificare il proprietario dell'elenco di parole non significative full-text. Se si desidera impostare se stessi, ovvero l'utente corrente, come proprietario, lasciare vuoto questo campo.  
  
 Per specificare un utente diverso, fare clic sul pulsante Sfoglia.  
  
### <a name="create-stoplist-options"></a>Opzioni di creazione di elenchi di parole non significative  
 Fare clic su una delle opzioni di creazione seguenti:  
  
 **Creare un elenco di parole non significative vuoto**  
 Il nuovo elenco di parole non significative non conterrà alcuna parola non significativa.  
  
 **Creare un elenco di parole non significative da un elenco di parole non significative di sistema**  
 Il nuovo elenco di parole non significative viene creato dall'elenco di parole non significative esistente per impostazione predefinita nel [Database Resource](../relational-databases/databases/resource-database.md).  
  
 **Creare un elenco di parole non significative da un elenco di parole non significative full-text esistente**  
 Il nuovo elenco di parole non significative viene creato copiando un elenco di parole non significative esistente.  
  
 **Database di origine**  
 Specifica il nome del database a cui appartiene l'elenco di parole non significative esistente. Per impostazione predefinita, è selezionato il database corrente. Se si desidera, selezionare un database diverso nella casella di riepilogo.  
  
 **Parole non significative di origine**  
 Specifica il nome di un elenco di parole non significative esistente. Nell'elenco di elenchi di parole non significative disponibili selezionare quello da utilizzare come origine. Gli elenchi di parole non significative disponibili sono elencati nell'ordine in cui vengono visualizzati in Esplora oggetti.  
  
 Se qualsiasi lingua specificata nelle parole non significative dell'elenco di parole non significative di origine non è registrata nel database corrente, CREATE FULLTEXT STOPLIST ha esito positivo, ma vengono restituiti avvisi e le parole non significative corrispondenti non vengono aggiunte.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
