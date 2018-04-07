---
title: Utilizzo di tipi definiti dall'utente | Documenti Microsoft
description: Utilizzo di tipi definiti dall'utente con il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_DATASOURCEINFO property set
- UDTs [OLE DB Driver for SQL Server]
- user-defined types [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- MSOLEDBSQL, user-defined types
- OLE DB Driver for SQL Server, user-defined types
- data access [OLE DB Driver for SQL Server], user-defined types
- ISSCommandWithParameters interface
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e982746608d6fc6bae25a6f54ee58fee5b9a52a8
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="using-user-defined-types"></a>Utilizzo dei tipi definiti dall'utente (UDT)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sono stati introdotti i tipi definiti dall'utente (UDT). Tipi definiti dall'utente estendono il sistema di tipi SQL consentendo di archiviare oggetti e strutture di dati personalizzati in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database. I tipi definiti dall'utente possono contenere più tipi di dati e possono assumere comportamenti, differenziandoli dai tipi di dati alias tradizionali costituiti da un singolo tipo di dati di sistema [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. I tipi definiti dall'utente vengono definiti utilizzando uno dei linguaggi supportati da .NET Common Language Runtime (CLR) che generano codice verificabile, Sono inclusi Microsoft Visual c#<sup>®</sup> e Visual Basic<sup>®</sup> .NET. I dati vengono esposti come campi e proprietà di una classe o struttura .NET mentre i comportamenti vengono definiti dai metodi della classe o della struttura.  
  
 Un tipo definito dall'utente può essere utilizzato come definizione di colonna di una tabella, come una variabile in un [!INCLUDE[tsql](../../../includes/tsql-md.md)] batch, o come un argomento di un [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedure o funzione.  
  
## <a name="ole-db-driver-for-sql-server"></a>Driver OLE DB per SQL Server  
 Il Driver OLE DB per SQL Server supporta i tipi definiti dall'utente come tipi binari con informazioni sui metadati, che consente di gestire i tipi definiti dall'utente come oggetti. Le colonne di tipo definito dall'utente vengono esposte come DBTYPE_UDT e i relativi metadati vengono esposti tramite l'interfaccia OLE DB principale **IColumnRowset**e il nuovo [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md) interfaccia.  
  
> [!NOTE]  
>  Il **irowsetfind:: FindNextRow** metodo non funziona con il tipo di dati definito dall'utente. Se il tipo definito dall'utente viene utilizzato come tipo di colonna di ricerca, viene restituito DB_E_BADCOMPAREOP.  
  
### <a name="data-bindings-and-coercions"></a>Associazione dati e coercizioni  
 Nella tabella seguente vengono descritte l'associazione e la coercizione che si verificano quando si utilizzano i tipi di dati elencati con un tipo definito dall'utente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le colonne di tipo definito dall'utente vengono esposte tramite il Driver OLE DB per SQL Server come DBTYPE_UDT. È possibile ottenere i metadati tramite i set di righe dello schema appropriati in modo da potere gestire i tipi definiti personalizzati come oggetti.  
  
|Tipo di dati|Al server<br /><br /> **UDT**|Al server<br /><br /> **non-UDT**|Dal server<br /><br /> **UDT**|Dal server<br /><br /> **non-UDT**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_UDT|Supportato<sup>6</sup>|Errore<sup>1</sup>|Supportato<sup>6</sup>|Errore<sup>5</sup>|  
|DBTYPE_BYTES|Supportato<sup>6</sup>|N/A<sup>2</sup>|Supportato<sup>6</sup>|N/A<sup>2</sup>|  
|DBTYPE_WSTR|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|Supportato<sup>4, 6</sup>|N/A<sup>2</sup>|  
|DBTYPE_BSTR|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|Supportato<sup>4</sup>|N/A<sup>2</sup>|  
|DBTYPE_STR|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|Supportato<sup>4, 6</sup>|N/A<sup>2</sup>|  
|DBTYPE_IUNKNOWN|Non supportato|N/A<sup>2</sup>|Non supportato|N/A<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Supportato<sup>6</sup>|N/A<sup>2</sup>|Supportato<sup>4</sup>|N/A<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Supportato<sup>3,6</sup>|N/A<sup>2</sup>|N/D|N/A<sup>2</sup>|  
  
 <sup>1</sup>se un server di tipo diverso da DBTYPE_UDT è specificato con **ICommandWithParameters:: SetParameterInfo** e il tipo di funzione di accesso è DBTYPE_UDT, si verifica un errore quando viene eseguita l'istruzione (DB_E_ERRORSOCCURRED; stato del parametro è DBSTATUS_E_BADACCESSOR). In caso contrario, i dati vengono inviati al server, ma il server restituisce un errore indicando che non è possibile eseguire una conversione implicita dal tipo definito dall'utente al tipo di dati del parametro.  
  
 <sup>2</sup>esula dall'ambito di questo articolo.  
  
 <sup>3</sup> si verifica la conversione dei dati da stringa esadecimale a dati binari.  
  
 <sup>4</sup> si verifica la conversione dei dati da dati binari a stringa esadecimale.  
  
 <sup>5</sup>convalida può verificarsi nella creazione della funzione di accesso o in fase di recupero, l'errore è DB_E_ERRORSOCCURRED, lo stato impostato su DBBINDSTATUS_UNSUPPORTEDCONVERSION dell'associazione.  
  
 <sup>6</sup>può essere utilizzato BY_REF.  
  
 DBTYPE_NULL e DBTYPE_EMPTY possono essere associati per i parametri di input ma non per i parametri di output o per i risultati. Se vengono associati per i parametri di input, lo stato deve essere impostato su DBSTATUS_S_ISNULL o DBSTATUS_S_DEFAULT.  
  
 DBTYPE_UDT può essere convertito anche in DBTYPE_EMPTY e DBTYPE_NULL, ma DBTYPE_NULL e DBTYPE_EMPTY non possono essere convertiti in DBTYPE_UDT. È coerente con DBTYPE_BYTES.  
  
> [!NOTE]  
>  Una nuova interfaccia viene utilizzata per la gestione di tipi definiti dall'utente come parametri, **ISSCommandWithParameters**, che eredita da **ICommandWithParameters**. Le applicazioni devono utilizzare questa interfaccia per impostare almeno SSPROP_PARAM_UDT_NAME del set di proprietà DBPROPSET_SQLSERVERPARAMETER per i parametri UDT. Se questa non operazione viene eseguita, **ICommand:: Execute** restituirà DB_E_ERRORSOCCURRED. Questo set di proprietà e interfaccia viene descritto più avanti in questo articolo.  
  
 Se un tipo definito dall'utente viene inserito in una colonna che non è sufficientemente grande da contenere tutti i relativi dati, **ICommand:: Execute** restituirà S_OK con lo stato DB_E_ERRORSOCCURRED.  
  
 Le conversioni di dati fornite dai servizi principali OLE DB (**IDataConvert**) non sono applicabili a DBTYPE_UDT. Non sono supportate altre associazioni.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Aggiunte e modifiche ai set di righe OLE DB  
 Il Driver OLE DB per SQL Server aggiunti nuovi valori o modifiche a molti dei set di righe dello schema OLE DB principali.  
  
#### <a name="the-procedureparameters-schema-rowset"></a>Set di righe dello schema PROCEDURE_PARAMETERS  
 Al set di righe dello schema PROCEDURE_PARAMETERS sono state effettuate le seguenti aggiunte.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificatore del nome in tre parti.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificatore del nome in tre parti.|  
|SS_UDT_NAME|DBTYPE_WSTR|Identificatore del nome in tre parti.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Nome completo dell'assembly che include il nome del tipo e l'identificazione dell'assembly necessaria a cui deve fare riferimento CLR.|  
  
#### <a name="the-sqlassemblies-schema-rowset"></a>Set di righe dello schema SQL_ASSEMBLIES  
 Il Driver OLE DB per SQL Server espone un nuovo set di righe dello schema specifico del provider che descrive i tipi definiti dall'utente registrati. Il server ASSEMBLY può essere specificato come DBTYPE_WSTR, ma non è presente nel set di righe. Se non viene specificato, il set di righe imposterà come valore predefinito il server corrente. Il set di righe dello schema SQL_ASSEMBLIES viene definito nella tabella seguente:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nome del catalogo dell'assembly contenente il tipo.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nome dello schema o nome del proprietario dell'assembly contenente il tipo. Sebbene l'ambito degli assembly sia il database e non lo schema, gli assembly dispongono di un proprietario qui rappresentato.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|Nome dell'assembly contenente il tipo.|  
|ASSEMBLY_ID|DBTYPE_UI4|L'ID oggetto dell'assembly che contiene il tipo.|  
|PERMISSION_SET|DBTYPE_WSTR|Valore che indica l'ambito di accesso per l'assembly. I valori includono "SAFE", "EXTERNAL_ACCESS" e "UNSAFE".|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|Rappresentazione binaria dell'assembly.|  
  
#### <a name="the-sqlassemblies-dependencies-schema-rowset"></a>Set di righe dello schema SQL_ASSEMBLIES_ DEPENDENCIES  
 Il Driver OLE DB per SQL Server espone un nuovo set di righe dello schema specifico del provider che descrive le dipendenze dell'assembly per un server specificato. ASSEMBLY_SERVER può essere specificato dal chiamante come DBTYPE_WSTR, ma non è presente nel set di righe. Se non viene specificato, il set di righe imposterà come valore predefinito il server corrente. Il set di righe dello schema SQL_ASSEMBLY_DEPENDENCIES viene definito nella tabella seguente:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nome del catalogo dell'assembly contenente il tipo.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nome dello schema o nome del proprietario dell'assembly contenente il tipo. Sebbene l'ambito degli assembly sia il database e non lo schema, gli assembly dispongono di un proprietario qui rappresentato.|  
|ASSEMBLY_ID|DBTYPE_UI4|L'ID oggetto dell'assembly.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|L'ID oggetto dell'assembly di riferimento.|  
  
#### <a name="the-sqlusertypes-schema-rowset"></a>Set di righe dello schema SQL_USER_TYPES  
 Il Driver OLE DB per SQL Server espone nuovi rowset dello schema, SQL_USER_TYPES, che descrive quando vengono aggiunti i tipi definiti dall'utente registrati per un server specificato. UDT_SERVER deve essere specificato dal chiamante come DBTYPE_WSTR, ma non è presente nel set di righe. Il set di righe dello schema SQL_USER_TYPES viene definito nella tabella seguente.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|Per le colonne di tipo definito dall'utente, questa proprietà è una stringa che specifica il nome del catalogo in cui è definito.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|Per le colonne di tipo definito dall'utente, questa proprietà è una stringa che specifica il nome dello schema in cui è definito.|  
|UDT_NAME|DBTYPE_WSTR|Nome dell'assembly contenente la classe UDT.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Il nome completo del tipo (AQN) include il nome del tipo preceduto dallo spazio dei nomi se applicabile.|  
  
#### <a name="the-columns-schema-rowset"></a>Set di righe dello schema COLUMNS  
 Le aggiunte al set di righe dello schema COLUMNS includono le colonne seguenti:  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Per le colonne di tipo definito dall'utente, questa proprietà è una stringa che specifica il nome del catalogo in cui è definito.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Per le colonne di tipo definito dall'utente, questa proprietà è una stringa che specifica il nome dello schema in cui è definito.|  
|SS_UDT_NAME|DBTYPE_WSTR|Nome del tipo definito dall'utente.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Il nome completo del tipo (AQN) include il nome del tipo preceduto dallo spazio dei nomi se applicabile.|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Aggiunte e modifiche ai set di proprietà OLE DB  
 Il Driver OLE DB per SQL Server aggiunti nuovi valori o modifiche a molte delle proprietà OLE DB principali set.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERPARAMETER  
 Per supportare tipi definiti dall'utente tramite OLE DB, il Driver OLE DB per SQL Server implementa il nuovo set di proprietà DBPROPSET_SQLSERVERPARAMETER, che contiene i valori seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|Identificatore del nome in tre parti.<br /><br /> Per i parametri UDT questa proprietà è una stringa che specifica il nome del catalogo in cui viene definito il tipo definito dall'utente.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|Identificatore del nome in tre parti.<br /><br /> Per i parametri UDT questa proprietà è una stringa che specifica il nome dello schema in cui viene definito il tipo definito dall'utente.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|Identificatore del nome in tre parti.<br /><br /> Per le colonne con tipo definito dall'utente questa proprietà è una stringa che specifica il nome costituito da una sola parte del tipo definito dall'utente.|  
  
 SSPROP_PARAM_UDT_NAME è obbligatorio. SSPROP_PARAM_UDT_CATALOGNAME e SSPROP_PARAM_UDT_SCHEMANAME sono facoltativi. Se le proprietà vengono specificate in modo non corretto, verrà restituito DB_E_ERRORSINCOMMAND. Se non vengono specificati SSPROP_PARAM_UDT_CATALOGNAME e SSPROP_PARAM_UDT_SCHEMANAME, il tipo definito dall'utente dovrà essere definito nello stesso database e nello stesso schema della tabella. Se la definizione UDT non è presente nello stesso schema della tabella, ma nello stesso database, sarà necessario specificare SSPROP_PARAM_UDT_SCHEMANAME. Se la definizione di tipo definito dall'utente è in un database diverso, quindi SSPROP_PARAM_UDT_CATALOGNAME e SSPROP_PARAM_UDT_SCHEMANAME deve essere specificato.  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERCOLUMN  
 Per supportare la creazione di tabelle di **ITableDefinition** interfaccia, il Driver OLE DB per SQL Server include le seguenti tre nuove colonne al set di proprietà DBPROPSET_SQLSERVERCOLUMN.  
  
|Nome|Description|Tipo|Description|  
|----------|-----------------|----------|-----------------|  
|SSPROP_COL_UDT_CATALOGNAME|UDT_CATALOGNAME|VT_BSTR|Per le colonne di tipo DBTYPE_UDT questa proprietà è una stringa che specifica il nome del catalogo in cui viene definito il tipo definito dall'utente.|  
|SSPROP_COL_UDT_SCHEMANAME|UDT_SCHEMANAME|VT_BSTR|Per le colonne di tipo DBTYPE_UDT questa proprietà è una stringa che specifica il nome dello schema in cui viene definito il tipo definito dall'utente.|  
|SSPROP_COL_UDT_NAME|UDT_NAME|VT_BSTR|Per le colonne di tipo DBTYPE_UDT questa proprietà è una stringa che specifica il nome costituito da una singola parte del tipo definito dall'utente. Per gli altri tipi di colonna questa proprietà restituisce una stringa vuota.|  
  
> [!NOTE]  
>  I tipi definiti dall'utente non sono presenti nel set di righe dello schema PROVIDER_TYPES. Tutte le colonne dispongono dell'accesso in lettura e scrittura.  
  
 ADO farà riferimento a queste proprietà tramite la voce corrispondente nella colonna Descrizione.  
  
 SSPROP_COL_UDTNAME è obbligatorio. SSPROP_COL_UDT_CATALOGNAME e SSPROP_COL_UDT_SCHEMANAME sono facoltativi. Se le proprietà vengono specificate in modo errato, **DB_E_ERRORSINCOMMAND** verranno restituiti.  
  
 Se non vengono specificati SSPROP_COL_UDT_CATALOGNAME e SSPROP_COL_UDT_SCHEMANAME, il tipo definito dall'utente dovrà essere definito nello stesso database e nello stesso schema della tabella.  
  
 Se la definizione UDT non è presente nello stesso schema della tabella, ma nello stesso database, sarà necessario specificare SSPROP_COL_UDT_SCHEMANAME.  
  
 Se la definizione UDT è presente in un database diverso, sarà necessario specificare SSPROP_COL_UDT_CATALOGNAME e SSPROP_COL_UDT_SCHEMANAME.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Aggiunte e modifiche alle interfacce OLE DB  
 Il Driver OLE DB per SQL Server aggiunti nuovi valori o modifiche a molte delle interfacce OLE DB principali.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Interfaccia ISSCommandWithParameters  
 Per supportare tipi definiti dall'utente tramite OLE DB, il Driver OLE DB per SQL Server implementa un numero di modifiche, inclusa l'aggiunta del **ISSCommandWithParameters** interfaccia. Questa nuova interfaccia eredita dall'interfaccia OLE DB principale **ICommandWithParameters**. Oltre ai tre metodi ereditati da **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, e **SetParameterInfo**; **ISSCommandWithParameters** fornisce il **GetParameterProperties** e **SetParameterProperties** metodi che consentono di specifici server di handle tipi di dati.  
  
> [!NOTE]  
>  Il **ISSCommandWithParameters** interfaccia consente inoltre di utilizzare la nuova struttura SSPARAMPROPS struttura.  
  
#### <a name="the-icolumnsrowset-interface"></a>Interfaccia IColumnsRowset  
 Oltre ai **ISSCommandWithParameters** interfaccia, il Driver OLE DB per SQL Server aggiunti nuovi valori nel set di righe restituito dalla chiamata il **IColumnsRowset:: Getcolumnrowset** inclusi (metodo) di seguito.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificatore del nome di catalogo del tipo definito dall'utente.|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificatore del nome dello schema del tipo definito dall'utente.|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|Identificatore del nome del tipo definito dall'utente.|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Nome completo dell'assembly che include il nome del tipo e l'identificazione dell'assembly necessaria a cui deve fare riferimento CLR.|  
  
 È possibile differenziare una colonna di tipo definito dall'utente di server dagli altri tipi binari quando DBCOLUMN_TYPE è impostato su DBTYPE_UDT analizzando i metadati UDT aggiunti specificato nella tabella precedente. Se tali dati sono parzialmente completi, il tipo di server sarà un tipo definito dall'utente. Per i tipi di server non UDT queste colonne vengono sempre restituite come NULL.  
 
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [OLE DB ISSCommandWithParameters & #40; & #41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
