---
title: bcp_gettypename | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_gettypename
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: de5b4a62dbb86008f686cb0d630386340238f42c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47743199"
---
# <a name="bcpgettypename"></a>bcp_gettypename
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Restituisce il nome del tipo SQL per il nome di un tipo di token specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_gettypename (  
        INT token,  
        DBBOOL fIsMaxType);  
```  
  
## <a name="arguments"></a>Argomenti  
 *token*  
 Valore che indica un token di tipo BCP.  
  
 *field*  
 Indica se il token richiesto è un tipo max.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Una stringa che contiene il nome del tipo SQL che corrisponde al tipo BCP. Se viene specificato un tipo BCP non valido, viene restituita una stringa vuota.  
  
## <a name="remarks"></a>Note  
 I token del tipo BCP vengono definiti nel file di intestazione sqlncli.h e nella libreria sqlncli11.lib.  
  
 Nella tabella seguente viene specificato quali sono i possibili tipi BCP, se si tratta di tipi max e l'output previsto.  
  
|Nome del tipo BCP|MaxType|Output|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|Prima o dopo|**decimal**|  
|**SQLNUMERIC**|Prima o dopo|**numeric**|  
|**SQLINT1**|Prima o dopo|**tinyint**|  
|**SQLINT2**|Prima o dopo|**smallint**|  
|**SQLINT4**|Prima o dopo|**int**|  
|**SQLMONEY**|Prima o dopo|**money**|  
|**SQLFLT8**|Prima o dopo|**float**|  
|**SQLDATETIME**|Prima o dopo|**datetime**|  
|**SQLBITN**|Prima o dopo|**bit-null**|  
|**SQLBIT**|Prima o dopo|**bit**|  
|**SQLBIGCHAR**|no|**char**|  
|**SQLCHARACTER**|no|**char**|  
|**SQLBIGVARCHAR**|no|**varchar**|  
|**SQLVARCHAR**|no|**varchar**|  
|**SQLTEXT**|Prima o dopo|**text**|  
|**SQLBIGBINARY**|no|**binary**|  
|**SQLBINARY**|no|**Binario**|  
|**SQLBIGVARBINARY**|no|**varbinary**|  
|**SQLVARBINARY**|no|**varbinary**|  
|**SQLIMAGE**|Prima o dopo|**Immagine**|  
|**SQLINTN**|Prima o dopo|**int-null**|  
|**SQLDATETIMN**|Prima o dopo|**datetime-null**|  
|**SQLMONEYN**|Prima o dopo|**money-null**|  
|**SQLFLTN**|Prima o dopo|**float-null**|  
|**SQLAOPSUM**|Prima o dopo|**Sum**|  
|**SQLAOPAVG**|Prima o dopo|**Avg**|  
|**SQLAOPCNT**|Prima o dopo|**Count**|  
|**SQLAOPMIN**|Prima o dopo|**Min**|  
|**SQLAOPMAX**|Prima o dopo|**Max**|  
|**SQLDATETIM4**|Prima o dopo|**smalldatetime**|  
|**SQLMONEY4**|Prima o dopo|**smallmoney**|  
|**SQLFLT4**|Prima o dopo|**Real**|  
|**SQLUNIQUEID**|Prima o dopo|**uniqueidentifier**|  
|**SQLNCHAR**|no|**nchar**|  
|**SQLNVARCHAR**|no|**Nvarchar**|  
|**SQLNTEXT**|Prima o dopo|**ntext**|  
|**SQLVARIANT**|Prima o dopo|**sql_variant**|  
|**SQLINT8**|Prima o dopo|**Bigint**|  
|**SQLCHARACTER**|Sì|**ntext**|  
|**SQLBIGCHAR**|Sì|**ntext**|  
|**SQLBIGVARCHAR**|Sì|**ntext**|  
|**SQLVARCHAR**|Sì|**ntext**|  
|**SQLBINARY**|Sì|**varbinary(max)**|  
|**SQLBIGBINARY**|Sì|**varbinary(max)**|  
|**SQLBIGVARBINARY**|Sì|**varbinary(max)**|  
|**SQLVARBINARY**|Sì|**varbinary(max)**|  
|**SQLNCHAR**|Sì|**nvarchar(max)**|  
|**SQLNVARCHAR**|Sì|**nvarchar(max)**|  
|**SQLXML**|Sì|**Xml**|  
|**SQLUDT**|Prima o dopo|**tipo definito dall'utente**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>Supporto di bcp_gettypename per le caratteristiche avanzate di data e ora  
 I valori di parametro del token per i tipi di data/ora sono descritti nella colonna della tabella in "Tipo in SQLNCLI. h" [modifiche apportate alla copia Bulk per avanzate di data e ora i tipi &#40;OLE DB e ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Il valore restituito si trova nella riga corrispondente della colonna "Tipo di archiviazione di file".  
  
 Per altre informazioni, vedere [data e miglioramenti per la fase &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di copia bulk](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
