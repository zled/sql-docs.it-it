---
title: Struttura SSVARIANT | Documenti Microsoft
description: Struttura SSVARIANT nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 797c10dfeabd1361395c5416f65c88a0d6c82176
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="ssvariant-structure"></a>Struttura SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il **SSVARIANT** struttura, di cui è definito in msoledbsql.h, corrisponde a un valore DBTYPE_SQLVARIANT nel Driver OLE DB per SQL Server.  
  
 **SSVARIANT** è un'unione discriminante. A seconda del valore del membro vt, il consumer può determinare il membro da leggere. i valori VT corrispondono alla [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati. Pertanto, il **SSVARIANT** struttura può contenere qualsiasi tipo di SQL Server. Per ulteriori informazioni sulla struttura dei dati per i tipi OLE DB standard, vedere [indicatori di tipo](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Osservazioni  
 Quando DataTypeCompat = = 80, diversi **SSVARIANT** sottotipi diventano stringhe. Ad esempio, i valori vt seguenti verranno visualizzato **SSVARIANT** come VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Quando DateTypeCompat == 0, questi tipi vengono visualizzati nel formato nativo.  
  
 Per ulteriori informazioni su SSPROP_INIT_DATATYPECOMPATIBILITY, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Il file msoledbsql.h contiene macro di accesso di tipo variant che semplificano la dereferenziazione i tipi di membri nel **SSVARIANT** struttura. Un esempio è rappresentato da V_SS_DATETIMEOFFSET, che è possibile utilizzare come indicato di seguito:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Per il set completo di macro di accesso per ogni membro della **SSVARIANT** struttura, vedere il file msoledbsql.h.  
  
 Nella tabella seguente vengono descritti i membri del **SSVARIANT** struttura:  
  
|Membro|Indicatore del tipo OLE DB|Tipo di dati C di OLE DB|valore vt|Commenti|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Specifica il tipo di valore contenuto nel **SSVARIANT** struct.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Supporta il **tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|sShortIntVal|DBTYPE_I2|**BREVE**|**VT_SS_I2**|Supporta il **smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Supporta il **int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Supporta il **bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Supporta il **reale** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Supporta il **float** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Supporta il **money** e **smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Supporta il **bit** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Supporta il **uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Supporta il **numerico** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Supporta il **data** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Supporta il **smalldatetime**, **datetime**, e **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Supporta il **ora** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) specifica la scala per *tTime2Val* valore.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Supporta il **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) specifica la scala per *tsDataTimeVal* valore.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Supporta il **datetimeoffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) specifica la scala per *tsoDateTimeOffsetVal* valore.|  
|NCharVal|Nessun indicatore del tipo OLE DB corrispondente.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Supporta il **nchar** e **nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (**breve**) specifica la lunghezza effettiva per la stringa a cui *pwchNCharVal* punti. Non include lo zero finale.<br /><br /> *sMaxLength* (**breve**) specifica la lunghezza massima per la stringa a cui *pwchNCharVal* punti.<br /><br /> *pwchNCharVal* (**WCHAR** \*) puntatore alla stringa.<br /><br /> Membri non utilizzati: *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|CharVal|Nessun indicatore del tipo OLE DB corrispondente.|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Supporta il **char** e **varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (**breve**) specifica la lunghezza effettiva per la stringa a cui *pchCharVal* punti. Non include lo zero finale.<br /><br /> *sMaxLength* (**breve**) specifica la lunghezza massima per la stringa a cui *pchCharVal* punti.<br /><br /> *pchCharVal* (**CHAR** \*) puntatore alla stringa.<br /><br /> Membri non utilizzati:<br /><br /> *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|BinaryVal|Nessun indicatore del tipo OLE DB corrispondente.|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Supporta il **binario** e **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (**breve**) specifica la lunghezza effettiva per i dati a cui *prgbBinaryVal* punti.<br /><br /> *sMaxLength* (**breve**) specifica la lunghezza massima per i dati a cui *prgbBinaryVal* punti.<br /><br /> *prgbBinaryVal* (**BYTE** \*) puntatore ai dati binari.<br /><br /> Membro non utilizzato: *dwReserved*.|  
|Tipo sconosciuto|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40; OLE DB &#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
