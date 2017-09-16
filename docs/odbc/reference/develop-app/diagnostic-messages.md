---
title: I messaggi diagnostici | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic messages messages
- error messages [ODBC], diagnostic messages
- diagnostic messages [ODBC]
ms.assetid: 98027871-9901-476e-a722-ee58b7723c1f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ddec8b5d5f658e4f6119c1962d785232bf44d985
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="diagnostic-messages"></a>Messaggi di diagnostica
Con ogni SQLSTATE, viene restituito un messaggio di diagnostica. Il valore stesso SQLSTATE spesso viene restituito con un numero di messaggi diversi. SQLSTATE 42000 (sintassi o violazione di accesso), ad esempio, viene restituito per la maggior parte degli errori nella sintassi SQL. Tuttavia, ogni errore di sintassi problema può essere rappresentata da un altro messaggio.  
  
 I messaggi di diagnostica di esempio sono elencati nella colonna della tabella di SQLSTATE nell'appendice A e in ogni funzione di errore. Anche se i driver possono restituire questi messaggi, sono più probabile che venga restituito il messaggio viene passato a tali dall'origine dati.  
  
 Le applicazioni in genere visualizzano messaggi di diagnostica all'utente, insieme alla SQLSTATE e il codice di errore nativo. In questo modo l'utente e il personale di supporto determinano la causa di eventuali problemi. Le informazioni sul componente incorporati nel messaggio è particolarmente utile per eseguire questa operazione.  
  
 I messaggi diagnostici provengono da origini dati e i componenti di una connessione ODBC, ad esempio driver, gateway e di gestione Driver. In genere, le origini dati non supportano direttamente ODBC. Di conseguenza, se un componente in una connessione ODBC riceve un messaggio da un'origine dati, è necessario identificare l'origine dati come origine del messaggio. Inoltre deve identificarsi come componente che riceve il messaggio.  
  
 Se l'origine dell'errore o avviso, è un componente stesso, il messaggio di diagnostica deve spiegare ciò. Pertanto, il testo dei messaggi ha due formati diversi. Per errori e avvisi che non sono presenti in un'origine dati, il messaggio di diagnostica deve utilizzare questo formato:  
  
 **[** *identificatore fornitore* **] [** *ODBC-componente-identifier* **]** * testo immesso componente*  
  
 Per errori e avvisi che si verificano in un'origine dati, il messaggio di diagnostica deve utilizzare questo formato:  
  
 **[** *identificatore fornitore* **] [** *ODBC-componente-identifier* **] [** * Identificatore dell'origine dati* **]** *dati-fornito-testo di origine*  
  
 Nella tabella seguente viene illustrato il significato di ogni elemento.  
  
|Elemento|Significato|  
|-------------|-------------|  
|*Identificatore fornitore*|Identifica il fornitore del componente in cui si è verificato l'errore o avviso o che ha ricevuto l'errore o avviso direttamente dall'origine dati.|  
|*Identificatore di componenti ODBC*|Identifica il componente in cui si è verificato l'errore o avviso o che ha ricevuto l'errore o avviso direttamente dall'origine dati.|  
|*Identificatore dell'origine dati*|Identifica l'origine dati. Per i driver basati su file, si tratta in genere un formato di file, ad esempio driver basati su DBMS per Xbase [1], questo è il prodotto DBMS.|  
|*testo immesso componente*|Generato dal componente di ODBC.|  
|*dati-fornito-testo di origine*|Generato dall'origine dati.|  
  
 [1] In questo caso, il driver funge dal driver e l'origine dati.  
  
 Le parentesi quadre (**[]**) deve essere incluso nel messaggio e non indicano elementi facoltativi.
