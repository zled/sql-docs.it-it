---
title: "Indice delle proprietà dinamiche ADO | Documenti Microsoft"
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
- dynamic properties [ADO], index
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c56ef6d6a146d1613bdd11618fadb3b11296fe7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="ado-dynamic-property-index"></a>Indice delle proprietà dinamiche ADO
Provider di dati, i provider di servizi e componenti del servizio possono aggiungere proprietà dinamiche per la **proprietà** raccolte di oggetti [connessione](../../../ado/reference/ado-api/connection-object-ado.md) e [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti. Un determinato provider può inoltre inserire le proprietà aggiuntive quando questi oggetti sono aperti. Alcune di queste proprietà sono elencate nella [proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md) sezione. Un elenco dei singoli provider in più di [appendice a: provider](../../../ado/guide/appendixes/appendix-a-providers.md) sezione.  
  
 Le tabelle seguenti sono cross-indexes dei nomi ADO e OLE DB per ogni proprietà dinamica di provider OLE DB standard. I provider possono aggiungere ulteriori proprietà oltre a quelle elencate di seguito. Per informazioni specifiche sulle proprietà dinamiche specifiche del provider, vedere la documentazione del provider.  
  
 Riferimento di OLE DB Programmer fa riferimento a un nome della proprietà ADO il termine "Descrizione". Per ulteriori informazioni su queste proprietà standard, cercare o sfogliare l'indice di [documentazione di OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)per la proprietà OLE DB in base al nome.  
  
## <a name="connection-dynamic-properties"></a>Proprietà di connessione dinamica  
  
|Nome della proprietà ADO|Nome della proprietà OLE DB|  
|-----------------------|--------------------------|  
|Sessioni attive|DBPROP_ACTIVESESSIONS|  
|Interruzione asincrona|DBPROP_ASYNCTXNABORT|  
|Commit Asynchable|DBPROP_ASYNCTNXCOMMIT|  
|Livelli di isolamento autocommit|DBPROP_SESS_AUTOCOMMITISOLEVELS|  
|Percorso del catalogo|DBPROP_CATALOGLOCATION|  
|Termine catalogo|DBPROP_CATALOGTERM|  
|Definizione di colonna|DBPROP_COLUMNDEFINITION|  
|Timeout di connessione|DBPROP_INIT_TIMEOUT|  
|Catalogo corrente|DBPROP_CURRENTCATALOG|  
|Data Source|DBPROP_INIT_DATASOURCE|  
|Nome origine dati|DBPROP_DATASOURCENAME|  
|Modello di Threading oggetto origine dei dati|DBPROP_DSOTHREADMODEL|  
|Nome DBMS|DBPROP_DBMSNAME|  
|Versione DBMS|DBPROP_DBMSVER|  
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|  
|GRUPPO di assistenza|DBPROP_GROUPBY|  
|Supporto tabelle eterogenee|DBPROP_HETEROGENEOUSTABLES|  
|Identificatore distinzione maiuscole/minuscole|DBPROP_IDENTIFIERCASE|  
|Catalogo iniziale|DBPROP_INIT_CATALOG|  
|Livelli di isolamento|DBPROP_SUPPORTEDTXNISOLEVELS|  
|Memorizzazione di isolamento|DBPROP_SUPPORTEDTXNISORETAIN|  
|Locale Identifier|DBPROP_INIT_LCID|  
|Percorso|DBPROP_INIT_LOCATION|  
|Dimensione massima dell'indice|DBPROP_MAXINDEXSIZE|  
|Dimensioni massime delle righe|DBPROP_MAXROWSIZE|  
|Dimensioni massime riga con BLOB|DBPROP_MAXROWSIZEINCLUDESBLOB|  
|Numero massimo di tabelle in SELECT|DBPROP_MAXTABLESINSELECT|  
|Elabora partizione/i|DBPROP_INIT_MODE|  
|Più set di parametri|DBPROP_MULTIPLEPARAMSETS|  
|Più risultati|DBPROP_MULTIPLERESULTS|  
|Più oggetti di archiviazione|DBPROP_MULTIPLESTORAGEOBJECTS|  
|Aggiornamento di più tabelle|DBPROP_MULTITABLEUPDATE|  
|Ordine delle regole di confronto NULL|DBPROP_NULLCOLLATION|  
|Comportamento di concatenazione NULL|DBPROP_CONCATNULLBEHAVIOR|  
|Servizi OLE DB|DBPROP_INIT_OLEDBSERVICES|  
|OLE DB versione|DBPROP_PROVIDEROLEDBVER|  
|Supporto dell'oggetto OLE|DBPROP_OLEOBJECTS|  
|Aprire il supporto di set di righe|DBPROP_OPENROWSETSUPPORT|  
|Colonne ORDER BY nell'elenco di selezione|DBPROP_ORDERBYCOLUMNSINSELECT|  
|Disponibilità dei parametri di output|DBPROP_OUTPUTPARAMETERAVAILABILITY|  
|Passare dalle funzioni di accesso di riferimento|DBPROP_BYREFACCESSORS|  
|Password|DBPROP_AUTH_PASSWORD|  
|Persist Security Info|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|  
|Tipo di ID persistenti|DBPROP_PERSISTENTIDTYPE|  
|Preparare il comportamento di interruzione|DBPROP_PREPAREABORTBEHAVIOR|  
|Preparare il comportamento di Commit|DBPROP_PREPARECOMMITBEHAVIOR|  
|Termine procedura|DBPROP_PROCEDURETERM|  
|Messaggio di richiesta|DBPROP_INIT_PROMPT|  
|Nome descrittivo del provider|DBPROP_PROVIDERFRIENDLYNAME|  
|Provider Name|DBPROP_PROVIDERFILENAME|  
|Versione del provider|DBPROP_PROVIDERVER|  
|Origine dati di sola lettura|DBPROP_DATASOURCEREADONLY|  
|Conversioni di set di righe nel comando|DBPROP_ROWSETCONVERSIONSONCOMMAND|  
|Termine schema|DBPROP_SCHEMATERM|  
|Utilizzo dello schema|DBPROP_SCHEMAUSAGE|  
|Supporto di SQL|DBPROP_SQLSUPPORT|  
|Archiviazione strutturata|DBPROP_STRUCTUREDSTORAGE|  
|Supporto delle sottoquery|DBPROP_SUBQUERIES|  
|Termine di una tabella|DBPROP_TABLETERM|  
|Transazione DDL|DBPROP_SUPPORTEDTXNDDL|  
|ID utente|DBPROP_AUTH_USERID|  
|Nome utente|DBPROP_USERNAME|  
|Handle di finestra|DBPROP_INIT_HWND|  
  
## <a name="recordset-dynamic-properties"></a>Proprietà dinamiche dell'oggetto Recordset  
 Si noti che il **proprietà dinamiche** del **Recordset** oggetto andare fuori ambito (diventano non disponibile) quando il **Recordset** viene chiuso.  
  
|Nome della proprietà ADO|Nome della proprietà OLE DB|  
|-----------------------|--------------------------|  
|IAccessor|DBPROP_IACCESSOR|  
|IChapteredRowset||  
|IColumnsInfo|DBPROP_ICOLUMNSINFO|  
|IColumnsRowset|DBPROP_ICOLUMNSROWSET|  
|IConnectionPointContainer|DBPROP_ICONNECTIONPOINTCONTAINER|  
|IConvertType||  
|ILockBytes|DBPROP_ILOCKBYTES|  
|IRowset|DBPROP_IROWSET|  
|IDBAsynchStatus|DBPROP_IDBASYNCHSTATUS|  
|IParentRowset||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|IRowsetExactScroll||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|IRowsetIdentity|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|IRowsetRefresh|DBPROP_IROWSETREFRESH|  
|IRowsetResynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|IRowsetView|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|Ordine di accesso|DBPROP_ACCESSORDER|  
|Set di righe solo di Accodamento|DBPROP_APPENDONLY|  
|Elaborazione asincrona del set di righe|DBPROP_ROWSET_ASYNCH|  
|Ricalcolo automatico|DBPROP_ADC_AUTORECALC|  
|Dimensione di recupero in background|DBPROP_ASYNCHFETCHSIZE|  
|Background Thread Priority|DBPROP_ASYNCHTHREADPRIORITY|  
|Dimensioni batch|DBPROP_ADC_BATCHSIZE|  
|Il blocco di oggetti di archiviazione|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Tipo di segnalibro|DBPROP_BOOKMARKTYPE|  
|Supporta|DBPROP_IROWSETLOCATE|  
|Segnalibri ordinati|DBPROP_ORDEREDBOOKMARKS|  
|Memorizzare nella cache le righe figlio|DBPROP_ADC_CACHECHILDROWS|  
|Memorizzare nella cache colonne posticipate|DBPROP_CACHEDEFERRED|  
|Modificare le righe inserite|DBPROP_CHANGEINSERTEDROWS|  
|Privilegi di colonna|DBPROP_COLUMNRESTRICT|  
|Notifica di Set di colonne|DBPROP_NOTIFYCOLUMNSET|  
|Colonna accessibile in scrittura|DBPROP_MAYWRITECOLUMN|  
|Timeout del comando|DBPROP_COMMANDTIMEOUT|  
|Versione del motore del cursore|DBPROP_ADC_CEVER|  
|Rinviare colonna|DBPROP_DEFERRED|  
|Aggiornamenti degli oggetti di archiviazione di ritardo|DBPROP_DELAYSTORAGEOBJECTS|  
|Recuperare le versioni precedenti|DBPROP_CANFETCHBACKWARDS|  
|Operazioni di filtro|DBPROP_FILTERCOMPAREOPS|  
|Operazioni di ricerca|DBPROP_FINDCOMPAREOPS|  
|Colonne nascoste (conteggio)|DBPROP_HIDDENCOLUMNS|  
|Contengono righe|DBPROP_CANHOLDROWS|  
|Righe immobili|DBPROP_IMMOBILEROWS|  
|Dimensione di recupero iniziale|DBPROP_ASYNCHPREFETCHSIZE|  
|Valore letterale segnalibri|DBPROP_LITERALBOOKMARKS|  
|Identità riga letterale|DBPROP_LITERALIDENTITY|  
|Gestire lo stato di modifica|DBPROP_ADC_MAINTAINCHANGESTATUS|  
|Numero massimo di righe aperto|DBPROP_MAXOPENROWS|  
|Numero massimo di righe in sospeso|DBPROP_MAXPENDINGROWS|  
|Numero massimo di righe|DBPROP_MAXROWS|  
|Utilizzo memoria|DBPROP_MEMORYUSAGE|  
|Granularità di notifica|DBPROP_NOTIFICATIONGRANULARITY|  
|Fasi di notifica|DBPROP_NOTIFICATIONPHASES|  
|Oggetti transazione|DBPROP_TRANSACTEDOBJECT|  
|Modifiche di altri utenti visibili|DBPROP_OTHERUPDATEDELETE|  
|Inserimenti altrui visibili|DBPROP_OTHERINSERT|  
|Proprie modifiche visibili|DBPROP_OWNUPDATEDELETE|  
|Inserimenti visibili|DBPROP_OWNINSERT|  
|Mantieni in caso di interruzione|DBPROP_ABORTPRESERVE|  
|Mantieni in caso di Commit|DBPROP_COMMITPRESERVE|  
|Private1||  
|Riavvio rapido|DBPROP_QUICKRESTART|  
|Eventi rientranti|DBPROP_REENTRANTEVENTS|  
|Rimuovere le righe eliminate|DBPROP_REMOVEDELETED|  
|Più modifiche del report|DBPROP_REPORTMULTIPLECHANGES|  
|Modificare la forma di nome|DBPROP_ADC_RESHAPENAME|  
|Risincronizzazione di comando|DBPROP_ADC_CUSTOMRESYNCH|  
|Restituisci inserimenti in sospeso|DBPROP_RETURNPENDINGINSERTS|  
|Notifica di eliminazione riga|DBPROP_NOTIFYROWDELETE|  
|Notifica prima modifica riga|DBPROP_NOTIFYROWFIRSTCHANGE|  
|Notifica inserimento riga|DBPROP_NOTIFYROWINSERT|  
|Privilegi di riga|DBPROP_ROWRESTRICT|  
|Notifica di risincronizzazione di riga|DBPROP_NOTIFYROWRESYNCH|  
|Modello di Threading di riga|DBPROP_ROWTHREADMODEL|  
|Notifica annullamento Modifica riga|DBPROP_NOTIFYROWUNDOCHANGE|  
|Notifica annullamento eliminazione riga|DBPROP_NOTIFYROWUNDODELETE|  
|Notifica annullamento inserimento riga|DBPROP_NOTIFYROWUNDOINSERT|  
|Notifica di aggiornamento di riga|DBPROP_NOTIFYROWUPDATE|  
|Notifica modifica posizione recupero di set di righe|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|  
|Notifica il rilascio di set di righe|DBPROP_NOTIFYROWSETRELEASE|  
|Scorrere in senso inverso|DBPROP_CANSCROLLBACKWARDS|  
|Cursore del server|DBPROP_SERVERCURSOR|  
|Ignora segnalibri eliminati|DBPROP_BOOKMARKSKIPPED|  
|Identità riga forte|DBPROP_STRONGIDENTITY|  
|Catalogo univoca|DBPROP_ADC_UNIQUECATALOG|  
|Righe univoche|DBPROP_UNIQUEROWS|  
|Schema univoco|DBPROP_ADC_UNIQUESCHEMA|  
|Tabella univoca|DBPROP_ADC_UNIQUETABLE|  
|Aggiornabile|DBPROP_UPDATABILITY|  
|Criteri di aggiornamento|DBPROP_ADC_UPDATECRITERIA|  
|Risincronizzazione di aggiornamento|DBPROP_ADC_UPDATERESYNC|  
|Utilizzare i segnalibri|DBPROP_BOOKMARKS|