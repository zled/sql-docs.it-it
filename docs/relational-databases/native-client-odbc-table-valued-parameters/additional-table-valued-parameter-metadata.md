---
title: I metadati di parametro con valori di tabella aggiuntivo | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 14a20ad29eb227da04544e3d0695e4536702f8f7
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="additional-table-valued-parameter-metadata"></a>Metadati aggiuntivi dei parametri con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Per recuperare metadati per un parametro con valori di tabella, un'applicazione chiama SQLProcedureColumns. Per un parametro con valori di tabella, SQLProcedureColumns restituisce una singola riga. Altri due [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-colonne specifiche, SS_TYPE_CATALOG_NAME e SS_TYPE_SCHEMA_NAME, sono stati aggiunti per fornire informazioni di catalogo e lo schema per tipi di tabella associati ai parametri con valori di tabella. In conformità con la specifica ODBC, SS_TYPE_CATALOG_NAME e SS_TYPE_SCHEMA_NAME vengono visualizzati prima di tutte le colonne specifiche del driver che sono state aggiunte nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dopo tutte le colonne richieste da ODBC stesso.  
  
 Nella tabella seguente sono elencate le colonne significative per i parametri con valori di tabella.  
  
|Nome colonna|Tipo di dati|Valore/commenti|  
|-----------------|---------------|---------------------|  
|DATA_TYPE|Smallint non NULL|SQL_SS_TABLE|  
|TYPE_NAME|WVarchar(128) non NULL|Nome del tipo del parametro con valori di tabella.|  
|COLUMN_SIZE|Integer|NULL|  
|BUFFER_LENGTH|Integer|0|  
|DECIMAL_DIGITS|Smallint|NULL|  
|NUM_PREC_RADIX|Smallint|NULL|  
|NULLABLE|Smallint non NULL|SQL_NULLABLE|  
|REMARKS|Varchar|NULL|  
|COLUMN_DEF|WVarchar(4000)|NULL|  
|SQL_DATA_TYPE|Smallint non NULL|SQL_SS_TABLE|  
|SQL_DATETIME_SUB|Smallint|NULL|  
|CHAR_OCTET_LENGTH|Integer|NULL|  
|ORDINAL_POSITION|Integer non NULL|Posizione ordinale del parametro.|  
|IS_NULLABLE|Varchar|"YES"|  
|SS_TYPE_CATALOG_NAME|WVarchar(128) non NULL|Catalogo contenente la definizione di tipo per il tipo di tabella del parametro con valori di tabella.|  
|SS_TYPE_SCHEMA_NAME|WVarchar(128) non NULL|Schema contenente la definizione di tipo per il tipo di tabella del parametro con valori di tabella.|  
  
 Le colonne WVarchar sono definite come Varchar nella specifica di ODBC ma, di fatto, vengono restituite come WVarchar in tutti i driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recenti. Questa modifica è stata apportata quando il supporto Unicode è stato aggiunto alla specifica di ODBC 3.5 ma non è stato esplicitamente menzionato.  
  
 Per ottenere metadati aggiuntivi per i parametri con valori di tabella, un'applicazione utilizza le funzioni di catalogo SQLColumns e SQLPrimaryKeys. Prima che queste funzioni vengano chiamate per i parametri con valori di tabella, è necessario che l'attributo dell'istruzione SQL_SOPT_SS_NAME_SCOPE venga impostato su SQL_SS_NAME_SCOPE_TABLE_TYPE. Questo valore indica che l'applicazione richiede metadati per un tipo di tabella piuttosto che una tabella effettiva. L'applicazione passa quindi TYPE_NAME del parametro con valori di tabella, come il *TableName* parametro. SS_TYPE_CATALOG_NAME e SS_TYPE_SCHEMA_NAME vengono utilizzati con il *CatalogName* e *SchemaName* parametri, rispettivamente, per identificare il catalogo e schema per il parametro con valori di tabella. Quando un'applicazione ha completato il recupero dei metadati per i parametri con valori di tabella, deve impostare nuovamente SQL_SOPT_SS_NAME_SCOPE sul valore predefinito di SQL_SS_NAME_SCOPE_TABLE.  
  
 Quando SQL_SOPT_SS_NAME_SCOPE è impostato su SQL_SS_NAME_SCOPE_TABLE, le query ai server collegati non riescono. Le chiamate a SQLColumns o SQLPrimaryKeys con un catalogo che contiene un componente server avrà esito negativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued parametri &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
