---
title: Synchronize (metodo) (RDS) | Documenti Microsoft
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Synchronize method [ADO]
ms.assetid: 7af42866-7db2-4174-8251-388a2cf741f2
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c933cbb0a39486ea1ed04b645057bdc31011b05b
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="synchronize-method-rds"></a>Synchronize (metodo) (RDS)
Sincronizzare il Recordset specificato con il database specificato dalla stringa di connessione per l'utilizzo in ADO 2.5 e versioni successiva.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Synchronize(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray, [lcid As Long], [pInformation)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ConnectionString*  
 Stringa utilizzata per la connessione al provider OLE DB in cui verrà inviata la richiesta. Se viene utilizzato un gestore, il gestore può modificare o sostituire la stringa di connessione.  
  
 *HandlerString*  
 La stringa identifica il gestore da utilizzare con questa esecuzione. La stringa contiene due parti. La prima parte contiene il nome (ProgID) del gestore da utilizzare. La seconda parte della stringa contiene gli argomenti vengono passati al gestore. Modalità di interpretazione della stringa di argomenti è gestore specifico. Le due parti sono separate dalla prima istanza di una virgola nella stringa (anche se la stringa di argomenti può contenere virgole aggiuntive). Gli argomenti sono facoltativi.  
  
 *lSynchronizeOptions*  
 Maschera di bit delle opzioni di sincronizzazione.  
  
 1 =*UpdateTransact* aggiornamenti al database vengono eseguito il wrapping in una transazione. La transazione viene interrotta se uno degli aggiornamenti non riesce.  
  
 2 =*RefreshWithUpdate* cause riga stati deve essere restituita se nessuna delle due *aggiornamento* né *RefreshConflicts* è impostata.  
  
 4 =*aggiornamento* il recordset viene aggiornato con i dati correnti dal database. Gli aggiornamenti in sospeso non vengono inseriti nel database. Se questo bit non è impostato, il recordset non viene aggiornato ed eventuali aggiornamenti in sospeso vengono inseriti nel database.  
  
 8 =*RefreshConflicts* tutte le righe con modifiche in sospeso non aggiornate. Impossibile aggiornare le righe vengono aggiornate con i dati correnti dal database.  
  
 *ppRecordset*  
 Puntatore al recordset da sincronizzare.  
  
 *pStatusArray*  
 Una variabile variant utilizzato per restituire una matrice protetta di stati di riga per le righe interessate da sincronizzare. Non impostare se nessuna delle seguenti opzioni di sincronizzazione sono impostata: *RefreshWithUpdate*, *aggiornamento* e *RefreshConflicts*.  
  
 *lcid*  
 L'identificatore LCID utilizzato per compilare gli eventuali errori che vengono restituiti in *pInformation*.  
  
 *pInformation*  
 Un puntatore all'errore di informazioni restituite da **Execute**. Se NULL, viene restituita alcuna informazione di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il *HandlerString* parametro può essere null. Cosa accade in questo caso dipende dalla modalità con cui il server di servizi desktop remoto è configurato. La stringa di un gestore di "MSDFMAP. Handler" indica che il gestore di Microsoft fornito (Msdfmap.dll) deve essere utilizzato. La stringa di un gestore di "MASDFMAP.handler,sample.ini" indica che deve essere utilizzato il gestore Msdfmap.dll e che l'argomento "il file" deve essere passato al gestore. MSDFMAP.dll interpreterà quindi l'argomento come una direzione di utilizzare il file per controllare le stringhe di connessione e query.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


