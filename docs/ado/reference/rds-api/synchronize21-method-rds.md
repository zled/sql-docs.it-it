---
title: Metodo Synchronize21 (RDS) | Documenti Microsoft
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Synchronize21 method [ADO]
ms.assetid: 6b35f136-9d9a-4bdd-8144-67decfd3c4e9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad5f94fb96fc7ff8095ad88aee0d8bf335206472
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="synchronize21-method-rds"></a>Metodo Synchronize21 (RDS)
Sincronizzare il recordset specificato con il database specificato dalla stringa di connessione per l'utilizzo con ADO 2.1.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Synchronize21(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray)  
```  
  
#### <a name="parameters"></a>Parametri  
 *connectionString*  
 Stringa utilizzata per la connessione al provider OLE DB in cui verrà inviata la richiesta. Se viene utilizzato un gestore, il gestore può modificare o sostituire la stringa di connessione.  
  
 *HandlerString*  
 La stringa identifica il gestore da utilizzare con questa esecuzione. La stringa contiene due parti. La prima parte contiene il nome (ProgID) del gestore da utilizzare. La seconda parte della stringa contiene gli argomenti vengono passati al gestore. Modalità di interpretazione della stringa di argomenti è gestore specifico. Le due parti sono separate per la prima istanza di una virgola nella stringa di. La stringa di argomenti può contenere virgole aggiuntive. Gli argomenti sono facoltativi.  
  
 *lSynchronizeOptions*  
 Maschera di bit delle opzioni di sincronizzazione.  
  
 1 =*UpdateTransact* aggiornamenti al database vengono eseguito il wrapping in una transazione. La transazione viene interrotta se uno degli aggiornamenti non riesce.  
  
 2 =*RefreshWithUpdate* cause riga stati deve essere restituita se nessuna delle due *aggiornamento* né *RefreshConflicts* è impostata.  
  
 4 =*aggiornamento* il recordset viene aggiornato con i dati correnti dal database. Gli aggiornamenti in sospeso non vengono inseriti nel database. Se questo bit non è impostato, il recordset non viene aggiornato e gli aggiornamenti in sospeso vengono inseriti nel database.  
  
 8 =*RefreshConflicts* tutte le righe con modifiche in sospeso non aggiornate. Impossibile aggiornare le righe vengono aggiornate con i dati correnti dal database.  
  
 *ppRecordset*  
 Un puntatore a un puntatore al recordset da sincronizzare.  
  
 *pStatusArray*  
 Una variabile variant utilizzato per restituire una matrice protetta di stati di riga per le righe interessate da sincronizzare. Non impostare se nessuna delle seguenti opzioni di sincronizzazione sono impostata: *RefreshWithUpdate*, *aggiornamento* e *RefreshConflicts*.  
  
## <a name="remarks"></a>Osservazioni  
 Il *HandlerString* parametro può essere null. Cosa accade in questo caso dipende dalla modalità con cui il server di servizi desktop remoto è configurato. La stringa di un gestore di "MSDFMAP. Handler" indica che il gestore di Microsoft fornito (Msdfmap.dll) deve essere utilizzato. La stringa di un gestore di "MASDFMAP.handler,sample.ini" indica che deve essere utilizzato il gestore Msdfmap.dll e che l'argomento "il file" deve essere passato al gestore. MSDFMAP.dll interpreterà quindi l'argomento come una direzione di utilizzare il file per controllare le stringhe di connessione e query.  
  
> [!NOTE]
>  Il **Synchronize21** metodo è semplicemente una versione di [sincronizzare metodo (RDS)](../../../ado/reference/rds-api/synchronize-method-rds.md). In cui è necessario utilizzare il **Sincronizza** metodo per comunicare con ADO 2.1, il **Synchronize21** metodo può essere chiamato invece. Le funzionalità del **Sincronizza** metodo in ADO 2.5 e versioni successiva sono un superset delle funzionalità disponibili per lo stesso metodo di ADO 2.1.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


