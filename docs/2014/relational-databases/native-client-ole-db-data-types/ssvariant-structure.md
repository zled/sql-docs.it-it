---
title: Struttura SSVARIANT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0af799acbf0c498797564f2c057532a4964db0ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101321"
---
# <a name="ssvariant-structure"></a>Struttura SSVARIANT
  La struttura `SSVARIANT`, definita in sqlncli.h, corrisponde a un valore DBTYPE_SQLVARIANT nel provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 `SSVARIANT` è un'unione discriminante. A seconda del valore del membro vt, il consumer può determinare il membro da leggere. I valori vt corrispondono ai tipi di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pertanto, la struttura `SSVARIANT` può contenere qualsiasi tipo SQL Server. Per altre informazioni sulla struttura dei dati per i tipi OLE DB standard, vedere [indicatori di tipo](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Note  
 Quando DataTypeCompat==80, diversi sottotipi di `SSVARIANT` diventano stringhe. I valori vt seguenti vengono ad esempio visualizzati in `SSVARIANT` come VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Quando DateTypeCompat == 0, questi tipi vengono visualizzati nel formato nativo.  
  
 Per altre informazioni su SSPROP_INIT_DATATYPECOMPATIBILITY, vedere [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Il file sqlncli.h contiene macro di accesso di tipo Variant che semplificano la risoluzione dei riferimenti ai tipi di membri nella struttura `SSVARIANT`. Un esempio è rappresentato da V_SS_DATETIMEOFFSET, che è possibile utilizzare come indicato di seguito:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Per il set completo di macro di accesso per ogni membro della struttura `SSVARIANT`, fare riferimento al file sqlncli.hi.  
  
 Nella tabella seguente vengono descritti i membri della struttura `SSVARIANT`:  
  
|Membro|Indicatore del tipo OLE DB|Tipo di dati C di OLE DB|valore vt|Commenti|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Specifica il tipo di valore contenuto nella struttura `SSVARIANT`.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Supporta il `tinyint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Supporta il `smallint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Supporta il `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Supporta il `bigint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Supporta il `real` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Supporta il `float` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Supporta il `money` e **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Supporta il `bit` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Supporta il `uniqueidentifier` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Supporta il `numeric` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Supporta il `date` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Supporta il `smalldatetime`, `datetime`, e `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Supporta il `time` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tTime2Val* (`DBTIME2`)<br /><br /> *bScale* (`BYTE`) specifica il fattore di scala *tTime2Val* valore.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Supporta il `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (`BYTE`) specifica il fattore di scala *tsDataTimeVal* valore.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Supporta il `datetimeoffset` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *tsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)<br /><br /> *bScale* (`BYTE`) specifica il fattore di scala *tsoDateTimeOffsetVal* valore.|  
|NCharVal|Nessun indicatore del tipo OLE DB corrispondente.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Supporta il `nchar` e **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (`SHORT`) specifica la lunghezza effettiva per la stringa a cui *pwchNCharVal* punti. Non include lo zero finale.<br /><br /> *sMaxLength* (`SHORT`) specifica la lunghezza massima per la stringa a cui *pwchNCharVal* punti.<br /><br /> *pwchNCharVal* (`WCHAR` \*) puntatore alla stringa.<br /><br /> Membri non utilizzati: *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|CharVal|Nessun indicatore del tipo OLE DB corrispondente.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Supporta il `char` e **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (`SHORT`) specifica la lunghezza effettiva per la stringa da cui *pchCharVal* punti. Non include lo zero finale.<br /><br /> *sMaxLength* (`SHORT`) specifica la lunghezza massima per la stringa da cui *pchCharVal* punti.<br /><br /> *pchCharVal* (`CHAR` \*) puntatore alla stringa.<br /><br /> Membri non utilizzati:<br /><br /> *rgbReserved*, *dwReserved*, e *pwchReserved*.|  
|BinaryVal|Nessun indicatore del tipo OLE DB corrispondente.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Supporta il `binary` e **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i tipi di dati.<br /><br /> Include i membri indicati di seguito:<br /><br /> *sActualLength* (`SHORT`) specifica la lunghezza effettiva per i dati a cui *prgbBinaryVal* punti.<br /><br /> *sMaxLength* (`SHORT`) specifica la lunghezza massima per i dati a cui *prgbBinaryVal* punti.<br /><br /> *prgbBinaryVal* (`BYTE` \*) puntatore ai dati binari.<br /><br /> Membro non utilizzato: *dwReserved*.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
