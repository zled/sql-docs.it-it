---
title: Provider Microsoft OLE DB per servizio di indicizzazione Microsoft | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d278b3fd6a2460471195e5744baef93292dfbc30
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Provider Microsoft OLE DB per una panoramica del servizio di indicizzazione Microsoft
Il Provider Microsoft OLE DB per servizio di indicizzazione Microsoft fornisce l'accesso di sola lettura a livello di codice per file system e i dati Web indicizzati dal servizio di indicizzazione Microsoft. Applicazioni ADO possono eseguire query SQL per recuperare informazioni sulle proprietà di contenuto e il file.

 Il provider è a thread libero e abilitato per UNICODE.

## <a name="connection-string-parameters"></a>Parametri di stringa di connessione
 Per connettersi a questo provider, impostare il **Provider =** argomento per il [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà:

```
MSIDXS
```

 Lettura di [Provider](../../../ado/reference/ado-api/provider-property-ado.md) restituirà anche questa stringa.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il Provider OLE DB per servizio di indicizzazione Microsoft. In genere questo è l'unica parola chiave specificata nella stringa di connessione.|
|**Data Source**|Specifica il nome del catalogo del servizio di indicizzazione. Se questa parola chiave non è specificata, viene utilizzato il catalogo di sistema predefinito.|
|**Locale Identifier**|Specifica un numero a 32 bit univoco (ad esempio, 1033) che specifica le preferenze relative alla lingua dell'utente. Se questa parola chiave non è specificata, viene utilizzato l'identificatore delle impostazioni locali di sistema predefinito.|

## <a name="command-text"></a>Testo comando
 La sintassi di query SQL del servizio di indicizzazione è costituita da estensioni per il SQL-92 **selezionare** istruzione e il relativo **FROM** e **dove** clausole. I risultati della query vengono restituiti tramite i set di righe OLE DB, che possono essere utilizzati da ADO e modificati come [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti.

 È possibile cercare parole o frasi o usare caratteri jolly per eseguire la ricerca di radici di parole o i modelli. La logica di ricerca può essere basata su decisioni booleane, termini ponderati o prossimità con altre parole. È inoltre possibile cercare da "testo libero", che consente di trovare corrispondenze in base alle significato piuttosto che termini esatti.

 Il sottolinguaggio del comando specifico è documentato in linguaggi di Query per la documentazione del servizio di indicizzazione.

 Il provider non accetta chiamate di stored procedure o i nomi di tabella semplice (ad esempio, il [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) proprietà sarà sempre **adCmdText**).

## <a name="recordset-behavior"></a>Comportamento di recordset
 Le tabelle seguenti elencano le funzionalità disponibili con un **Recordset** oggetto aperto con questo provider. Solo il tipo di cursore statico (**adOpenStatic**) è disponibile.

 Per informazioni dettagliate sui **Recordset** comportamento per la configurazione di provider, eseguire il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo ed enumerare il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme del **Recordset** per determinare se sono presenti proprietà dinamiche specifiche del provider.

 **Disponibilità di proprietà Recordset ADO standard:**

|Proprietà|Disponibilità|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|lettura/scrittura|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|lettura/scrittura|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Sola lettura|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Sola lettura|
|[Segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md)*|lettura/scrittura|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lettura/scrittura|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|sempre **adUseServer**|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|sempre **adOpenStatic**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|sempre **adEditNone**|
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Sola lettura|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|lettura/scrittura|
|[Tipo di blocco](../../../ado/reference/ado-api/locktype-property-ado.md)|lettura/scrittura|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|non disponibile|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lettura/scrittura|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Sola lettura|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lettura/scrittura|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Sola lettura|
|[Origine](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lettura/scrittura|
|[State](../../../ado/reference/ado-api/state-property-ado.md)|Sola lettura|
|[Stato](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Sola lettura|

 \*È necessario abilitare i segnalibri nel provider per questa funzionalità sia presente nel **Recordset**.

 **Disponibilità dei metodi di Recordset ADO standard:**

|Metodo|Disponibile?|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|no|
|[Annulla](../../../ado/reference/ado-api/cancel-method-ado.md)|Sì|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|no|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|no|
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Sì|
|[Chiudi](../../../ado/reference/ado-api/close-method-ado.md)|Sì|
|[Elimina](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|no|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Sì|
|[Sposta](../../../ado/reference/ado-api/move-method-ado.md)|Sì|
|[Metodo MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Sì|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Sì|
|[Aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Sì|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Sì|
|[Risincronizzazione](../../../ado/reference/ado-api/resync-method.md)|Sì|
|[Supporta](../../../ado/reference/ado-api/supports-method.md)|Sì|
|[Update](../../../ado/reference/ado-api/update-method.md)|no|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|no|

 Per dettagli specifici sull'implementazione e funzionale informazioni su Provider Microsoft OLE DB per servizio di indicizzazione Microsoft, consultare il [Guida per programmatori OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx), oppure visitare la pagina servizi Web di Windows NT Server Web sito.

## <a name="see-also"></a>Vedere anche
 [La proprietà CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [proprietà ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [insieme di proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [proprietà Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [ Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [supporta (metodo)](../../../ado/reference/ado-api/supports-method.md)
