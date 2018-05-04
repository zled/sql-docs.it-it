---
title: 'Issasynchstatus:: getStatus (OLE DB) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus::GetStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- GetStatus method
ms.assetid: 354b6ee4-b5a1-48f6-9403-da3bdc911067
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 107550eaf5700fe68cf276771837d20ec047b7cf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="issasynchstatusgetstatus-ole-db"></a>ISSAsynchStatus::GetStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Restituisce lo stato di un'operazione in esecuzione in modo asincrono.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT GetStatus(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation,  
        DBCOUNTITEM *pulProgress,  
        DBCOUNTITEM *pulProgressMax,  
        DBASYNCHPHASE *peAsynchPhase,  
        LPOLESTR *ppwszStatusText);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hChapter*[in]  
 Handle del capitolo. Se l'oggetto sottoposto a polling non è un oggetto set di righe o l'operazione non è applicabile a un capitolo, deve essere impostato sul valore DB_NULL_HCHAPTER, che viene ignorato dal provider.  
  
 *eOperation*[in]  
 Operazione per la quale viene richiesto lo stato asincrono. Deve corrispondere al valore seguente:  
  
 DBASYNCHOP_OPEN: il consumer richiede informazioni sull'apertura o sul popolamento asincrono di un set di righe o sull'inizializzazione asincrona di un oggetto origine dati. Se il provider è un provider conforme a OLE DB 2.5 che supporta l'associazione URL diretta, il consumer richiede informazioni sull'inizializzazione o sul popolamento asincrono di un oggetto origine dati, set di righe, riga o flusso.  
  
 *pulProgress*[out]  
 Puntatore alla memoria in cui restituire lo stato corrente dell'operazione asincrona rispetto al valore massimo previsto indicato nel *pulProgressMax* parametro. Per ulteriori informazioni sul significato di *pulProgress*, vedere la descrizione di *peAsynchPhase*.  
  
 Se *pulProgress* è un puntatore null, non viene restituito alcun progresso.  
  
 *pulProgressMax*[out]  
 Puntatore alla memoria in cui restituire il valore massimo previsto del *pulProgress* parametro. Questo valore può variare nelle diverse chiamate al metodo. Per ulteriori informazioni sul significato di *pulProgressMax*, vedere la descrizione di *peAsynchPhase*.  
  
 Se *pulProgressMax* è un puntatore null, non viene restituito alcun valore massimo previsto.  
  
 *peAsynchPhase*[out]  
 Puntatore alla memoria in cui restituire informazioni aggiuntive sullo stato dell'operazione asincrona. I valori validi includono:  
  
 DBASYNCHPHASE_INITIALIZATION: l'oggetto si trova in una fase di inizializzazione. Gli argomenti *pulProgress* e *pulProgressMax* indicano un rapporto di completamento stimato. L'oggetto non è ancora completamente materializzato. Il tentativo di chiamare qualsiasi altra interfaccia potrebbe non riuscire e il set completo di interfacce potrebbe non essere disponibile per l'oggetto. Se l'operazione asincrona è il risultato della chiamata al metodo **ICommand:: Execute** per un comando che aggiorna, Elimina o inserisce righe e se *cParamSets* è maggiore di 1, *pulProgress* e *pulProgressMax* possono indicare lo stato per un singolo set di parametri o per l'intera matrice di set di parametri.  
  
 DBASYNCHPHASE_POPULATION: l'oggetto si trova in una fase di popolamento. Anche se il set di righe viene inizializzato completamente e l'intervallo completo di interfacce è disponibile per l'oggetto, nel set di righe potrebbero essere presenti altre righe non ancora popolate. Mentre *pulProgress* e *pulProgressMax* può essere basato sul numero di righe popolate, sono generalmente basate sul tempo o il lavoro richiesto per popolare il set di righe. Un chiamante deve pertanto utilizzare queste informazioni come stima approssimativa del tempo che potrebbe essere necessario e non dell'eventuale conteggio delle righe. Questa fase viene restituita solo durante il popolamento di un set di righe. Non viene restituita mai durante l'inizializzazione di un oggetto origine dati o l'esecuzione di un comando che aggiorna, elimina o inserisce righe.  
  
 DBASYNCHPHASE_COMPLETE: tutta l'elaborazione asincrona dell'oggetto è stata completata. **Issasynchstatus:: GetStatus** restituisce un valore HRESULT che indica il risultato dell'operazione. In genere, si tratta dell'oggetto HRESULT che sarebbe stato restituito se l'operazione fosse stata chiamata in modo sincrono. Se l'operazione asincrona è il risultato della chiamata al metodo **ICommand:: Execute** per un comando che aggiorna, Elimina o inserisce righe, *pulProgress* e *pulProgressMax* sono uguale al numero totale di righe interessate dal comando. Se *cParamSets* è maggiore di 1, questo è il numero totale di righe interessate da tutti i set di parametri specificati nell'esecuzione. Se *peAsynchPhase* è un puntatore null, non viene restituito alcun codice di stato.  
  
 DBASYNCHPHASE_CANCELED: l'elaborazione asincrona dell'oggetto è stata interrotta. **Issasynchstatus:: GetStatus** restituisce DB_E_CANCELED. Se l'operazione asincrona è il risultato della chiamata al metodo **ICommand:: Execute** per un comando che aggiorna, Elimina o inserisce righe, *pulProgress* è uguale al numero totale di righe, per tutti i set di parametri, interessate dal comando prima dell'annullamento.  
  
 *ppwszStatusText*[in/out]  
 Puntatore alla memoria contenente informazioni aggiuntive sull'operazione. Un provider può utilizzare questo valore per distinguere tra elementi differenti di un'operazione, ad esempio le diverse risorse a cui si accede. Questa stringa viene localizzata in base alla proprietà DBPROP_INIT_LCID dell'oggetto origine dati.  
  
 Se *ppwszStatusText* è non null per l'input, il provider restituisce lo stato associato allo specifico elemento identificato da *ppwszStatusText*. Se *ppwszStatusText* non indica un elemento di *eOperation*, il provider restituisce S_OK con *pulProgress* e *pulProgressMax*impostato sullo stesso valore. Se il provider non distingue tra gli elementi in base a un identificatore testuale, imposta *ppwszStatusText* a NULL e restituisce informazioni sull'operazione nel suo complesso; in caso contrario, se *ppwszStatusText*è non null per l'input, il provider lascia *ppwszStatusText* invariati.  
  
 Se *ppwszStatusText* è null per l'input, il provider imposta *ppwszStatusText* su un valore che indica ulteriori informazioni sull'operazione o su NULL se tali informazioni non sono disponibile o se  **Issasynchstatus:: GetStatus** restituisce un errore. Quando *ppwszStatusText* è null per l'input, il provider alloca memoria per la stringa di stato e restituisce l'indirizzo alla memoria. Il consumer rilascia la memoria con **IMalloc:: Free** quando non è più necessario la stringa.  
  
 Se *ppwszStatusText* è NULL per input, non viene restituita alcuna stringa di stato e il provider restituisce informazioni su qualsiasi elemento dell'operazione o sull'operazione in generale.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è stato restituito correttamente.  
  
-   Se *peAsynchPhase* è uguale a DBASYNCHPHASE_INITIALIZATION, l'oggetto non ancora completamente inizializzato, il tentativo di chiamare qualsiasi altra interfaccia potrebbe non riuscire e il set completo di interfacce potrebbe non essere disponibile per l'oggetto.  
  
-   Se *peAsynchPhase* è uguale a DBASYNCHPHASE_POPULATION, il set di righe è completamente inizializzato e l'intervallo completo di interfacce è disponibile per l'oggetto; tuttavia, potrebbero essere presenti altre righe non ancora popolate nel set di righe.  
  
-   Se *peAsynchPhase* è uguale a DBASYNCHPHASE_COMPLETE, tutta l'elaborazione asincrona dell'oggetto è stata completata. L'oggetto è stato inizializzato e popolato completamente.  
  
 DB_E_CANCELED  
 L'elaborazione asincrona è stata annullata durante il popolamento del set di righe. Il popolamento viene arrestato, ma il set di righe rimane valido per le righe già popolate.  
  
 L'elaborazione asincrona è stata annullata durante l'inizializzazione dell'oggetto origine dati. L'oggetto origine dati si trova in uno stato non inizializzato.  
  
 E_INVALIDARG  
 Il *hChapter* parametro non è corretto.  
  
 E_UNEXPECTED  
 **Issasynchstatus:: GetStatus** è stato chiamato su un oggetto di origine dati, e **IDBInitialize:: Initialize** non è stato chiamato sull'oggetto origine dati.  
  
 **Issasynchstatus:: GetStatus** è stato chiamato su un set di righe **ITransaction:: commit** o **ITransaction:: Abort** è stato chiamato e l'oggetto è in uno stato non valido.  
  
 **Issasynchstatus:: GetStatus** è stato chiamato su un set di righe annullato in modo asincrono nella fase di inizializzazione. Il set di righe si trova in uno stato non valido.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider.  
  
## <a name="remarks"></a>Osservazioni  
 Il **issasynchstatus:: GetStatus** metodo funziona esattamente come il **idbasynchstatus:: GetStatus** metodo tranne il fatto che se l'oggetto di origine di inizializzazione di un tipo di dati viene interrotta, viene restituito E_UNEXPECTED anziché rispetto a DB_E_CANCELED (benché [issasynchstatus::](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) restituirà DB_E_CANCELED). Questo accade perché l'oggetto origine dati non rimane nello stato non valido in seguito a un'interruzione, allo scopo di consentire altri tentativi di inizializzazione.  
  
 Se il set di righe viene inizializzato o popolato in modo asincrono, deve supportare questo metodo.  
  
 Oltre ai valori restituiti elencati, **issasynchstatus:: GetStatus** può restituire qualsiasi HRESULT che sarebbe stato restituito dal metodo che ha avviato l'operazione asincrona, che indica l'esito positivo o negativo dell'operazione.  
  
 Alcune operazioni asincrone potrebbero non essere in grado di restituire stati diversi da "terminato" e "non terminato". È necessario impostare *pulProgressMax* su un valore pari a 1, che indica la granularità radicale della stima, pertanto le relative risposte sono 0/1 o 1/1.  
  
 Un provider può modificare *pulProgressMax* nelle chiamate successive e persino restituire un rapporto inferiore a quello precedente, se riflette una stima migliore del livello di completamento dell'attività.  
  
 Il provider non è obbligato a garantire una maggiore accuratezza, anche se questa è auspicabile quando sono possibili stime accettabili del completamento. L'impegno per ottenere questo risultato migliorerà la qualità dell'interfaccia utente perché è probabile che questa funzione venga utilizzata principalmente per fornire all'utente dettagli sullo stato. La soddisfazione dell'utente aumenta proporzionalmente alla qualità dei dettagli relativi a un'attività impercettibile e con esecuzione prolungata.  
  
 La chiamata **issasynchstatus:: GetStatus** su un oggetto origine dati inizializzato o un set di righe popolato o si passa un valore per *eOperation* diverso da DBASYNCHOP_OPEN, viene restituito S_OK con  *pulProgress* e *pulProgressMax* impostata sullo stesso valore. Se **issasynchstatus:: GetStatus** viene chiamato su un oggetto creato dall'esecuzione di un comando che aggiorna, Elimina o inserisce righe, entrambi *pulProgress* e *pulProgressMax* indica il numero totale di righe interessate dal comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../../relational-databases/native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
