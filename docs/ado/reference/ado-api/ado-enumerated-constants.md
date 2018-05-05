---
title: Costanti enumerate ADO | Documenti Microsoft
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
helpviewer_keywords:
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151b4e88b3f094cd44ac7078e5d16e0b0730a9e3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-enumerated-constants"></a>Costanti enumerate ADO
Per semplificare il debug, le enumerazioni ADO specificano un valore per ciascuna costante. Tuttavia, questo valore è puramente indicativo e può variare da una versione di ADO a un altro. Il codice deve dipendere esclusivamente il nome, non il valore effettivo di ogni costante enumerata.  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Per un servizio dati di riferimento **Recordset** dell'oggetto, specifica la priorità di esecuzione del thread asincrona che recupera i dati.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Specifica quando il **MSDataShape** provider nuovamente Calcola l'aggregazione e le colonne calcolate in un modello gerarchico **Recordset**.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Specifica i campi che è possono utilizzare per rilevare i conflitti durante un aggiornamento ottimistico di una riga dell'origine dati con un **Recordset** oggetto.|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Specifica se il **UpdateBatch** metodo è seguito da implicita **Resync** operazione del metodo e in tal caso, l'ambito dell'operazione.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Specifica i record interessati da un'operazione.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Specifica un segnalibro che indica dove iniziare l'operazione.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Specifica la modalità di interpretazione di un argomento del comando.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Specifica la posizione relativa di due record rappresentati dai relativi segnalibri.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Specifica le autorizzazioni disponibili per la modifica dei dati in un **connessione**, aprire un **Record**, o specificando i valori per il **modalità** proprietà del  **Record** e **flusso** oggetti.|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Specifica se il **aprire** metodo di un **connessione** oggetto deve essere restituito dopo (in modo sincrono) o prima (in modo asincrono) in cui viene stabilita la connessione.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Specifica se deve essere visualizzata una finestra di dialogo per la richiesta di parametri mancanti quando si apre una connessione a un'origine dati ODBC.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Specifica il comportamento del **CopyRecord** metodo.|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Specifica la posizione del motore del cursore.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Specifica il tipo di funzionalità di **supporta** consigliabile testare il metodo per.|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Specifica il tipo di cursore utilizzato in un **Recordset** oggetto.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Specifica il tipo di dati di un **campo**, **parametro**, o **proprietà**.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Specifica lo stato di modifica di un record.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Specifica il tipo di errore di run-time di ADO.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Specifica il motivo che ha causato un evento si verifichi.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Specifica lo stato corrente dell'esecuzione di un evento.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Specifica come un provider deve eseguire un comando.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Specifica i campi speciali a cui fa riferimento il **campi** raccolta di un **Record** oggetto.|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Specifica uno o più attributi di un **campo** oggetto.|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Specifica lo stato di un **campo** oggetto.|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Specifica il gruppo di record da filtrare un **Recordset**.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Specifica il numero di record da recuperare da un **Recordset**.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Specifica il livello di isolamento delle transazioni per un **connessione** oggetto.|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Specifica il carattere utilizzato come separatore di riga nel testo **flusso** oggetti.|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Specifica il tipo di blocco applicato ai record durante la modifica.|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Specifica i record che devono essere restituiti al server.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Specifica il comportamento del **Record** oggetto **MoveRecord** metodo.|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Specifica se un oggetto è aperto o chiuso, la connessione a un'origine dati, l'esecuzione di un comando o il recupero dei dati.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Specifica gli attributi di un **parametro** oggetto.|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Specifica se il **parametro** rappresenta un parametro di input, un parametro di output o entrambi, o se il parametro è il valore restituito da una stored procedure.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Specifica il formato in cui salvare un **Recordset**.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Specifica la posizione corrente del puntatore del record all'interno di un **Recordset**.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Specifica gli attributi di un **proprietà** oggetto.|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Specifica per il **Record** oggetto **aprire** metodo se un oggetto esistente **Record** deve essere aperto, o un nuovo **Record** deve essere creato.|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Specifica le opzioni per aprire un **Record**. Questi valori possono essere combinati utilizzando l'operatore OR.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Specifica lo stato di un record per quanto riguarda gli aggiornamenti in batch e altre operazioni bulk.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Specifica il tipo di **Record** oggetto.|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Specifica se i valori sottostanti vengono sovrascritti da una chiamata a **Resync**.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Specifica se un file deve essere creato o sovrascritto durante il salvataggio da un **flusso** oggetto. I valori possono essere combinati con un operatore AND.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Specifica il tipo di schema **Recordset** che il **OpenSchema** recupera metodo. Specifica la direzione di una ricerca di record all'interno di un **Recordset**.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Specifica la direzione di una ricerca di record all'interno di un **Recordset**. Specifica il tipo di **Seek** da eseguire.|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Specifica il tipo di **Seek** da eseguire. Specifica le opzioni per aprire un **flusso** oggetto. I valori possono essere combinati con un operatore AND.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Specifica le opzioni per aprire un **flusso** oggetto. I valori possono essere combinati con un operatore AND. Specifica se leggere l'intero flusso o la riga successiva in un **flusso** oggetto.|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Specifica se leggere l'intero flusso o la riga successiva in un **flusso** oggetto. Specifica il tipo di dati archiviati in un **flusso** oggetto.|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Specifica il tipo di dati archiviati in un **flusso** oggetto. Specifica se un separatore di riga viene aggiunto alla stringa di scrivere un **flusso** oggetto.|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Specifica se un separatore di riga viene aggiunto alla stringa di scrivere un **flusso** oggetto. Specifica il formato durante il recupero di un **Recordset** sotto forma di stringa.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Specifica il formato durante il recupero di un **Recordset** sotto forma di stringa. Specifica gli attributi della transazione di un **connessione** oggetto.|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Specifica gli attributi della transazione di un **connessione** oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte di ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Appendice b: errori di ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Metodi ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Le interfacce e gli oggetti ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Proprietà ADO](../../../ado/reference/ado-api/ado-properties.md)
