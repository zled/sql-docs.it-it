---
title: Esecuzione del commit e rollback delle transazioni | Documenti Microsoft
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
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- transactions [ODBC], committing
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4090e609063b74fdcbef694c400272ee6af090c5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="committing-and-rolling-back-transactions"></a>Esecuzione del commit e rollback delle transazioni
Per eseguire il commit o rollback della transazione in modalità di commit manuale, un'applicazione chiama **SQLEndTran**. I driver per DBMS che supportano le transazioni in genere implementano questa funzione tramite l'esecuzione di un **COMMIT** o **ROLLBACK** istruzione. Gestione Driver non chiama **SQLEndTran** quando la connessione è in modalità autocommit; semplicemente restituisce SQL_SUCCESS, anche se l'applicazione tenta di eseguire il rollback della transazione. Poiché i driver per DBMS che non supportano le transazioni sono sempre in modalità di commit automatico, è possibile implementare **SQLEndTran** restituisce SQL_SUCCESS senza eseguire alcuna operazione o non implementare.  
  
> [!NOTE]  
>  Le applicazioni non devono eseguire il commit o il rollback delle transazioni eseguendo **COMMIT** o **ROLLBACK** istruzioni con **SQLExecute** o **SQLExecDirect**. Non sono definiti gli effetti di questa operazione. I problemi possibili includono il driver non sapere quando è attiva una transazione e tali istruzioni non superati rispetto a origini dati che non supportano le transazioni. Queste applicazioni devono chiamare **SQLEndTran** invece.  
  
 Se l'applicazione passa l'handle di ambiente per **SQLEndTran** ma non chiama concettualmente non passare un handle di connessione, gestione Driver **SQLEndTran** con l'handle di ambiente per ogni driver che dispone di uno o più connessioni attive nell'ambiente. Il driver quindi esegue il commit delle transazioni in ogni connessione nell'ambiente. Tuttavia, è importante tenere presente che il driver né the Driver Manager esegue un commit a due fasi per le connessioni dell'ambiente. si tratta semplicemente un facilitare la programmazione contemporaneamente chiamare **SQLEndTran** per tutte le connessioni nell'ambiente.  
  
 (A *commit in due fasi* viene generalmente usato per eseguire il commit delle transazioni che sono distribuite in più origini dati. Nella prima fase, le origini dati sono sottoposti a polling per che possono eseguire il commit di propria parte della transazione. Nella seconda fase, la transazione viene effettivamente eseguito il commit in tutte le origini dati. Se tutte le origini dati risponde nella prima fase, che è Impossibile eseguire il commit della transazione, la seconda fase non viene eseguito.)
