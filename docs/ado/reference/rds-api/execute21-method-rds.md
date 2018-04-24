---
title: Metodo Execute21 (RDS) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute21 method [RDS]
ms.assetid: 9f131c8d-1497-416d-8209-abb481c38f7b
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f0eb7764c01ee7ae8cfd5cb27371dd9d5fa390b2
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="execute21-method-rds"></a>Metodo Execute21 (RDS)
Esegue la richiesta e crea un recordset ADO per l'utilizzo in ADO 2.1.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.Execute21(ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters)  
```  
  
#### <a name="parameters"></a>Parametri  
 *connectionString*  
 Stringa utilizzata per la connessione al provider OLE DB in cui verrà inviata la richiesta per l'esecuzione. Se viene specificato un gestore con *HandlerString*, è possibile modificare o sostituire la stringa di connessione.  
  
 *HandlerString*  
 La stringa identifica il gestore da utilizzare con questa esecuzione. La stringa contiene due parti. La prima parte contiene il nome (ProgID) del gestore da utilizzare. La seconda parte della stringa contiene gli argomenti vengono passati al gestore. Modalità di interpretazione della stringa di argomenti è gestore specifico. Le due parti sono separate dalla prima istanza di una virgola nella stringa (anche se la stringa di argomenti può contenere virgole aggiuntive). Gli argomenti sono facoltativi.  
  
 *QueryString*  
 Un comando nel linguaggio di comando supportato dal provider OLE DB identificato nella stringa di connessione. Per i provider basato su SQL, è possibile che contenga un [!INCLUDE[tsql](../../../includes/tsql_md.md)] istruzione di comando, ma per i provider non SQL (ad esempio, MSDataShape) non è possibile un [!INCLUDE[tsql](../../../includes/tsql_md.md)] istruzione di query.  
  
 Inoltre, se viene utilizzato un gestore e si consiglia di utilizzare un gestore, il gestore può modificare o sostituire il valore specificato qui. Ad esempio, in genere sostituisce il gestore *QueryString* con una stringa di query dal file ini. Per impostazione predefinita, viene utilizzato il file MSDFMAP.  
  
 *lMarshalOptions*  
 Utilizzato per impostare le opzioni di marshalling nel set di righe recordset restituito.  
  
 *TableID*  
 Una variante del tipo VT_EMPTY o VT_BSTR. Se questo valore è di tipo VT_EMPTY, viene ignorato. Se è di tipo VT_BSTR, il set di record viene creato utilizzando **adCmdTableDirect** utilizzando il valore specificato qui e *QueryString* parametro viene ignorato.  
  
 *lExecuteOptions*  
 Maschera di bit delle opzioni di esecuzione:  
  
 1 =*ReadOnly* verrà aperto il recordset utilizzando **adLockReadOnly**.  
  
 2 =*NoBatch* verrà aperto il recordset utilizzando **adLockOptimistic**.  
  
 4 =*AllParamInfoSupplied* chiamante garantisce che le informazioni sui parametri per tutti i parametri viene fornite *pParameters*.  
  
 8 =*GetInfo* informazioni sui parametri per la query verrà ottenuti dal provider OLE DB e restituite nel *pParameters* parametro. Non viene eseguita la query e non viene restituito alcun oggetto recordset.  
  
 16 = GetHiddenColumns verrà aperto il recordset utilizzando **adLockBatchOptimistic** e le colonne nascoste verranno inclusa nel recordset.  
  
 Sebbene *ReadOnly*, *NoBatch* e *GetHiddenColumns* si escludono a vicenda, non è possibile impostare più di uno di essi. Se sono impostate più opzioni, *GetHiddenColumns* ha la precedenza su tutte le altre opzioni, seguiti da *ReadOnly*. Se viene specificata alcuna opzione, per impostazione predefinita, il recordset è aperto tramite **adLockBatchOptimistic** ma le colonne nascoste non vengono inclusi nel recordset.  
  
 *pParameters*  
 Una variabile variant contenente una matrice protetta di definizioni di parametro. Se il *GetInfo* in è stata specificata l'opzione *lExecuteOptions*, questo parametro viene utilizzato per restituire le definizioni dei parametri ottenuti dal provider OLE DB. In caso contrario, questo parametro può essere vuoto.  
  
## <a name="remarks"></a>Osservazioni  
 Il *HandlerString* parametro può essere null. Cosa accade in questo caso dipende dalla modalità con cui il server di servizi desktop remoto è configurato. La stringa di un gestore di "MSDFMAP. Handler" indica che il gestore di Microsoft fornito (Msdfmap.dll) deve essere utilizzato. La stringa di un gestore di "MASDFMAP.handler,sample.ini" indica che deve essere utilizzato il gestore Msdfmap.dll e che l'argomento "il file" deve essere passato al gestore. MSDFMAP.dll interpreterà l'argomento come una direzione di utilizzare il file per controllare le stringhe di connessione e query.  
  
> [!NOTE]
>  Il **Execute21** metodo è una versione di [Execute (metodo) (RDS)](../../../ado/reference/rds-api/execute-method-rds.md). In cui è necessario utilizzare il **Execute** metodo per comunicare con ADO 2.1, il **Execute21** metodo può essere chiamato invece. Le funzionalità del **Execute** metodo in ADO 2.5 e versioni successiva sono un superset delle funzionalità disponibili per lo stesso metodo di ADO 2.1.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


