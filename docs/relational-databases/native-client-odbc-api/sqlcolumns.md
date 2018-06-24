---
title: SQLColumns | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
caps.latest.revision: 62
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ca8fab6d42ab562caa4fd0da380094ed42409d0d
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695682"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumns** restituisce SQL_SUCCESS se esistono o meno valori per il *CatalogName*, *TableName*, o *ColumnName* parametri. **SQLFetch** restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
> [!NOTE]  
>  Per i tipi di valori di grandi dimensioni, tutti i parametri della lunghezza verranno restituiti con un valore di SQL_SS_LENGTH_UNLIMITED.  
  
 **SQLColumns** può essere eseguito su un cursore server statico. Un tentativo di eseguire **SQLColumns** su un cursore aggiornabile (dinamico o keyset) restituirà SQL_SUCCESS_WITH_INFO che indica che il tipo di cursore è stato modificato.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la segnalazione di informazioni relative alle tabelle sui server collegati mediante l'accettazione di un nome composto da due parti per il *CatalogName* parametro: *linked_server_name*.  
  
 Per ODBC 2. *x* le applicazioni non utilizzano caratteri jolly in *TableName*, **SQLColumns** restituisce informazioni riguardo a qualsiasi tabella il cui nome corrisponde a *TableName*e di proprietà dell'utente corrente. Se l'utente corrente non possiede alcuna tabella il cui nome corrisponde la *TableName* parametro **SQLColumns** restituisce informazioni su qualsiasi tabella appartenente ad altri utenti in cui il nome della tabella corrisponde il  *TableName* parametro. Per ODBC 2. *x* applicazioni che utilizzano caratteri jolly **SQLColumns** restituisce tutte le tabelle i cui nomi corrispondono a *TableName*. Per ODBC 3. *x* applicazioni **SQLColumns** restituisce tutte le tabelle i cui nomi corrispondono a *TableName* indipendentemente dal proprietario o se vengono utilizzati i caratteri jolly.  
  
 Nella tabella seguente vengono elencate le colonne restituite dal set di risultati:  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|DATA_TYPE|Restituisce SQL_VARCHAR, SQL_VARBINARY o SQL_WVARCHAR per i **varchar (max)** tipi di dati.|  
|TYPE_NAME|Restituisce "varchar", "varbinary" o "nvarchar" per il **varchar (max)**, **varbinary (max)**, e **nvarchar (max)** tipi di dati.|  
|COLUMN_SIZE|Restituisce SQL_SS_LENGTH_UNLIMITED per **varchar (max)** tipi di dati, che indica che le dimensioni della colonna sono illimitata.|  
|BUFFER_LENGTH|Restituisce SQL_SS_LENGTH_UNLIMITED per **varchar (max)** tipi di dati, che indica che la dimensione del buffer è illimitata.|  
|SQL_DATA_TYPE|Restituisce SQL_VARCHAR, SQL_VARBINARY o SQL_WVARCHAR per i **varchar (max)** tipi di dati.|  
|CHAR_OCTET_LENGTH|Restituisce la lunghezza massima di una colonna di tipo carattere o binario. Restituisce 0 per indicare che la dimensione è illimitata.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Restituisce il nome del catalogo nel quale è definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome del catalogo, questa variabile contiene una stringa vuota.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Restituisce il nome dello schema nel quale è definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome dello schema, questa variabile contiene una stringa vuota.|  
|SS_XML_SCHEMACOLLECTION_NAME|Restituisce il nome di una raccolta di XML Schema. Se non è possibile trovare il nome, questa variabile contiene una stringa vuota.|  
|SS_UDT_CATALOG_NAME|Nome del catalogo contenente il tipo definito dall'utente.|  
|SS_UDT_SCHEMA_NAME|Nome dello schema contenente il tipo definito dall'utente.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Nome completo dell'assembly del tipo definito dall'utente.|  
  
 Per tipi definiti dall'utente, la colonna TYPE_NAME esistente viene utilizzata per indicare il nome del tipo in questione; pertanto alcuna colonna aggiuntiva per tale non deve essere aggiunto al set di risultati di **SQLColumns** oppure [SQLProcedureColumns](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md). DATA_TYPE per un parametro o una colonna con tipo definito dall'utente è SQL_SS_UDT.  
  
 Per il tipo definito dall'utente dei parametri, è possibile utilizzare i nuovi descrittori specifici del driver definiti precedentemente per ottenere o impostare le proprietà di metadati aggiuntive di un tipo definito dall'utente, nel caso in cui il server restituisca o richieda queste informazioni.  
  
 Quando un client si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e chiama SQLColumns, utilizzando i valori NULL o con caratteri jolly per il parametro di input del catalogo non restituirà informazioni provenienti dagli altri cataloghi. Verranno invece restituite solo informazioni relative al catalogo corrente. Il client può chiamare innanzitutto SQLTables per determinare in quale catalogo si trova la tabella desiderata. Il client può quindi utilizzare tale valore di catalogo per il parametro di input del catalogo nella chiamata a SQLColumns per recuperare informazioni sulle colonne della tabella.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns e parametri con valori di tabella  
 Il set di risultati restituito da SQLColumns dipende dall'impostazione di SQL_SOPT_SS_NAME_SCOPE. Per altre informazioni, vedere [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Di seguito sono indicate le colonne che sono state aggiunte per i parametri con valori di tabella:  
  
|Nome colonna|Tipo di dati|Sommario|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Per una colonna in TABLE_TYPE, SQL_TRUE se la colonna è una colonna calcolata. In caso contrario, SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE se la colonna è una colonna Identity. In caso contrario, SQL_FALSE.|  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Supporto di SQLColumns per le caratteristiche avanzate di data e ora  
 Per informazioni sui valori restituiti per i tipi di data/ora, vedere [metadati del catalogo](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Per altre informazioni, vedere [data e ora miglioramenti &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Supporto di SQLColumns per tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLColumns** supporta grandi CLR tipi definiti dall'utente (UDT). Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Supporto di SQLColumns per colonne di tipo sparse  
 Due [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne specifiche sono stati aggiunti al set di risultati per SQLColumns:  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**smallint**|SQL_TRUE se una colonna è di tipo sparse. In caso contrario, SQL_FALSE.|  
|SS_IS_COLUMN_SET|**smallint**|Se la colonna è il **column_set** colonna, sql_true; in caso contrario, SQL_FALSE.|  
  
 In conformità con la specifica ODBC, SS_IS_SPARSE e SS_IS_COLUMN_SET vengono visualizzati prima di tutte le colonne specifiche del driver che sono state aggiunte per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versioni precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]e dopo tutte le colonne richieste da ODBC stesso.  
  
 Il set di risultati restituito da SQLColumns dipende dall'impostazione di SQL_SOPT_SS_NAME_SCOPE. Per altre informazioni, vedere [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Per ulteriori informazioni sulle colonne di tipo sparse in ODBC, vedere [supporto per colonne di tipo Sparse &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLColumns](http://go.microsoft.com/fwlink/?LinkId=59336)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
