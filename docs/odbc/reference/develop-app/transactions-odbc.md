---
title: Transazioni ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], about transactions
- transactions [ODBC]
ms.assetid: b4ca861a-c164-4e87-8672-d5de15e3823c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e6e18576f4898b6902d15ab20cc5ebfcb336835
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="transactions-odbc"></a>Transazioni ODBC
Oggetto *transazione* è un'unità di lavoro che viene eseguita come operazione atomica singola; vale a dire, l'operazione ha esito positivo o negativo nel suo complesso. Si consideri, ad esempio, il trasferimento di denaro da un conto bancario a un altro. Questa operazione comporta due passaggi: prelievo del denaro dal conto primo e il deposito al secondo. È importante che entrambi i passaggi esito positivo. non è accettabile per un passaggio abbia esito positivo e l'altro errore. Un database che supporta le transazioni è in grado di garantire questo.  
  
 Transazioni possono essere completate da Trova *commit* o *rollback*. Quando una transazione viene eseguito il commit, le modifiche apportate in una transazione vengono rese permanenti. Quando una transazione viene eseguito il rollback, le righe interessate vengono restituite lo stato in cui che si trovavano prima dell'avvio della transazione. Per estendere l'esempio di trasferimento di account, un'applicazione esegue un'istruzione SQL per il primo account di addebito e un'istruzione SQL diversa per il secondo account del credito. Se entrambe le istruzioni hanno esito positivo, quindi l'applicazione esegue il commit della transazione. Tuttavia, se l'istruzione non riesce per qualsiasi motivo, l'applicazione esegue il rollback della transazione. In entrambi i casi, l'applicazione garantisce uno stato coerente al termine della transazione.  
  
 Una singola transazione può includere più operazioni di database che si verificano in momenti diversi. Se altre transazioni fosse effettuare l'accesso ai risultati intermedi, le transazioni potrebbero interferire con altri. Ad esempio, si supponga che una transazione inserisce una riga, una seconda transazione legge di tale riga e la prima transazione viene eseguito il rollback. La seconda transazione ora dispone di dati per una riga che non esiste.  
  
 Per risolvere questo problema, sono disponibili vari schemi per isolare le transazioni uno da altro. *Isolamento delle transazioni* viene in genere implementato dal blocco di righe, che impedisce di più di una transazione utilizzando la stessa riga nello stesso momento. In alcuni database, il blocco di una riga può inoltre bloccare le altre righe.  
  
 Isolamento delle transazioni vengono ridotto *concorrenza,* o la possibilità di due transazioni di utilizzare gli stessi dati nello stesso momento. Per ulteriori informazioni, vedere [impostando il livello di isolamento](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Transazioni in ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Isolamento della transazione](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Controllo della concorrenza](../../../odbc/reference/develop-app/concurrency-control.md)
