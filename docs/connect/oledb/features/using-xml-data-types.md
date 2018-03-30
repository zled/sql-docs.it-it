---
title: Utilizzo di tipi di dati XML | Documenti Microsoft
description: Usando tipi di dati XML con il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- IRowsetUpdate interface
- data access [OLE DB Driver for SQL Server], xml data type
- OLE DB Driver for SQL Server schema rowsets
- PROVIDER_TYPES rowset
- IColumnsInfo interface
- IRowsetFind interface
- IColumnsRowset interface
- PROCEDURE_PARAMETERS rowset
- MSOLEDBSQL, XML
- xml data type [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, XML
- IRowset interface
- ISequentialStream interface
- ISSCommandWithParameters interface
- SS_XMLSCHEMA rowset
- OLE DB Driver for SQL Server OLE DB interfaces
- XML [SQL Server], OLE DB Driver for SQL Server
- COLUMNS rowset
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 97a28369b44dd42bd9e587db094c29d1911de1ec
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="using-xml-data-types"></a>Utilizzo di tipi di dati XML
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]introdotto un **xml** tipo di dati che consente di archiviare documenti XML e frammenti un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database. Il **xml** tipo di dati è un tipo di dati incorporati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ed è simile ad altri tipi predefiniti, quali **int** e **varchar**. Come con altri tipi predefiniti, è possibile usare il **xml** del tipo di dati come un tipo di colonna durante la creazione di una tabella, come un tipo di variabile, un tipo di parametro o un tipo restituito dalla funzione; oppure nelle funzioni CAST e CONVERT.  
  
## <a name="programming-considerations"></a>Considerazioni sulla programmazione  
 XML può essere autodescrittivo in quanto può eventualmente includere un'intestazione XML che specifica la codifica del documento, ad esempio:  
  
 `<?xml version="1.0" encoding="windows-1252"?><doc/>`  
  
 Lo standard XML descrive il modo in cui un processore XML può rilevare la codifica utilizzata per un documento esaminando i primi byte del documento. È possibile che la codifica specificata nell'applicazione crei conflitti con quella specificata nel documento. Poiché per i documenti passati come parametri associati i dati XML vengono considerati dati binari in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], non viene eseguita alcuna conversione e il parser XML può utilizzare senza problemi la codifica specificata nel documento. Per i dati XML associati come WSTR, tuttavia, l'applicazione deve quindi garantire che il documento venga codificato come Unicode. Questo scenario potrebbe comportare il caricamento del documento in un documento DOM, la modifica la codifica su Unicode e serializzando il documento. Se questo passaggio non viene eseguito, le conversioni di dati possono verificarsi, risultante in formato XML non valido o danneggiato.  
  
 Vi è inoltre il rischio di conflitti quando XML viene specificato in valori letterali. I dati seguenti, ad esempio, non sono validi:  
  
 `INSERT INTO xmltable(xmlcol) VALUES('<?xml version="1.0" encoding="UTF-16"?><doc/>')`  
  
 `INSERT INTO xmltable(xmlcol) VALUES(N'<?xml version="1.0" encoding="UTF-8"?><doc/>')`  
  
## <a name="ole-db-driver-for-sql-server"></a>Driver OLE DB per SQL Server 
 DBTYPE_XML è un nuovo tipo di dati specifico in formato XML nel Driver OLE DB per SQL Server. È inoltre possibile accedere ai dati XML tramite i tipi OLE DB esistenti DBTYPE_BYTES, DBTYPE_WSTR, DBTYPE_BSTR, DBTYPE_XML, DBTYPE_STR, DBTYPE_VARIANT e DBTYPE_IUNKNOWN. Dati archiviati nelle colonne di tipo XML possono essere recuperati da una colonna in un Driver OLE DB per SQL Server set di righe nei formati seguenti:  
  
-   Stringa di testo  
  
-   Un **ISequentialStream**  
  
> [!NOTE]  
>  Il Driver OLE DB per SQL Server non include un lettore SAX, ma la **ISequentialStream** può essere passata in modo semplice per gli oggetti SAX e DOM in MSXML.  
  
 **ISequentialStream** deve essere utilizzato per il recupero di documenti XML di grandi dimensioni. A XML si applicano le stesse tecniche utilizzate per altri tipi di valore di grandi dimensioni. Per ulteriori informazioni, vedere [utilizzando tipi di valore elevato](../../oledb/features/using-large-value-types.md).  
  
 Dati archiviati nelle colonne di tipo XML in un set di righe possono anche essere recuperati, inseriti o aggiornati da un'applicazione tramite le normali interfacce, ad esempio **IRow:: GetColumns**, **irowchange:: SetColumns**, e **ICommand:: Execute**. Analogamente al caso del recupero, un'applicazione può passare una stringa di testo o un **ISequentialStream** per il Driver OLE DB per SQL Server.  
  
> [!NOTE]  
>  Per inviare i dati XML in formato stringa tramite il **ISequentialStream** interfaccia, è necessario ottenere **ISequentialStream** specificando DBTYPE_IUNKNOWN e impostare il relativo *pObject* argomento null nell'associazione.  
  
 Quando i dati XML recuperati risultano troncati a causa di un buffer del consumer di dimensioni troppo ridotte, è possibile che la lunghezza venga restituita come 0xffffffff, a indicare che non è nota. Questo comportamento è coerenza con l'implementazione come tipo di dati trasmesso al client senza inviare informazioni sulla lunghezza dei dati effettivi. In alcuni casi, la lunghezza effettiva può essere restituita quando il provider ha memorizzato nel buffer l'intero valore, ad esempio **IRowset:: GetData** e in cui viene eseguita la conversione dei dati.  
  
 I dati XML inviati a SQL Server vengono considerati dati binari dal server. Questo comportamento impedisce tutte le conversioni che si verificano e consente il parser XML può rilevare automaticamente la codifica XML. Di conseguenza, una più ampia gamma di documenti XML, ad esempio quelli codificati in UTF-8, viene accettata come input in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Se i dati XML di input vengono associati come DBTYPE_WSTR, l'applicazione deve verificare che i dati siano già codificati come Unicode per evitare qualsiasi rischio di danni dovuti a conversioni di dati indesiderate.  
  
### <a name="data-bindings-and-coercions"></a>Associazione dati e coercizioni  
 Nella tabella seguente vengono descritte l'associazione e la coercizione che si verifica quando i dati di utilizzo dei tipi con il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **xml** tipo di dati.  
  
|Tipo di dati|Al server<br /><br /> **XML**|Al server<br /><br /> **Non XML**|Dal server<br /><br /> **XML**|Dal server<br /><br /> **Non XML**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_XML|Pass-through<sup>6,7</sup>|Errore<sup>1</sup>|OK<sup>11,6</sup>|Errore<sup>8</sup>|  
|DBTYPE_BYTES|Pass-through<sup>6,7</sup>|N/A<sup>2</sup>|OK <sup>11,6</sup>|N/A <sup>2</sup>|  
|DBTYPE_WSTR|Pass-through<sup>6,10</sup>|N/A <sup>2</sup>|OK<sup>4, 6, 12</sup>|N/A <sup>2</sup>|  
|DBTYPE_BSTR|Pass-through<sup>6,10</sup>|N/A <sup>2</sup>|OK <sup>3</sup>|N/A <sup>2</sup>|  
|DBTYPE_STR|OK<sup>6, 9, 10</sup>|N/A <sup>2</sup>|OK<sup>5, 6, 12</sup>|N/A <sup>2</sup>|  
|DBTYPE_IUNKNOWN|Flusso di byte tramite **ISequentialStream**<sup>7</sup>|N/A <sup>2</sup>|Flusso di byte tramite **ISequentialStream**<sup>11</sup>|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Pass-through<sup>6,7</sup>|N/A <sup>2</sup>|N/D|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Pass-through<sup>6,10</sup>|N/A <sup>2</sup>|OK<sup>3</sup>|N/A <sup>2</sup>|  
  
 <sup>1</sup>se un server di tipo diverso da DBTYPE_XML è specificato con **ICommandWithParameters:: SetParameterInfo** e il tipo di funzione di accesso è DBTYPE_XML, si verifica un errore quando viene eseguita l'istruzione (DB_E_ERRORSOCCURRED, lo stato del parametro è DBSTATUS_E_BADACCESSOR); in caso contrario, i dati vengono inviati al server, ma il server restituisce un errore indicando che non vi è alcuna conversione implicita da XML al tipo di dati del parametro.  
  
 <sup>2</sup>esula dall'ambito di questo articolo.  
  
 <sup>3</sup>formato è UTF-16, nessun contrassegno di ordine byte (BOM), nessuna specifica di codifica, Nessuna terminazione null.  
  
 <sup>4</sup>formato non è UTF-16, Nessun indicatore ordine byte, nessuna specifica di codifica, terminazione null.  
  
 <sup>5</sup>formato è caratteri multibyte codificati nella tabella codici del client con terminatore null. Conversione da server Unicode fornito può provocare danni ai dati, questa associazione è sconsigliata.  
  
 <sup>6</sup>può essere utilizzato BY_REF.  
  
 <sup>7</sup>dati UTF-16 devono iniziare con una distinta base. In caso contrario, la codifica potrebbe non essere riconosciuta correttamente dal server.  
  
 <sup>8</sup>convalida può verificarsi nella creazione della funzione di accesso o in fase di recupero. L'errore è DB_E_ERRORSOCCURRED, lo stato dell'associazione è impostato su DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>9</sup>dati vengono convertiti in Unicode utilizzando la tabella codici del client prima di essere inviati al server. Se la codifica del documento non corrisponde la tabella codici del client, può verificarsi un danneggiamento dei dati, in modo da questa associazione è fortemente sconsigliata.  
  
 <sup>10</sup>un BOM viene sempre aggiunto ai dati inviati al server. Se i dati iniziano già con un indicatore ordine byte, saranno presenti due indicatori all'inizio del buffer. Il server utilizza il primo indicatore dell'ordine dei byte per riconoscere la codifica come UTF-16, quindi lo ignora. Il secondo indicatore dell'ordine dei byte viene interpretato come spazio unificatore di larghezza zero.  
  
 <sup>11</sup>formato è UTF-16, nessuna specifica di codifica, un BOM viene aggiunto ai dati ricevuti dal server. Se dal server viene restituita una stringa vuota, all'applicazione viene comunque restituito un indicatore dell'ordine dei byte. Se la lunghezza di buffer è un numero dispari di byte, i dati vengono troncati correttamente. Se il valore intero viene restituito in blocchi, questi possono essere concatenati per ricostituire il valore corretto.  
  
 <sup>12</sup>se la lunghezza del buffer è meno di due caratteri, ovvero è insufficiente per la terminazione null, viene restituito un errore di overflow.  
  
> [!NOTE]  
>  Per i valori XML NULL non viene restituito alcun dato.  
  
 Lo standard XML richiede che i dati XML con codifica UTF-16 inizino con un indicatore dell'ordine dei byte, codice di carattere UTF-16 0xFEFF. Quando si utilizzano associazioni WSTR e BSTR, il Driver OLE DB per SQL Server non richiede o aggiungere un indicatore ordine byte, come la codifica è implicita dall'associazione. Quando si utilizzano associazioni BYTES, XML o IUNKNOWN, lo scopo è semplicità di gestione di altri processori XML e sistemi di archiviazione. In questo caso, un indicatore ordine byte deve essere presente con XML con codifica UTF-16 e non l'applicazione deve considerare con la codifica, poiché la maggior parte dei processori XML (incluso SQL Server) deduce la codifica controllando i primi byte del valore. I dati XML ricevuti da Driver OLE DB per SQL Server usando byte, XML, o le associazioni di IUNKNOWN sono sempre codificati in UTF-16 con un BOM e senza una dichiarazione di codifica incorporata.  
  
 Le conversioni di dati fornite dai servizi principali OLE DB (**IDataConvert**) non sono applicabili a DBTYPE_XML.  
  
 La convalida viene eseguita durante l'invio dei dati al server. La convalida lato client e la codifica delle modifiche devono essere gestiti dall'applicazione. È consigliabile non elaborano i dati XML direttamente, ma si dovrebbe usare invece un o un lettore SAX per elaborarli.  
  
 DBTYPE_NULL e DBTYPE_EMPTY possono essere associati per i parametri di input ma non per i parametri di output o per i risultati. Se vengono associati per i parametri di input, lo stato deve essere impostato su DBSTATUS_S_ISNULL o DBSTATUS_S_DEFAULT.  
  
 DBTYPE_XML può essere convertito in DBTYPE_EMPTY e DBTYPE_NULL, DBTYPE_EMPTY può essere convertito in DBTYPE_XML, ma DBTYPE_NULL non può essere convertito in DBTYPE_XML. Questo comportamento è coerente con DBTYPE_WSTR.  
  
 DBTYPE_IUNKNOWN è un'associazione supportata (come illustrato nella tabella precedente), ma non sono disponibili conversioni tra DBTYPE_XML e DBTYPE_IUNKNOWN. DBTYPE_IUNKNOWN non può essere utilizzato con DBTYPE_BYREF.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Aggiunte e modifiche ai set di righe OLE DB  
 Il Driver OLE DB per SQL Server aggiunti nuovi valori o modifiche a molti dei set di righe dello schema OLE DB principali.  
  
#### <a name="the-columns-and-procedureparameters-schema-rowsets"></a>Set di righe dello schema COLUMNS e PROCEDURE_PARAMETERS  
 Aggiunte di righe dello schema COLUMNS e procedure_parameters sono includono le colonne seguenti:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Nome di un catalogo in cui viene definita una raccolta di XML Schema. NULL per una colonna non XML o una colonna XML non tipizzata.|  
|SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Nome di uno schema in cui viene definita una raccolta di XML Schema. NULL per una colonna non XML o una colonna XML non tipizzata.|  
|SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nome della raccolta di XML Schema. NULL per una colonna non XML o una colonna XML non tipizzata.|  
  
#### <a name="the-providertypes-schema-rowset"></a>Set di righe dello schema PROVIDER_TYPES  
 Nel set di righe dello schema PROVIDER_TYPES, il valore COLUMN_SIZE è 0 per il **xml** tipo di dati, e DATA_TYPE è DBTYPE_XML.  
  
#### <a name="the-ssxmlschema-schema-rowset"></a>Set di righe dello schema SS_XMLSCHEMA  
 È stato introdotto un nuovo set di righe dello schema per i client, denominato SS_XMLSCHEMA, che consente il recupero di informazioni su XML Schema. Il set di righe SS_XMLSCHEMA contiene le colonne seguenti:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Catalogo cui appartiene una raccolta XML.|  
|SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Schema cui appartiene una raccolta XML.|  
|SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nome di una raccolta di XML Schema per colonne XML tipizzate. In caso contrario, NULL.|  
|TARGETNAMESPACEURI|DBTYPE_WSTR|Spazio dei nomi di destinazione di un elemento XML Schema.|  
|SCHEMACONTENT|DBTYPE_WSTR|Contenuto dell'elemento XML Schema.|  
  
 L'ambito di ogni XML Schema è costituito da nome del catalogo, nome dello schema, nome della raccolta di schemi e URI dello spazio dei nomi di destinazione. Viene inoltre definito un nuovo GUID con il nome DBSCHEMA_XML_COLLECTIONS. Il numero di restrizioni e di colonne limitate per il set di righe dello schema SS_XMLSCHEMA viene definito come segue.  
  
|GUID|Numero di restrizioni|Colonne limitate|  
|----------|----------------------------|------------------------|  
|DBSCHEMA_XML_COLLECTIONS|4|SCHEMACOLLECTION_CATALOGNAME<br /><br /> SCHEMACOLLECTION_SCHEMANAME<br /><br /> SCHEMACOLLECTIONNAME<br /><br /> TARGETNAMESPACEURI|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Aggiunte e modifiche ai set di proprietà OLE DB  
 Il Driver OLE DB per SQL Server aggiunti nuovi valori o modifiche a molte delle proprietà OLE DB principali set.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERPARAMETER  
 Per supportare le **xml** del tipo di dati tramite OLE DB, il Driver OLE DB per SQL Server implementa il nuovo set di proprietà DBPROPSET_SQLSERVERPARAMETER, che contiene i valori seguenti.  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Nome di un catalogo (database) in cui viene definita una raccolta di XML Schema. Una parte dell'identificatore di nome in tre parti di SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Nome di un elemento XML Schema all'interno della raccolta di schemi. Una delle tre parti di cui è composto l'identificatore del nome SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nome della raccolta di XML Schema all'interno del catalogo. Una delle tre parti di cui è composto l'identificatore del nome SQL.|  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERCOLUMN  
 Per supportare la creazione di tabelle di **ITableDefinition** interfaccia, il Driver OLE DB per SQL Server aggiunge tre nuove colonne al set di proprietà DBPROPSET_SQLSERVERCOLUMN.  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME|VT_BSTR|Per le colonne XML tipizzate, questa proprietà è una stringa che specifica il nome del catalogo in cui viene archiviato l'elemento XML Schema. Per gli altri tipi di colonna questa proprietà restituisce una stringa vuota.|  
|SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME|VT_BSTR|Per le colonne XML tipizzate, questa proprietà è una stringa che specifica il nome dell'elemento XML Schema che definisce la colonna.|  
|SSPROP_COL_XML_SCHEMACOLLECTIONNAME|VT_BSTR|Per le colonne XML tipizzate, questa proprietà è una stringa che specifica il nome della raccolta di XML Schema che definisce il valore.|  
  
 Analogamente ai valori di SSPROP_PARAM, tutte queste proprietà sono facoltative e non sono specificate per impostazione predefinita. SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME e SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME possono essere specificate solo se si specifica SSPROP_COL_XML_SCHEMACOLLECTIONNAME. Se quando si passano dati XML al server questi valori sono inclusi, ne viene verificata l'esistenza (validità) rispetto al database corrente e i dati dell'istanza vengono controllati rispetto allo schema. In tutti i casi, per essere validi tali valori devono essere tutti vuoti o specificati.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Aggiunte e modifiche alle interfacce OLE DB  
 Il Driver OLE DB per SQL Server aggiunti nuovi valori o modifiche a molte delle interfacce OLE DB principali.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Interfaccia ISSCommandWithParameters  
 Per supportare le **xml** del tipo di dati tramite OLE DB, il Driver OLE DB per SQL Server implementa un numero di modifiche inclusi l'aggiunta del [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md) interfaccia. Questa nuova interfaccia eredita dall'interfaccia OLE DB principale **ICommandWithParameters**. Oltre ai tre metodi ereditati da **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, e **SetParameterInfo**; **ISSCommandWithParameters** fornisce il [GetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md) e [SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) i metodi utilizzati per gestire server specifiche tipi di dati.  
  
> [!NOTE]  
>  Il **ISSCommandWithParameters** interfaccia consente inoltre di utilizzare la nuova struttura SSPARAMPROPS struttura.  
  
#### <a name="the-icolumnsrowset-interface"></a>Interfaccia IColumnsRowset  
 Il Driver OLE DB per SQL Server consente di aggiungere quanto segue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-colonne specifiche nel set di righe restituito dal **IColumnRowset:: GetColumnsRowset** metodo. Tali colonne contengono il nome in tre parti di una raccolta di XML Schema. Per le colonne non XML o per le colonne XML non tipizzate, le tre colonne assumono tutte il valore predefinito NULL.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Catalogo cui appartiene una raccolta di XML Schema.<br /><br /> In caso contrario, NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Schema cui appartiene una raccolta di XML Schema. In caso contrario, NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nome della raccolta di XML Schema per le colonne XML tipizzate. In caso contrario, NULL.|  
  
#### <a name="the-irowset-interface"></a>Interfaccia IRowset  
 Un'istanza XML in una colonna XML viene recuperata mediante la **IRowset:: GetData** metodo. A seconda dell'associazione specificata dal client, un'istanza XML può essere recuperata come DBTYPE_BSTR, DBTYPE_WSTR DBTYPE_VARIANT, DBTYPE_XML, DBTYPE_STR, DBTYPE_BYTES o come interfaccia tramite DBTYPE_IUNKNOWN. Se il consumer specifica DBTYPE_BSTR, DBTYPE_WSTR o DBTYPE_VARIANT, il provider converte l'istanza XML nel tipo richiesto dall'utente e la archivia nella posizione specificata nell'associazione corrispondente.  
  
 Se il consumer specifica DBTYPE_IUNKNOWN e imposta il *pObject* argomento NULL o set di *pObject* argomento su IID_ISequentialStream, il provider restituisce un **ISequentialStream** interfaccia al consumer, in modo che il consumer può trasmettere i dati XML all'esterno della colonna. **ISequentialStream** quindi restituisce i dati XML come flusso di caratteri Unicode.  
  
 Quando viene restituito un valore XML associato a DBTYPE_IUNKNOWN, il provider segnala un valore di dimensioni `sizeof (IUnknown *)`. Questo comportamento è coerenza con l'approccio adottato quando una colonna è associata come DBTYPE_IUnknown o DBTYPE_IDISPATCH e tramite DBTYPE_IUNKNOWN/ISequentialStream quando non è possibile determinare le dimensioni della colonna esatto.  
  
#### <a name="the-irowsetchange-interface"></a>Interfaccia IRowsetChange  
 Il consumer può aggiornare un'istanza XML in una colonna utilizzando due modalità diverse. Il primo consiste nell'utilizzare l'oggetto di archiviazione **ISequentialStream** creato dal provider. Il consumer può chiamare il **ISequentialStream:: Write** metodo aggiornare direttamente l'istanza XML restituita dal provider.  
  
 Il secondo approccio consiste nell'utilizzare **IRowsetChange:: SetData** o **IRowsetChange:: InsertRow** metodi. In questo approccio è possibile specificare un'istanza XML nel buffer del consumer in un'associazione di tipo DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML o DBTYPE_IUNKNOWN.  
  
 Se viene specificato DBTYPE_BSTR, DBTYPE_WSTR o DBTYPE_VARIANT, il provider archivia l'istanza XML che si trovano nel buffer del consumer nella colonna appropriata.  
  
 Se si specifica DBTYPE_IUNKNOWN/ISequentialStream, se il consumer non è specificato alcun oggetto di archiviazione, il consumer deve creare un' **ISequentialStream** dell'oggetto in anticipo, associare il documento XML con l'oggetto e quindi passare il oggetto al provider tramite il **IRowsetChange:: SetData** metodo. Il consumer può creare anche uno spazio di archiviazione dell'oggetto, impostare l'argomento pObject su IID_ISequentialStream, creare un **ISequentialStream** dell'oggetto e quindi passare il **ISequentialStream** dell'oggetto per il **IRowsetChange:: SetData** metodo. In entrambi i casi, il provider può recuperare l'oggetto XML tramite il **ISequentialStream** dell'oggetto e di inserirla in una colonna appropriata.  
  
#### <a name="the-irowsetupdate-interface"></a>Interfaccia IRowsetUpdate  
 **IRowsetUpdate** interfaccia fornisce funzionalità per aggiornamenti ritardati. I dati resi disponibili per i set di righe non vengono resi disponibili ad altre transazioni finché il consumer chiama il **IRowsetUpdate:: Update** metodo.  
  
#### <a name="the-irowsetfind-interface"></a>Interfaccia IRowsetFind  
 Il **irowsetfind:: FindNextRow** metodo non funziona con il **xml** tipo di dati. Quando **irowsetfind:: FindNextRow** viene chiamato e *hAccessor* argomento specifica una colonna di tipo DBTYPE_XML, viene restituito DB_E_BADBINDINFO. Ciò si verifica indipendentemente dal tipo di colonna di cui si esegue la ricerca. Per qualsiasi altro tipo di associazione, il **FindNextRow** ha esito negativo con DB_E_BADCOMPAREOP se la colonna da cercare è la **xml** tipo di dati.  
 
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [OLE DB ISSCommandWithParameters &#40; &#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
