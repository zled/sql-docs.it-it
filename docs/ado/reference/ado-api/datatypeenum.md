---
title: DataTypeEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataTypeEnum
helpviewer_keywords:
- DataTypeEnum enumeration [ADO]
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 403797d082e3a3d9656c7f3992eb6db5c692307c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="datatypeenum"></a>DataTypeEnum
Specifica il tipo di dati di un [campo](../../../ado/reference/ado-api/field-object.md), [parametro](../../../ado/reference/ado-api/parameter-object.md), o [proprietà](../../../ado/reference/ado-api/property-object-ado.md). L'indicatore del tipo OLE DB corrispondente è racchiusa tra parentesi nella colonna Descrizione della tabella seguente.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**AdArray**|0x2000|Un valore del flag, sempre combinato con un'altra costante del tipo di dati, che indica una matrice del tipo di dati. Si applica ad ADOX.|  
|**adBigInt**|20|Indica un intero con segno a 8 byte (DBTYPE_I8).|  
|**adBinary**|128|Indica un valore binario (DBTYPE_BYTES).|  
|**adBoolean**|11|Indica un **booleano** valore (DBTYPE_BOOL).|  
|**adBSTR**|8|Indica una stringa di caratteri con terminazione null (Unicode) (DBTYPE_BSTR).|  
|**adChapter**|136|Indica un valore a quattro byte capitolo che identifica le righe in un set di righe figlio (DBTYPE_HCHAPTER).|  
|**adChar**|129|Indica un valore stringa (DBTYPE_STR).|  
|**adCurrency**|6|Indica un valore di valuta (DBTYPE_CY). Valuta è un numero a virgola fissa con quattro cifre a destra del separatore decimale. Vengono archiviati in un intero con segno a 8 byte ridimensionato di 10.000.|  
|**adDate**|7|Indica un valore di data (DBTYPE_DATE). Una data viene archiviata come valore double, la parte intera è il numero di giorni a partire dal 30 dicembre 1899, e la parte frazionaria è la frazione del giorno.|  
|**adDBDate**|133|Indica un valore di data (aaaammgg) (DBTYPE_DBDATE).|  
|**adDBTime**|134|Indica un valore di ora (hhmmss) (DBTYPE_DBTIME).|  
|**adDBTimeStamp**|135|Indica un indicatore di data/ora (aaaammgghhmmss più una frazione in miliardesimi) (DBTYPE_DBTIMESTAMP).|  
|**adDecimal**|14|Indica un valore numerico esatto con una precisione e scala fisse (DBTYPE_DECIMAL).|  
|**adDouble**|5|Indica un valore a virgola mobile a precisione doppia (DBTYPE_R8).|  
|**adEmpty**|0|Non specifica alcun valore (DBTYPE_EMPTY).|  
|**adError**|10|Indica un codice di errore a 32 bit (DBTYPE_ERROR).|  
|**adFileTime**|64|Indica un valore a 64 bit che rappresenta il numero di intervalli da 100 nanosecondi trascorsi dal 1 gennaio 1601 (DBTYPE_FILETIME).|  
|**adGUID**|72|Indica un identificatore univoco globale (GUID) (DBTYPE_GUID).|  
|**adIDispatch**|9|Indica un puntatore a un **IDispatch** interfaccia su un oggetto COM (DBTYPE_IDISPATCH).<br /><br /> **Nota** questo tipo di dati non è supportato da ADO. Utilizzo può provocare risultati imprevisti.|  
|**adInteger**|3|Indica un intero con segno a 4 byte (DBTYPE_I4).|  
|**adIUnknown**|13|Indica un puntatore a un **IUnknown** interfaccia su un oggetto COM (DBTYPE_IUNKNOWN).<br /><br /> **Nota** questo tipo di dati non è supportato da ADO. Utilizzo può provocare risultati imprevisti.|  
|**adLongVarBinary**|205|Indica un valore binario lungo.|  
|**adLongVarChar**|201|Indica un valore stringa lunga.|  
|**adLongVarWChar**|203|Indica un valore di stringa Unicode lungo a terminazione null.|  
|**adNumeric**|131|Indica un valore numerico esatto con una precisione e scala fisse (DBTYPE_NUMERIC).|  
|**adPropVariant**|138|Indica un'automazione PROPVARIANT (DBTYPE_PROP_VARIANT).|  
|**adSingle**|4|Indica un valore a virgola mobile e precisione singola (DBTYPE_R4).|  
|**adSmallInt**|2|Indica un intero con segno a due byte (DBTYPE_I2).|  
|**adTinyInt**|16|Indica un intero con segno a 1 byte (DBTYPE_I1).|  
|**adUnsignedBigInt**|21|Indica un intero senza segno a 8 byte (DBTYPE_UI8).|  
|**adUnsignedInt**|19|Indica un intero senza segno a 4 byte (DBTYPE_UI4).|  
|**adUnsignedSmallInt**|18|Indica un intero senza segno a due byte (DBTYPE_UI2).|  
|**adUnsignedTinyInt**|17|Indica un intero senza segno a 1 byte (DBTYPE_UI1).|  
|**adUserDefined**|132|Indica una variabile definita dall'utente (DBTYPE_UDT).|  
|**adVarBinary**|204|Indica un valore binario.|  
|**adVarChar**|200|Indica un valore stringa.|  
|**adVariant**|12|Indica un'automazione **Variant** (DBTYPE_VARIANT).<br /><br /> **Nota** questo tipo di dati non è supportato da ADO. Utilizzo può provocare risultati imprevisti.|  
|**adVarNumeric**|139|Indica un valore numerico.|  
|**adVarWChar**|202|Indica una stringa di caratteri Unicode con terminazione null.|  
|**adWChar**|130|Indica una terminazione null stringa di caratteri Unicode (DBTYPE_WSTR).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.DataType.ARRAY|  
|AdoEnums.DataType.BIGINT|  
|AdoEnums.DataType.BINARY|  
|AdoEnums.DataType.BOOLEAN|  
|AdoEnums.DataType.BSTR|  
|AdoEnums.DataType.CHAPTER|  
|AdoEnums.DataType.CHAR|  
|AdoEnums.DataType.CURRENCY|  
|AdoEnums.DataType.DATE|  
|AdoEnums.DataType.DBDATE|  
|AdoEnums.DataType.DBTIME|  
|AdoEnums.DataType.DBTIMESTAMP|  
|AdoEnums.DataType.DECIMAL|  
|AdoEnums.DataType.DOUBLE|  
|AdoEnums.DataType.EMPTY|  
|AdoEnums.DataType.ERROR|  
|AdoEnums.DataType.FILETIME|  
|AdoEnums.DataType.GUID|  
|AdoEnums.DataType.IDISPATCH|  
|AdoEnums.DataType.INTEGER|  
|AdoEnums.DataType.IUNKNOWN|  
|AdoEnums.DataType.LONGVARBINARY|  
|AdoEnums.DataType.LONGVARCHAR|  
|AdoEnums.DataType.LONGVARWCHAR|  
|AdoEnums.DataType.NUMERIC|  
|AdoEnums.DataType.PROPVARIANT|  
|AdoEnums.DataType.SINGLE|  
|AdoEnums.DataType.SMALLINT|  
|AdoEnums.DataType.TINYINT|  
|AdoEnums.DataType.UNSIGNEDBIGINT|  
|AdoEnums.DataType.UNSIGNEDINT|  
|AdoEnums.DataType.UNSIGNEDSMALLINT|  
|AdoEnums.DataType.UNSIGNEDTINYINT|  
|AdoEnums.DataType.USERDEFINED|  
|AdoEnums.DataType.VARBINARY|  
|AdoEnums.DataType.VARCHAR|  
|AdoEnums.DataType.VARIANT|  
|AdoEnums.DataType.VARNUMERIC|  
|AdoEnums.DataType.VARWCHAR|  
|AdoEnums.DataType.WCHAR|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Metodo CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|  
|[Metodo CreateRecordset (Servizi Desktop remoto)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|[Proprietà Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)|
