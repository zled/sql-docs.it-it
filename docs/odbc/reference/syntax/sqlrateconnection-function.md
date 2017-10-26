---
title: Funzione SQLRateConnection | Documenti Microsoft
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
- SQLRateConnection function [ODBC]
ms.assetid: e8da2ffb-d6ef-4ca7-824f-57afd29585d8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e63a6312a6f4b637d13282e25311204ea3879fd5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlrateconnection-function"></a>SQLRateConnection (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 3,81 conformità: ODBC  
  
 **Riepilogo**  
 **SQLRateConnection** determina se un driver può riutilizzare una connessione esistente nel pool di connessioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SQLRETURN  SQLRateConnection(  
                SQLHDBC_INFO_TOKEN   hRequest,  
                SQLHDBC              hCandidateConnection,  
                BOOL                 fRequiredTransactionEnlistment,  
                TRANSID              transId,  
                DWORD *              pRating );  
```  
  
## <a name="arguments"></a>Argomenti  
 *hRequest*  
 [Input] Handle di token che rappresenta la nuova richiesta di connessione dell'applicazione.  
  
 *hCandidateConnection*  
 [Input] La connessione esistente nel pool di connessioni. La connessione deve essere in uno stato aperto.  
  
 *fRequiredTransactionEnlistment*  
 [Input] Se TRUE, il riutilizzo della connessione esistente *hCandidateConnection* per la nuova richiesta di connessione (*hRequest*) richiede un'integrazione aggiuntiva.  
  
 *ID transazione*  
 [Input] Se *fRequiredTransactionEnlistment* è TRUE, *ID transazione* rappresenta la transazione DTC che la richiesta verrà inserita. Se *fRequiredTransactionEnlistment* è FALSE, *ID transazione* verrà ignorato.  
  
 *pRating*  
 [Output] *hCandidateConnection*punteggio per il riutilizzo di *hRequest*. Questa valutazione sarà compreso tra 0 e 100 (inclusivo).  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS o SQL_ERROR, SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Gestione Driver non elaborerà le informazioni di diagnostica restituite dalla funzione.  
  
## <a name="remarks"></a>Osservazioni  
 **SQLRateConnection** produce un punteggio compreso tra 0 e 100 che indica come anche una connessione esistente corrisponde alla richiesta (incluso).  
  
|Punteggio|Significato (quando viene restituito SQL_SUCCESS)|  
|-----------|-----------------------------------------------|  
|0|*hCandidateConnection* non devono essere riutilizzate per le *hRequest*.|  
|Qualsiasi valore compreso tra 1 e 98 (inclusivo)|Maggiore il punteggio, più vicina che *hCandidateConnection* corrisponde a *hRequest*.|  
|99|Sono disponibili solo le mancate corrispondenze negli attributi non significativi.  Gestione Driver deve interrompere il ciclo di valutazione.|  
|100|Corrispondenza esatta.  Gestione Driver deve interrompere il ciclo di valutazione.|  
|Qualsiasi valore maggiore di 100|*hCandidateConnection* è contrassegnata come inattiva e non verrà riutilizzate anche in una richiesta di connessione future.|  
  
 Gestione Driver verranno contrassegnate come una connessione come inattivi se il codice restituito è diverso da SQL_SUCCESS (inclusi SQL_SUCCESS_WITH_INFO) o la classificazione è maggiore di 100. La connessione di messaggi non recapitabili non verrà riutilizzata (anche in richieste di connessione future) e verrà infine timeout dopo CPTimeout passa. Gestione Driver continuerà a trovare un'altra connessione dal pool di frequenza.  
  
 Se Gestione Driver riutilizzare una connessione con punteggio è rigorosamente minore di 100 (inclusi 99), Driver Manager chiamerà SQLSetConnectAttr(SQL_ATTR_DBC_INFO_TOKEN) per reimpostare la connessione nello stato richiesto dall'applicazione. Il driver non deve reimpostare la connessione in questa chiamata di funzione.  
  
 Se *fRequiredTransactionEnlistment* è TRUE, viene riutilizzata *hCandidateConnection* richiede un'integrazione aggiuntiva (*ID transazione* ! = NULL) o unenlistment (* ID transazione* = = NULL). Indica il costo di riutilizzare una connessione e se il driver deve integrare / rimuovere la connessione se sta per riutilizzare la connessione. Se *fRequireTransactionEnlistment* è FALSE, driver deve ignorare il valore di *ID transazione*.  
  
 Gestione Driver garantisce che l'elemento padre HENV gestire di *hRequest* e *hCandidateConnection* sono uguali. Gestione Driver garantisce che l'ID del pool è associata a *hRequest* e *hCandidateConnection* sono uguali.  
  
 Le applicazioni non devono chiamare direttamente questa funzione. Un driver ODBC che supporta il pool di connessioni compatibile con il driver deve implementare questa funzione.  
  
 Includere sqlspi.h per lo sviluppo di driver ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Il pool di connessioni compatibile con il driver](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Sviluppo di un Driver ODBC consapevolezza Pool di connessioni](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

