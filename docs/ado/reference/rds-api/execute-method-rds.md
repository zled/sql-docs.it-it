---
title: Eseguire il metodo (RDS) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c050ef685d6e3ef566d78307db2c10c2c01c23e7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="execute-method-rds"></a>Eseguire il metodo (RDS)
Esegue la richiesta e crea un recordset ADO per l'utilizzo in ADO 2.5 e versioni successive.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>Parametri  
 *connectionString*  
 Stringa utilizzata per la connessione al provider OLE DB in cui verrà inviata la richiesta per l'esecuzione. Se viene specificato un gestore con *HandlerString* può modificare o sostituire la stringa di connessione.  
  
 *HandlerString*  
 Una stringa di due parti che identifica il gestore da utilizzare con questa esecuzione. La stringa contiene due parti. La prima parte contiene il nome (ProgID) del gestore da utilizzare. La seconda parte contiene gli argomenti vengono passati al gestore. I dettagli della modalità di interpretazione della stringa di argomenti sono specifici per ogni gestore. Le due parti sono separate per la prima istanza di una virgola nella stringa di. La stringa di argomenti può contenere virgole aggiuntive. Gli argomenti sono facoltativi.  
  
 *QueryString*  
 Un comando nel linguaggio di comando supportato dal provider OLE DB identificato nella stringa di connessione. Per i provider basato su SQL, *QueryString* potrebbe contenere un'istruzione di comando Transact-SQL, ma per i provider non SQL (ad esempio, MSDataShape) non è possibile un [!INCLUDE[tsql](../../../includes/tsql_md.md)] istruzione di query.  
  
 Se viene utilizzato un gestore, il gestore può modificare o sostituire il valore specificato qui. Ad esempio, in genere sostituisce il gestore *QueryString* con una stringa di query dal file ini. Per impostazione predefinita, viene utilizzato il file MSDFMAP.  
  
 *lFetchOptions*  
 Indica il tipo di recupero asincrono.  
  
 Per ulteriori informazioni, vedere [proprietà FetchOptions (RDS)](../../../ado/reference/rds-api/fetchoptions-property-rds.md).  
  
 *TableID*  
 Oggetto **Variant** di tipo VT_EMPTY o VT_BSTR. Se questo valore è di tipo VT_EMPTY, viene ignorato. Se è di tipo VT_BSTR, il set di record viene creato utilizzando **adCmdTableDirect** e il valore specificato qui e *QueryString* parametro viene ignorato.  
  
 *lExecuteOptions*  
 Una maschera di bit delle opzioni di esecuzione:  
  
 1 =*ReadOnly* verrà aperto il recordset utilizzando **adLockReadOnly**.  
  
 2 =*NoBatch* verrà aperto il recordset utilizzando **adLockOptimistic**.  
  
 4 =*AllParamInfoSupplied* chiamante garantisce che le informazioni sui parametri per tutti i parametri viene fornite *pParameters*.  
  
 8 =*GetInfo* informazioni sui parametri per la query verrà ottenuti dal provider OLE DB e restituite nel *pParameters* parametro. Non viene eseguita la query e non viene restituito alcun oggetto recordset.  
  
 16 =*GetHiddenColumns* verrà aperto il recordset utilizzando **adLockBatchOptimistic** e le colonne nascoste verranno inclusa nel recordset.  
  
 *ReadOnly*, *NoBatch* e *GetHiddenColumns* si escludono a vicenda; tuttavia, non genera un errore per impostare più di uno di essi. Se sono impostate più opzioni, *GetHiddenColumns* ha la precedenza su tutte le altre, seguito da *ReadOnly*. Se viene specificata alcuna opzione, per impostazione predefinita, il recordset è aperto tramite **adLockBatchOptimistic** e colonne nascoste non sono incluse nel recordset.  
  
 *pParameters*  
 Oggetto **Variant** che contiene una matrice protetta di definizioni di parametro. Se il *GetInfo* in è stata specificata l'opzione *lExecuteOptions*, questo parametro viene utilizzato per restituire le definizioni dei parametri ottenuti dal provider OLE DB. In caso contrario, questo parametro può essere vuoto.  
  
 *lcid*  
 L'identificatore LCID utilizzato per compilare gli eventuali errori che vengono restituiti in *pInformation*.  
  
 *pInformation*  
 Puntatore all'errore di informazioni restituite dall'esecuzione. Se NULL, viene restituita alcuna informazione di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il *HandlerString* parametro può essere null. Cosa accade in questo caso dipende dalla modalità con cui il server di servizi desktop remoto è configurato. La stringa di un gestore di "MSDFMAP. Handler" indica che il gestore di Microsoft fornito (Msdfmap.dll) deve essere utilizzato. La stringa di un gestore di "MASDFMAP.handler,sample.ini" indica che deve essere utilizzato il gestore Msdfmap.dll e che l'argomento "il file" deve essere passato al gestore. MSDFMAP.dll interpreterà l'argomento come una direzione di utilizzare il file per controllare le stringhe di connessione e query.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


