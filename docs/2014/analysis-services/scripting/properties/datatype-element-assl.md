---
title: Elemento DataType (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92c3981344d0425c46ef283fa8792de942d6193b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191041"
---
# <a name="datatype-element-assl"></a>Elemento DataType (ASSL)
  Definisce il tipo di dati dell'elemento associato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../data-type/dataitem-data-type-assl.md), [misura](../objects/measure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 I valori per `DataType` sono definiti nell'enumerazione `System.Data.OleDb.OleDbType`. Tuttavia, solo i valori di enumerazione nella tabella seguente sono validi nell'elemento `DataType`.  
  
|valore|Description|  
|-----------|-----------------|  
|*BigInt*|Intero con segno a 64 bit. Esegue il mapping di questo tipo di dati per il `Int64` tipo di dati [!INCLUDE[msCoName](../../../includes/msconame-md.md)] tipo .NET Framework e i dati di DBTYPE_I8 in OLE DB.|  
|*bool*|Valore booleano. Questo tipo di dati esegue il mapping al tipo di dati `Boolean` in .NET Framework e il tipo di dati di DBTYPE_BOOL in OLE DB.|  
|*Valuta*|Valore di valuta compreso tra -2<sup>63</sup> (o -922.337.203.685.477,5808) a 2<sup>63</sup>-1 (o + 922.337.203.685.477,5807) con un'approssimazione pari a dieci millesimi di unità di valuta. Questo tipo di dati esegue il mapping al tipo di dati `Decimal` in .NET Framework e il tipo di dati di DBTYPE_CY in OLE DB.|  
|*Data*|Tipo di dati data, registrato come numero a virgola mobile e doppia precisione. La parte intera è il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno. Questo tipo di dati esegue il mapping al tipo di dati `DateTime` in .NET Framework e il tipo di dati di DBTYPE_DATE in OLE DB.|  
|*Valore Double*|Numero a doppia precisione e virgola mobile compreso tra -1,79E +308 e 1,79E +308. Questo tipo di dati esegue il mapping al tipo di dati `Double` in .NET Framework e il tipo di dati di DBTYPE_R8 in OLE DB.|  
|*Integer*|Intero con segno a 32 bit. Questo tipo di dati esegue il mapping al tipo di dati `Int32` in .NET Framework e il tipo di dati di DBTYPE_I4 in OLE DB.|  
|*Singolo*|Numero a precisione singola e virgola mobile compreso tra -3,40E +38 e 3,40E +38. Questo tipo di dati esegue il mapping al tipo di dati `Single` in .NET Framework e il tipo di dati di DBTYPE_R4 in OLE DB.|  
|*SmallInt*|Intero con segno a 16 bit. Questo tipo di dati esegue il mapping al tipo di dati `Int16` in .NET Framework e il tipo di dati di DBTYPE_I2 in OLE DB.|  
|*TinyInt*|Numero intero con segno a 8 bit. Questo tipo di dati esegue il mapping al tipo di dati `SByte` in .NET Framework e il tipo di dati di DBTYPE_I1 in OLE DB.|  
|*UnsignedBigInt*|Intero senza segno a 64 bit. Questo tipo di dati esegue il mapping al tipo di dati `UInt64` in .NET Framework e il tipo di dati di DBTYPE_UI8 in OLE DB.|  
|*UnsignedInt*|Intero senza segno a 32 bit. Questo tipo di dati esegue il mapping al tipo di dati `UInt32` in .NET Framework e il tipo di dati di DBTYPE_UI4 in OLE DB.|  
|*UnsignedSmallInt*|Numero intero non firmato a 16 bit. Questo tipo di dati esegue il mapping al tipo di dati `UInt16` in .NET Framework e il tipo di dati di DBTYPE_UI2 in OLE DB.|  
|*WChar*|Flusso con terminazione Null di caratteri Unicode. Questo tipo di dati esegue il mapping al tipo di dati `String` in .NET Framework e il tipo di dati di DBTYPE_WSTR in OLE DB.|  
|*Ereditata*|Il tipo di dati di `DataItem` contenuti nel [origine](source-element-measure-assl.md) elemento del `Measure` elemento. **Nota:** applicabile solo a `Measure` elementi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
