---
title: Supporto sql_variant per i tipi Date e Time | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0cbde879e2b7f215c5044936dfbdacab9196f02d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150823"
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>Supporto sql_variant per i tipi di data e ora
  In questo argomento viene illustrato come il tipo di dati `sql_variant` supporta la funzionalità avanzata di data e ora.  
  
 L'attributo della colonna SQL_CA_SS_VARIANT_TYPE è utilizzato per restituire il tipo C di una colonna dei risultati variant. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduce un attributo aggiuntivo, SQL_CA_SS_VARIANT_SQL_TYPE, che imposta il tipo SQL di una colonna di risultati variant nel descrittore della riga di implementazione (IRD). SQL_CA_SS_VARIANT_SQL_TYPE è anche utilizzabile nel descrittore di parametri di implementazione (IPD) per specificare il tipo SQL di un SQL_SS_TIME2 o SQL_SS_TIMESTAMPOFFSET parametro che ha un tipo SQL_C_BINARY C associato al tipo SQL_SS_VARIANT.  
  
 I nuovi tipi SQL_SS_TIME2 e SQL_SS_TIMESTAMPOFFSET possono essere impostati da SQLColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE può essere restituito da SQLGetDescField.  
  
 Per le colonne dei risultati, il driver convertirà i tipi da variant a date/time. Per altre informazioni, vedere [le conversioni da SQL a C](datetime-data-type-conversions-from-sql-to-c.md). In caso di associazione a SQL_C_BINARY, la lunghezza dei buffer deve essere sufficiente a consentire la ricezione della struttura che corrisponde al tipo SQL.  
  
 Per i parametri SQL_SS_TIME2 e SQL_SS_TIMESTAMPOFFSET, il driver convertirà i valori C in valori `sql_variant`, come descritto nella tabella seguente. Se un parametro viene associato come SQL_C_BINARY e il tipo di server è SQL_SS_VARIANT, verrà trattato come valore binario, a meno che l'applicazione non abbia impostato SQL_CA_SS_VARIANT_SQL_TYPE su un tipo SQL diverso. In questo caso SQL_CA_SS_VARIANT_SQL_TYPE ha la precedenza, ovvero se è impostato SQL_CA_SS_VARIANT_SQL_TYPE, viene ignorato il comportamento predefinito che consiste nel dedurre il tipo SQL variant dal tipo C.  
  
|Tipo C|Tipo server|Commenti|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_USHORT|INT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_LONG|INT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_SLONG|INT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_FLOAT|REAL|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_DOUBLE|FLOAT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE non è impostato.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> La scala è impostata su SQL_DESC_PRECISION (il *DecimalDigits* parametro di `SQLBindParameter`).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> La scala è impostata su SQL_DESC_PRECISION (il *DecimalDigits* parametro di `SQLBindParameter`).|  
|SQL_C_TYPE_DATE|Data|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|La scala è impostata su SQL_DESC_PRECISION (il *DecimalDigits* parametro di `SQLBindParameter`).|  
|SQL_C_NUMERIC|Decimal|La precisione è impostata su SQL_DESC_PRECISION (il *ColumnSize* parametro di `SQLBindParameter`).<br /><br /> Scala impostata su SQL_DESC_SCALE (il *DecimalDigits* parametro di SQLBindParameter).|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE viene ignorato|  
  
## <a name="see-also"></a>Vedere anche  
 [Data e miglioramenti per la fase &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  
