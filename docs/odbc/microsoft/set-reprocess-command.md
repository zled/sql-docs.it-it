---
title: Comando RIELABORAZIONE SET | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SET REPROCESS command [ODBC]
ms.assetid: b0708757-b1d7-42f3-8988-787f2a806b8b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba3689fb9d70418d546d9583a537b2112a65a71b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="set-reprocess-command"></a>Comando RIELABORAZIONE SET
Specifica quante volte o per informazioni su come long per bloccare un file o un record dopo un tentativo di blocco non riuscito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>Argomenti  
 PER *nAttempts*[SECONDS]  
 Specifica il numero di volte o il numero di secondi di tenta di bloccare un file o un record dopo il tentativo iniziale non riuscito. Il valore predefinito è 0. il valore massimo è 32.000.  
  
 SECONDI specifica che Visual FoxPro tenta di bloccare un file o record per *nAttempts* secondi. È disponibile solo quando *nAttempts* è maggiore di zero.  
  
 Ad esempio, se *nAttempts* è 30, Visual FoxPro tenta di bloccare un record o il file fino a 30 volte. Se si includono inoltre (impostare RIELABORARE a 30 secondi), Visual FoxPro tenterà continuamente di bloccare un record o un file per un massimo di 30 secondi.  
  
 Se una routine ON ERROR è attiva e se da un comando per bloccare il record o il file tentativo, viene eseguita la routine ON ERROR. Tuttavia, se una funzione tenta il blocco, non viene eseguita una routine di errore ON e la funzione restituisce False (. F.).  
  
 Se una routine di errore ON non è attivo, un comando tenta di bloccare il record o il file e non è possibile inserire il blocco, viene generato un errore. Se una funzione tenta di inserire il blocco, non viene visualizzato l'avviso e la funzione restituisce False (. F.).  
  
 Se *nAttempts* è 0 (valore predefinito) e si esegue un comando o una funzione che tenta di bloccare un record o un file, Visual FoxPro tenta di bloccare il record o il file per un periodo illimitato. Se il record o il file diventa disponibile per il blocco durante l'attesa, viene inserito il blocco e il messaggio di sistema viene cancellato. Se una funzione ha tentato di inserire il blocco, la funzione restituisce True (. T.).  
  
 Se una routine ON ERROR è attiva e un comando sta tentando di bloccare il record o un file, la routine ON ERROR ha la precedenza su ulteriori tentativi di bloccare il record o un file. La routine ON ERROR viene eseguita immediatamente. Visual FoxPro non tenta di record aggiuntivi o blocchi di file e non visualizza il messaggio di sistema.  
  
 Se *nAttempts* è 1, Visual FoxPro tenta di bloccare il record o il file per un periodo illimitato e non viene eseguita una routine ON ERROR.  
  
 Se un blocco è stato inserito da un altro utente per il record o un file che si sta tentando di bloccare, è necessario attendere fino a quando l'utente rilascia il blocco.  
  
 SU AUTOMATICO  
 Specifica che Visual FoxPro tenta di bloccare il record o il file per un periodo illimitato. (SET di RIELABORAZIONE per -2 è un comando equivalente).  
  
## <a name="remarks"></a>Osservazioni  
 Al primo tentativo di bloccare un record o un file non è sempre esito positivo. Spesso, un record o un file è bloccato da un altro utente nella rete. IMPOSTARE RIELABORARE determina se Visual FoxPro esegue ulteriori tentativi per bloccare il record o il file durante il tentativo iniziale ha esito negativo. È possibile specificare il numero di tentativi eseguiti altri tentativi vengono apportati o per quanto tempo i tentativi vengono stabiliti. Una routine ON ERROR influisce sulla riuscita come blocco vengono gestiti i tentativi.
