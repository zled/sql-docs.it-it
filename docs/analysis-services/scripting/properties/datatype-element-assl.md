---
title: Elemento DataType (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataType Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DataType
helpviewer_keywords: DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5493199c219747a1b7d5eb843c73103d51039957
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="datatype-element-assl"></a>Elemento DataType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce il tipo di dati dell'elemento associato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md), [misura](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 I valori per **DataType** sono definite nel **System.Data.OleDb.OleDbType** enumerazione. Tuttavia, solo i valori di enumerazione nella tabella seguente sono validi nel **DataType** elemento.  
  
|Valore|Description|  
|-----------|-----------------|  
|*BigInt*|Intero con segno a 64 bit. Esegue il mapping di questo tipo di dati per il **Int64** del tipo di dati [!INCLUDE[msCoName](../../../includes/msconame-md.md)] tipo di .NET Framework e i dati di DBTYPE_I8 in OLE DB.|  
|*Bool*|Valore booleano. Esegue il mapping di questo tipo di dati per il **booleano** tipo di dati .NET Framework e il tipo di dati DBTYPE_BOOL in OLE DB.|  
|*Valuta*|Un valore di valuta compreso tra -2<sup>63</sup> (o -922.337.203.685.477,5808) a 2<sup>63</sup>-1 (o + 922.337.203.685.477,5807) con un'accuratezza di un decimillesimo di unità di valuta. Esegue il mapping di questo tipo di dati per il **decimale** tipo di dati .NET Framework e il tipo di dati DBTYPE_CY in OLE DB.|  
|*Data*|Tipo di dati data, registrato come numero a virgola mobile e doppia precisione. La parte intera è il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno. Esegue il mapping di questo tipo di dati per il **DateTime** tipo di dati .NET Framework e il tipo di dati DBTYPE_DATE in OLE DB.|  
|*Doppia*|Numero a doppia precisione e virgola mobile compreso tra -1,79E +308 e 1,79E +308. Esegue il mapping di questo tipo di dati per il **doppie** tipo di dati .NET Framework e il tipo di dati DBTYPE_R8 in OLE DB.|  
|*Integer*|Intero con segno a 32 bit. Esegue il mapping di questo tipo di dati per il **Int32** tipo di dati .NET Framework e il tipo di dati DBTYPE_I4 in OLE DB.|  
|*Singolo*|Numero a precisione singola e virgola mobile compreso tra -3,40E +38 e 3,40E +38. Esegue il mapping di questo tipo di dati per il **singolo** il tipo di dati in .NET Framework e il tipo di dati DBTYPE_R4 in OLE DB.|  
|*SmallInt*|Intero con segno a 16 bit. Esegue il mapping di questo tipo di dati per il **Int16** tipo di dati .NET Framework e il tipo di dati DBTYPE_I2 in OLE DB.|  
|*TinyInt*|Numero intero con segno a 8 bit. Esegue il mapping di questo tipo di dati per il **SByte** tipo di dati .NET Framework e il tipo di dati DBTYPE_I1 in OLE DB.|  
|*UnsignedBigInt*|Intero senza segno a 64 bit. Esegue il mapping di questo tipo di dati per il **UInt64** il tipo di dati in .NET Framework e il tipo di dati DBTYPE_UI8 in OLE DB.|  
|*UnsignedInt*|Intero senza segno a 32 bit. Esegue il mapping di questo tipo di dati per il **UInt32** tipo di dati .NET Framework e il tipo di dati DBTYPE_UI4 in OLE DB.|  
|*UnsignedSmallInt*|Numero intero non firmato a 16 bit. Esegue il mapping di questo tipo di dati per il **UInt16** tipo di dati .NET Framework e il tipo di dati DBTYPE_UI2 in OLE DB.|  
|*WChar*|Flusso con terminazione Null di caratteri Unicode. Esegue il mapping di questo tipo di dati per il **stringa** tipo di dati .NET Framework e il tipo di dati DBTYPE_WSTR in OLE DB.|  
|*Ereditata*|Il tipo di dati di **DataItem** contenuti nel [origine](../../../analysis-services/scripting/properties/source-element-measure-assl.md) elemento del **misura** elemento.<br /><br /> Nota: Applicabile solo a **misura** elementi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
