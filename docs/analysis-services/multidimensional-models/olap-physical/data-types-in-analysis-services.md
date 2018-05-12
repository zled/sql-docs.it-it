---
title: Tipi di dati in Analysis Services | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b7ac934afdc086a50020e9ba22ca2d236ee091b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="data-types-in-analysis-services"></a>Tipi di dati in Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Per tutti i <xref:Microsoft.AnalysisServices.DataItem> oggetti, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta il subset seguente di **System.Data.OleDb.OleDbType**. Per impostare o leggere il tipo di dati, utilizzare [tipo di dati DataItem &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
## <a name="supported-data-types"></a>Tipi di dati supportati  
  
|||  
|-|-|  
|BigInt|Intero con segno a 64 bit. Il *BigInt* tipo di valore rappresenta interi con valori compresi tra 9.223.372.036.854.775.808 negativo e 9.223.372.036.854.775.807 positivo.|  
|Binario|Un flusso di dati binari di **Byte** tipo. **Byte** è un tipo di valore che rappresenta interi senza segno con valori compresi tra 0 e 255.|  
|Boolean|Istanze di questo tipo dispongono di valori **true** o **false**.|  
|Currency|Oggetto *valuta* valore compreso tra -922.337.203.685.477,5808 e 922.337.203.685.477,5807 con un'accuratezza di un decimillesimo di unità di valuta (quattro cifre decimali).|  
|Data|Dati relativi alla data e all'ora, archiviati come valore Double. La parte intera indica il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno o dell'ora del giorno.|  
|Double|Numero a virgola mobile compreso tra -1,79769313486232E +308 e 1,79769313486232E +308. Un valore Double consente di archiviare informazioni sui numeri fino a 15 cifre decimali di precisione.|  
|Integer|Intero con segno a 32 bit che rappresenta interi con segno con valori compresi tra 2.147.483.648 (negativo) e 2.147.483.647 (positivo).|  
|Single|Numero a virgola mobile compreso tra - 3,4028235E +38 e 3,4028235E +38. Un valore Single consente di archiviare informazioni sui numeri fino a 7 cifre decimali di precisione.|  
|Smallint|Intero con segno a 16 bit. Il *Smallint* tipo di valore rappresenta interi con segno con valori compresi tra 32768 negativo e 32767 positivo.|  
|Tinyint|Numero intero con segno a 8 bit. Il tipo di valore Tinyint rappresenta interi con valori compresi tra 128 (negativo) e 127 (positivo).|  
|UnsignedBigInt|Intero senza segno a 64 bit. Il *UnsignedBigInt* tipo di valore rappresenta interi senza segno con valori compresi tra 0 a 18.446.744.073.709.551.615.|  
|UnsignedInt|Intero senza segno a 32 bit. Il *UnsignedInt* tipo di valore rappresenta interi senza segno con valori compresi tra 0 e 4.294.967.295.|  
|UnsignedSmallInt|Numero intero non firmato a 16 bit. Il *UnsignedSmallInt* tipo di valore rappresenta interi senza segno con valori compresi tra 0 e 65535.|  
|UnsignedTinyInt|Intero senza segno a 8 bit. Il *e UnsignedTinyInt* tipo di valore rappresenta interi senza segno con valori compresi tra 0 e 255.|  
|WChar|Flusso con terminazione Null di caratteri Unicode. Oggetto *WChar* è una raccolta sequenza di caratteri Unicode che viene utilizzata per rappresentare del testo.|  
  
## <a name="amo-validations-on-data-types"></a>Convalide AMO nei tipi di dati  
 Nella tabella seguente vengono elencate le convalide aggiuntive eseguite nella libreria AMO (Analysis Management Objects) per determinate associazioni.  
  
|Oggetto|Associazione|Tipi di dati consentiti|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Tutti tranne i dati binari|  
||NameColumn|Solo WChar|  
||SkippedLevelsColumns|Solo tipi integer: BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt e UnsignedTinyInt|  
||CustomRollupColumn|Solo WChar|  
||CustomRollupPropertiesColumn|Solo WChar|  
||UnaryOperatorColumn|Solo WChar|  
||ValueColumn|Tutto|  
|AttributeTranslation|CaptionColumn|Solo WChar|  
|ScalarMiningStructureColumn|KeyColumns|Tutti tranne i dati binari|  
||NameColumn|Solo WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|Tutti tranne i dati binari|  
|MeasureGroupAttribute|KeyColumns|Tutti tranne i dati binari|  
|Misura Distinct Count|Origine|BigInt, Currency, Double, Integer, Single, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt e UnsignedTinyInt|  
  
  
