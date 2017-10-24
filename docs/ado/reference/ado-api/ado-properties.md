---
title: "Proprietà ADO | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [ADO]
- ADO properties
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 686684010ff1e72f61b971c2504d5634ee28f269
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ado-properties"></a>Proprietà ADO
|||  
|-|-|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Indica la pagina in cui risiede il record corrente.|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Indica la posizione ordinale del record corrente di un **Recordset** oggetto.|  
|[ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md)|Indica il **comando** oggetto che ha creato l'oggetto associato **Recordset** oggetto.|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Indica a cui **connessione** dell'oggetto specificato **comando**, **Recordset**, o **Record** oggetto attualmente appartiene.|  
|[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)|Indica la lunghezza effettiva del valore di un campo.|  
|[Attributi](../../../ado/reference/ado-api/attributes-property-ado.md)|Indica una o più caratteristiche di un oggetto.|  
|[BOF ed EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|**BOF** indica che la posizione del record corrente è precedente al primo record in un oggetto Recordset.<br /><br /> **EOF** indica che la posizione del record corrente è successiva all'ultimo record in un oggetto Recordset.|  
|[Segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md)|Indica un segnalibro che identifica in modo univoco il record corrente in un **Recordset** dell'oggetto o imposta il record corrente in un **Recordset** oggetto sul record identificato da un segnalibro valido.|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Indica il numero di record da un **Recordset** oggetti memorizzati nella cache in locale.|  
|[Capitolo](../../../ado/reference/ado-api/chapter-property-ado.md)|Ottiene o imposta OLE DB **capitolo** oggetto da/su un **ADORecordsetConstruction** oggetto.|  
|[Set di caratteri](../../../ado/reference/ado-api/charset-property-ado.md)|Indica il set di caratteri in cui il contenuto di un testo **flusso** devono essere convertite.|  
|[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)|Indica il flusso utilizzato come input per un **comando** oggetto.|  
|[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)|Indica il testo di un comando per essere eseguito in base a un provider.|  
|[CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)|Indica il tempo di attesa durante l'esecuzione di un comando prima di terminare il tentativo e generare un errore.|  
|[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)|Indica il tipo di un **comando** oggetto.|  
|[Proprietà ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)|Indica le informazioni utilizzate per stabilire una connessione a un'origine dati.|  
|[ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)|Indica il tempo di attesa durante il tentativo di stabilire una connessione prima di terminare il tentativo e generare un errore.|  
|[Conteggio](../../../ado/reference/ado-api/count-property-ado.md)|Indica il numero di oggetti in una raccolta.|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|Indica la posizione del servizio di cursore.|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Indica il tipo di cursore utilizzato in un **Recordset** oggetto.|  
|[DataMember](../../../ado/reference/ado-api/datamember-property.md)|Indica il nome del membro dati che verrà recuperato dall'oggetto a cui fa riferimento il **DataSource** proprietà.|  
|[Origine dati](../../../ado/reference/ado-api/datasource-property-ado.md)|Indica un oggetto che contiene i dati per essere rappresentato come un **Recordset** oggetto.|  
|[DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)|Indica il database predefinito per un **connessione** oggetto.|  
|[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)|Indica la capacità di dati di un **campo** oggetto.|  
|[Descrizione](../../../ado/reference/ado-api/description-property.md)|Viene descritto un **errore** oggetto.|  
|[Sottolinguaggio](../../../ado/reference/ado-api/dialect-property.md)|Indica la sintassi e regole generali utilizzate per analizzare il provider di **CommandText** o **CommandStream** proprietà.|  
|[Direzione](../../../ado/reference/ado-api/direction-property.md)|Indica se il **parametro** rappresenta un parametro di input, un parametro di output o entrambi, o se il parametro è il valore restituito da una stored procedure.|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|Indica lo stato di modifica del record corrente.|  
|[FINE DEL FLUSSO](../../../ado/reference/ado-api/eos-property.md)|Indica se la posizione corrente è alla fine del flusso.|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Indica un filtro per i dati in un **Recordset**.|  
|[HelpContext e HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)|Indica il file e l'argomento associato a un **errore** oggetto.<br /><br /> **ID argomento Guida** restituisce un ID di contesto, come un **lungo** valore, per un argomento in un file della Guida.<br /><br /> **HelpFile** restituisce un **stringa** valore che restituisce un percorso completamente risolto di un file della Guida.|  
|[Indice](../../../ado/reference/ado-api/index-property.md)|Indica il nome dell'indice attualmente attivo per un **Recordset** oggetto.|  
|[IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)|Indica il livello di isolamento per una **connessione** oggetto.|  
|[Elemento](../../../ado/reference/ado-api/item-property-ado.md)|Indica un membro specifico di una raccolta, per nome o numero ordinale.|  
|[Separatore](../../../ado/reference/ado-api/lineseparator-property-ado.md)|Indica il carattere binario da utilizzare come separatore di riga nel testo **flusso** oggetti.|  
|[Tipo di blocco](../../../ado/reference/ado-api/locktype-property-ado.md)|Indica il tipo di blocco applicato ai record durante la modifica.|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|Indica i record che deve essere sottoposto a marshalling al server.|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Indica il numero massimo di record da restituire per una **Recordset** da una query.|  
|[Mode](../../../ado/reference/ado-api/mode-property-ado.md)|Indica le autorizzazioni disponibili per la modifica dei dati in un **connessione**, **Record**, o **flusso** oggetto.|  
|[Nome](../../../ado/reference/ado-api/name-property-ado.md)|Indica il nome di un oggetto.|  
|[NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md)|Indica il codice di errore specifico del provider per un particolare **errore** oggetto.|  
|[Numero](../../../ado/reference/ado-api/number-property-ado.md)|Indica il numero che identifica in modo univoco un **errore** oggetto.|  
|[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)|Indica la scala di valori numerici in un **parametro** o **campo** oggetto.|  
|[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)|Indica il valore di un **campo** che era presente nel record prima che eventuali modifiche apportate.|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Indica il numero di pagine di dati di **Recordset** oggetto contiene.|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Indica il numero di record rappresenta una pagina di **Recordset**.|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Imposta il contenitore di OLE DB **riga** oggetto un **ADORecordConstruction** oggetto, in modo che l'elemento padre della riga viene trasformato in un oggetto ADO **Record** oggetto.|  
|[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)|Indica una stringa URL assoluto che punta all'elemento padre **Record** corrente **Record** oggetto.|  
|[Posizione](../../../ado/reference/ado-api/position-property-ado.md)|Indica la posizione corrente all'interno di un **flusso** oggetto.|  
|[Precisione](../../../ado/reference/ado-api/precision-property-ado.md)|Indica il grado di precisione per i valori numerici in un **parametro** oggetto o per valori numerici **campo** oggetti.|  
|[Preparato](../../../ado/reference/ado-api/prepared-property-ado.md)|Indica se salvare una versione compilata di un comando prima dell'esecuzione.|  
|[Provider](../../../ado/reference/ado-api/provider-property-ado.md)|Indica il nome del provider per un **connessione** oggetto.|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Indica il numero di record in un **Recordset** oggetto.|  
|[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)|Indica il tipo di **Record** oggetto.|  
|[Riga](../../../ado/reference/ado-api/row-property-ado.md)|Ottiene o imposta OLE DB **riga** oggetto da/su un **ADORecordConstruction** oggetto.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Ottiene o imposta OLE DB **RowPosition** oggetto da/su un **ADORecordsetConstruction** oggetto.|  
|[Set di righe](../../../ado/reference/ado-api/rowset-property-ado.md)|Ottiene o imposta OLE DB **set di righe** oggetto da/su un **ADORecordsetConstruction** oggetto.|  
|[Origine (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)|Indica il nome dell'oggetto o dell'applicazione che ha generato un errore.|  
|[Origine (Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)|Indica l'entità rappresentata dal **Record** oggetto.|  
|[Origine (Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Indica l'origine dei dati in un **Recordset** oggetto|  
|[SQLState](../../../ado/reference/ado-api/sqlstate-property.md)|Indica lo stato SQL per uno specifico **errore** oggetto.|  
|[State](../../../ado/reference/ado-api/state-property-ado.md)|Indica per tutti gli oggetti applicabili se lo stato dell'oggetto è aperto o chiuso. Indica per l'esecuzione di un metodo asincrono, se lo stato corrente dell'oggetto è la connessione, l'esecuzione o il recupero di tutti gli oggetti applicabili|  
|[Stato (campo ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)|Indica lo stato di un **campo** oggetto.|  
|[Stato (Recordset ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Indica lo stato del record corrente riguardanti gli aggiornamenti batch o altre operazioni bulk.|  
|[StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)|Indica, in una gerarchia **Recordset** oggetto, se il riferimento a record figlio sottostanti (vale a dire il *capitolo*) le modifiche quando la riga padre posiziona le modifiche.|  
|[Proprietà del flusso](../../../ado/reference/ado-api/stream-property.md)|Ottiene o imposta OLE DB **flusso** oggetto da/su un **ADOStreamConstruction** oggetto.|  
|[Tipo](../../../ado/reference/ado-api/type-property-ado.md)|Indica il tipo di dati o di tipo operativo di un **parametro**, **campo**, o **proprietà** oggetto.|  
|[Tipo (flusso ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)|Indica il tipo di dati contenuti nel **flusso** (binario o testo).|  
|[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)|Indica il valore corrente del database per un **campo** oggetto.|  
|[Valore](../../../ado/reference/ado-api/value-property-ado.md)|Indica il valore assegnato a un **campo**, **parametro**, o **proprietà** oggetto.|  
|[Version](../../../ado/reference/ado-api/version-property-ado.md)|Indica il numero di versione di ADO.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte di ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Costanti enumerate ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Appendice b: errori ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Metodi ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Le interfacce e gli oggetti ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)

