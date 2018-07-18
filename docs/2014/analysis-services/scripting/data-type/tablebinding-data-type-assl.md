---
title: Tipo di dati TableBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TableBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableBinding
helpviewer_keywords:
- TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 475044a0bcad3c90ffaffa71eeeb6735a37f96c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220251"
---
# <a name="tablebinding-data-type-assl"></a>Tipo di dati TableBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione a una tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[TabularBinding](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Elemento DataSourceID](../properties/id-element-assl.md), [DbSchemaName](../properties/name-element-assl.md), [DbTableName](../properties/dbtablename-element-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 Se si fa riferimento ad altre tabelle nell'espressione di filtro tramite una selezione secondaria, è possibile che le prestazioni in alcune origini dati risultino ridotte. La finestra di progettazione può tuttavia controllare completamente l'espressione SQL tramite la definizione di una query denominata nella vista origine dati da utilizzare come riferimento.  
  
 Il metodo di definizione delle associazioni per una partizione è indipendente dall'utilizzo di tabelle partizionate nella vista origine dati.  
  
 Si consideri, ad esempio, un gruppo di misure la cui tabella predefinita "Sales" contiene le colonne Date, Product ID, Qty, Price e Amount calcolate nella vista origine dati. In questo caso, la partizione "Sales97" può utilizzare la tabella "Sales97" con il filtro "Year(Sales.Date) = 97".  
  
 La query effettiva sarà la seguente:  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 L'espressione calcolata si applica comunque, anche se l'espressione utilizza nomi di tabella qualificati, ad esempio Sales.Qty. Ciò vale anche se la tabella viene sostituita da una query "SELECT...". In questo caso, la clausola FROM indicata in precedenza diverrebbe "FROM SELECT... As Sales".  
  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) di tipo `Binding` e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati binding &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
